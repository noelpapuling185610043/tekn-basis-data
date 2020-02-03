# tekn-basis-data
Enter password: ****
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.5.0-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| bioskop            |
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
5 rows in set (0.001 sec)

MariaDB [(none)]> use bioskop;
Database changed
MariaDB [bioskop]> show tables;
+-------------------+
| Tables_in_bioskop |
+-------------------+
| film              |
| pemesan           |
+-------------------+
2 rows in set (0.001 sec)

MariaDB [bioskop]> desc film;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id_movi     | char(6)     | NO   | PRI | NULL    |       |
| member_id   | char(6)     | YES  | MUL | NULL    |       |
| movi_rented | varchar(10) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
3 rows in set (0.079 sec)

MariaDB [bioskop]> insert into film()
    -> values('1','1','Pirates of the Caribbean');
ERROR 1406 (22001): Data too long for column 'movi_rented' at row 1
MariaDB [bioskop]> alter table film change movi_rented movi_rented varchar(50);
Query OK, 0 rows affected (0.190 sec)
Records: 0  Duplicates: 0  Warnings: 0

MariaDB [bioskop]> insert into film()
    -> values('1','1','Pirates of the Caribbean');
Query OK, 1 row affected (0.052 sec)

MariaDB [bioskop]> insert into film()
    -> values('2','1','Clash of the Titans');a
Query OK, 1 row affected (0.117 sec)

    -> insert into film()
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'a
insert into film()' at line 1
MariaDB [bioskop]> insert into film()
    -> values('3','2','Forgetting Sarah Marshal');
Query OK, 1 row affected (0.032 sec)

MariaDB [bioskop]> insert into film()
    -> values('4','2','Daddys Little Girls');
Query OK, 1 row affected (0.117 sec)

MariaDB [bioskop]> insert into film()
    -> values('5','3','Clash of the Titans');
Query OK, 1 row affected (0.118 sec)
use near '.member_id=film.member_id
where full_name = 'JanetJones'' at line 3
MariaDB [bioskop]> select pemesan.full_name, film.movi_rented
    -> from film
    -> inner join pemesan on pemesan.member_id = film.member_id
    -> where full_name = 'JanetJones';
+------------+--------------------------+
| full_name  | movi_rented              |
+------------+--------------------------+
| janetjones | Pirates of the Caribbean |
| janetjones | Clash of the Titans      |
+------------+--------------------------+
2 rows in set (0.067 sec)
