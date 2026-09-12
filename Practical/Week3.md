Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 93
Server version: 8.0.46 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE DATABASE sqlpractice;
Query OK, 1 row affected (0.06 sec)

mysql> USE sqlpractice;
Database changed
mysql> CREATE TABLE orders (
    ->     ord_no INT PRIMARY KEY,
    ->     purch_amt DECIMAL(10,2),
    ->     ord_date DATE,
    ->     customer_id INT,
    ->     salesman_id INT
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> SELECT * FROM orders;
Empty set (0.01 sec)

mysql> INSERT INTO orders VALUES
    -> (70001,150.50,'2012-10-05',3005,5002),
    -> (70002,65.26,'2012-10-05',3002,5001),
    -> (70003,2480.40,'2012-10-10',3009,5003),
    -> (70004,110.50,'2012-08-17',3009,5003),
    -> (70005,2400.60,'2012-07-27',3007,5001),
    -> (70007,948.50,'2012-09-10',3005,5002),
    -> (70008,5760.00,'2012-09-10',3002,5001),
    -> (70009,270.65,'2012-09-10',3001,5005),
    -> (70010,1983.43,'2012-10-10',3004,5006),
    -> (70011,75.29,'2012-08-17',3003,5007),
    -> (70012,250.45,'2012-06-27',3008,5002),
    -> (70013,3045.60,'2012-04-25',3002,5001);
Query OK, 12 rows affected (0.02 sec)
Records: 12  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM orders;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70001 |    150.50 | 2012-10-05 |        3005 |        5002 |
|  70002 |     65.26 | 2012-10-05 |        3002 |        5001 |
|  70003 |   2480.40 | 2012-10-10 |        3009 |        5003 |
|  70004 |    110.50 | 2012-08-17 |        3009 |        5003 |
|  70005 |   2400.60 | 2012-07-27 |        3007 |        5001 |
|  70007 |    948.50 | 2012-09-10 |        3005 |        5002 |
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70009 |    270.65 | 2012-09-10 |        3001 |        5005 |
|  70010 |   1983.43 | 2012-10-10 |        3004 |        5006 |
|  70011 |     75.29 | 2012-08-17 |        3003 |        5007 |
|  70012 |    250.45 | 2012-06-27 |        3008 |        5002 |
|  70013 |   3045.60 | 2012-04-25 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
12 rows in set (0.00 sec)

mysql> SELECT *
    -> FROM orders
    -> WHERE purch_amt > 2000;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70003 |   2480.40 | 2012-10-10 |        3009 |        5003 |
|  70005 |   2400.60 | 2012-07-27 |        3007 |        5001 |
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70013 |   3045.60 | 2012-04-25 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
4 rows in set (0.01 sec)

mysql> SELECT *
    -> FROM orders
    -> WHERE ord_date = '2012-09-10';
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70007 |    948.50 | 2012-09-10 |        3005 |        5002 |
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70009 |    270.65 | 2012-09-10 |        3001 |        5005 |
+--------+-----------+------------+-------------+-------------+
3 rows in set (0.01 sec)

mysql> SELECT *
    -> FROM orders
    -> WHERE salesman_id = 5001;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70002 |     65.26 | 2012-10-05 |        3002 |        5001 |
|  70005 |   2400.60 | 2012-07-27 |        3007 |        5001 |
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70013 |   3045.60 | 2012-04-25 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
4 rows in set (0.00 sec)

mysql> SELECT *
    -> FROM orders
    -> ORDER BY purch_amt DESC;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70013 |   3045.60 | 2012-04-25 |        3002 |        5001 |
|  70003 |   2480.40 | 2012-10-10 |        3009 |        5003 |
|  70005 |   2400.60 | 2012-07-27 |        3007 |        5001 |
|  70010 |   1983.43 | 2012-10-10 |        3004 |        5006 |
|  70007 |    948.50 | 2012-09-10 |        3005 |        5002 |
|  70009 |    270.65 | 2012-09-10 |        3001 |        5005 |
|  70012 |    250.45 | 2012-06-27 |        3008 |        5002 |
|  70001 |    150.50 | 2012-10-05 |        3005 |        5002 |
|  70004 |    110.50 | 2012-08-17 |        3009 |        5003 |
|  70011 |     75.29 | 2012-08-17 |        3003 |        5007 |
|  70002 |     65.26 | 2012-10-05 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
12 rows in set (0.00 sec)

mysql> SELECT *
    -> FROM orders
    -> ORDER BY ord_date;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70013 |   3045.60 | 2012-04-25 |        3002 |        5001 |
|  70012 |    250.45 | 2012-06-27 |        3008 |        5002 |
|  70005 |   2400.60 | 2012-07-27 |        3007 |        5001 |
|  70004 |    110.50 | 2012-08-17 |        3009 |        5003 |
|  70011 |     75.29 | 2012-08-17 |        3003 |        5007 |
|  70007 |    948.50 | 2012-09-10 |        3005 |        5002 |
|  70008 |   5760.00 | 2012-09-10 |        3002 |        5001 |
|  70009 |    270.65 | 2012-09-10 |        3001 |        5005 |
|  70001 |    150.50 | 2012-10-05 |        3005 |        5002 |
|  70002 |     65.26 | 2012-10-05 |        3002 |        5001 |
|  70003 |   2480.40 | 2012-10-10 |        3009 |        5003 |
|  70010 |   1983.43 | 2012-10-10 |        3004 |        5006 |
+--------+-----------+------------+-------------+-------------+
12 rows in set (0.00 sec)

mysql> SELECT SUM(purch_amt) AS total_amount
    -> FROM orders;
+--------------+
| total_amount |
+--------------+
|     17541.18 |
+--------------+
1 row in set (0.01 sec)

mysql> SELECT AVG(purch_amt) AS average_amount
    -> FROM orders;
+----------------+
| average_amount |
+----------------+
|    1461.765000 |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT MAX(purch_amt) AS maximum_amount
    -> FROM orders;
+----------------+
| maximum_amount |
+----------------+
|        5760.00 |
+----------------+
1 row in set (0.01 sec)

mysql> SELECT MIN(purch_amt) AS minimum_amount
    -> FROM orders;
+----------------+
| minimum_amount |
+----------------+
|          65.26 |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT COUNT(*) AS total_orders
    -> FROM orders;
+--------------+
| total_orders |
+--------------+
|           12 |
+--------------+
1 row in set (0.02 sec)

mysql> SELECT salesman_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> GROUP BY salesman_id;
+-------------+--------------+
| salesman_id | total_amount |
+-------------+--------------+
|        5002 |      1349.45 |
|        5001 |     11271.46 |
|        5003 |      2590.90 |
|        5005 |       270.65 |
|        5006 |      1983.43 |
|        5007 |        75.29 |
+-------------+--------------+
6 rows in set (0.01 sec)

mysql> SELECT customer_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> GROUP BY customer_id;
+-------------+--------------+
| customer_id | total_amount |
+-------------+--------------+
|        3005 |      1099.00 |
|        3002 |      8870.86 |
|        3009 |      2590.90 |
|        3007 |      2400.60 |
|        3001 |       270.65 |
|        3004 |      1983.43 |
|        3003 |        75.29 |
|        3008 |       250.45 |
+-------------+--------------+
8 rows in set (0.00 sec)

mysql> SELECT customer_id, MAX(purch_amt) AS maximum_amount
    -> FROM orders
    -> GROUP BY customer_id;
+-------------+----------------+
| customer_id | maximum_amount |
+-------------+----------------+
|        3005 |         948.50 |
|        3002 |        5760.00 |
|        3009 |        2480.40 |
|        3007 |        2400.60 |
|        3001 |         270.65 |
|        3004 |        1983.43 |
|        3003 |          75.29 |
|        3008 |         250.45 |
+-------------+----------------+
8 rows in set (0.00 sec)

mysql> SELECT salesman_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> GROUP BY salesman_id
    -> HAVING SUM(purch_amt) > 3000;
+-------------+--------------+
| salesman_id | total_amount |
+-------------+--------------+
|        5001 |     11271.46 |
+-------------+--------------+
1 row in set (0.00 sec)

mysql> SELECT customer_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> GROUP BY customer_id
    -> HAVING SUM(purch_amt) > 3000;
+-------------+--------------+
| customer_id | total_amount |
+-------------+--------------+
|        3002 |      8870.86 |
+-------------+--------------+
1 row in set (0.00 sec)

mysql> SELECT salesman_id, COUNT(*) AS total_orders
    -> FROM orders
    -> GROUP BY salesman_id
    -> HAVING COUNT(*) > 1;
+-------------+--------------+
| salesman_id | total_orders |
+-------------+--------------+
|        5002 |            3 |
|        5001 |            4 |
|        5003 |            2 |
+-------------+--------------+
3 rows in set (0.00 sec)

mysql> SELECT salesman_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> GROUP BY salesman_id
    -> HAVING SUM(purch_amt) > 3000
    -> ORDER BY total_amount DESC;
+-------------+--------------+
| salesman_id | total_amount |
+-------------+--------------+
|        5001 |     11271.46 |
+-------------+--------------+
1 row in set (0.00 sec)

mysql> SELECT salesman_id, SUM(purch_amt) AS total_amount
    -> FROM orders
    -> WHERE purch_amt BETWEEN 500 AND 3000
    -> GROUP BY salesman_id
    -> HAVING SUM(purch_amt) > 3000;
Empty set (0.00 sec)

mysql> SELECT customer_id, COUNT(*) AS total_orders
    -> FROM orders
    -> GROUP BY customer_id
    -> HAVING COUNT(*) > 1;
+-------------+--------------+
| customer_id | total_orders |
+-------------+--------------+
|        3005 |            2 |
|        3002 |            3 |
|        3009 |            2 |
+-------------+--------------+
3 rows in set (0.00 sec)

mysql> SELECT salesman_id, MAX(purch_amt) AS maximum_amount
    -> FROM orders
    -> GROUP BY salesman_id
    -> HAVING MAX(purch_amt) > 2000;
+-------------+----------------+
| salesman_id | maximum_amount |
+-------------+----------------+
|        5001 |        5760.00 |
|        5003 |        2480.40 |
+-------------+----------------+
2 rows in set (0.00 sec)

mysql>
