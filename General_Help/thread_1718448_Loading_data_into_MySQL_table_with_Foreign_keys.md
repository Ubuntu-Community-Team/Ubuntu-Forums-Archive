---
title: "Loading data into MySQL table with Foreign keys"
date: 2011-03-31
forum: General Help
---

### Post by petersfreeman on 2011-03-31
I have a problem loading data into a MySQL table.  I'm using MySQL Workbench and with this code:
```
load data local infile '~/LegLoadTest.csv'
into table Journeys.Leg
fields terminated by ','
lines terminated by '\n'
ignore 1 lines
(idTour,LegNum,StartLocation,EndLocation)
;
```
I get this error message:
```
Cannot add or update a child row: 
a foreign key constraint fails (`Journeys`.`Leg`, 
CONSTRAINT `fk_Leg_Location1` FOREIGN KEY (`StartLocation`) 
REFERENCES `Location` (`idLocation`) 
ON DELETE NO ACTION ON UPDATE CASCADE)
```
I can create the records manually by typing in the data and everyting works fine, but when I try to load it in, it does not work, even if my load data set contains only only one record.

When I used to use Microsoft Access, I encountered a similar problem.  I solved the problem then by first loading in all the fields except the foreign keys.  This created the records.  I then updated the records by adding the foreign key fields, one field per update query.

I have two questions.
[LIST=1]
[*]Is there a better forum for this problem?
[*]Is there a more elegant way of loading data that has foreign keys?
[/LIST] 

Thank you,

Peter

---

