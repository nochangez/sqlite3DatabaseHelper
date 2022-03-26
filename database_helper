# coding=utf-8


import sqlite3


class DatabaseHelper:
    """
    this class helps in using database methods, database
    initialize, send queries and get data from it
    """

    def __init__(self, db_path: str):
        """
        database init (connection and creating database cursor)
        :param db_path: absolute database's path
        """

        # trying to connect to the database
        try:
            self.db_connection = sqlite3.connect(db_path)  # creating db and connecting to it
            self.db_cursor = self.db_connection.cursor()  # cursor for control db queries

            print(f"[db] database has been created/opened successfully!")
        except sqlite3.Error as db_error:
            print(f"[db] an error has occurred: {db_error}")
        finally:
            if self.db_connection:
                self.db_connection.close()  # close db connection if error occurred

    def execute_query(self, db_query: str, get_data: bool = False):
        """
        :param db_query: your database query
        :param get_data: if query returns data - set True value, default: False
        :return: returns received data from database
        """

        self.db_cursor.execute(db_query)  # execute requested query in database
        self.db_connection.commit()  # save all changes

        if get_data:
            received_data = self.db_cursor.fetchall()  # received data from db query

            return received_data
        else:
            print("[db] query executed successfully!")
