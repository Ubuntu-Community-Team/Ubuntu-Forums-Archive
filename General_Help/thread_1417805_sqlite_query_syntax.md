---
title: "sqlite query syntax"
date: 2010-02-27
forum: General Help
---

### Post by GOwin on 2010-02-27
Could anyone help me with this sqlite query please? I have these tables:

cities (id string, name string)
neighbors (center string, adjacent string)

neighbors.center and neighbors.adjacent are foreign keys of the cities.id primary key.

cities.id, cities.name
1	city 1
2	city 2
3	city 3
4	city 4
5	city 5
6	city 6

neighbors.adjacent
1	2
1	3
2	1
2	4
3	1
3	4
4	2
4	3
4	5
5	4

what is the query to list all cities and its neighboring cities like this?

cities.id, cities.name, neighboring cities (id), number of neighbors
1|city 1|2,3|2
2|city 2|1,4|2
3|city 3|1,4|2
4|city 4|2,35|3
5|city 5|4|1
6|city 6||0

or; cities.id, cities.name, neighboring cities (name), number of neighbors
1|city 1|city 2, city3|2
2|city 2|city 1, city 4|2
3|city 3|city 1, city 4|2
4|city 4|city 2, city 3, city 5|3
5|city 5|city 4|1
6|city 6||0

---

### Post by kostkon on 2010-02-27
Is this for a homework?

---

### Post by n0dix on 2010-02-27
sorry for hijacking the thread. @kostkon you don't like to do the homework of someone?

---

### Post by lovinglinux on 2010-02-27
[http://www.sqlite.org/docs.html](http://www.sqlite.org/docs.html)
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Sef on 2010-02-27
Closed.  Homework.

Update:  OP explained it was not homework, so reopened the thread.

---

### Post by GOwin on 2010-03-01
The solution:

```

SELECT n.center, c1.name, group_concat(c2.name), count(*)
FROM cities AS c1, cities AS c2, neighbors AS n
WHERE n.center = c1.id
	AND n.neighbor = c2.id
	AND k1.year = "2001"
	AND k2.year = "2001"
GROUP BY n.center, c1.name;

```

This wasn't homework. Thank you to those kind people who *bothered* to asked.

---

