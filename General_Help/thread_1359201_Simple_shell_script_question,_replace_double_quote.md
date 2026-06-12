---
title: "Simple shell script question, replace double quotes with ASCII character?"
date: 2009-12-19
forum: General Help
---

### Post by shawn.bordeaux on 2009-12-19
I am trying to load a .csv file into mysql using a shell script. Works fine so as long as I don't add; " ENCLOSED BY '"' " as part of the script.

I think the double quotes is throwing off the syntax because if I make it ENCLOSED BY '""' (using two double quotes) it executes but doesn't give me the results I am wanting. Basically I have a field that has a comma in it and is enclosed by quotes so I want it to load in a single field, "the, end" and not load as "the", "end". 

Is there a way to replace the double quotes with it's ASCII equivalent?

```

mysql -uroot -p123453 -e "LOAD DATA INFILE 'data.csv' INTO TABLE jras_intranet.test FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n' (firstname, lastname) ";

```
Thank you!

Shawn

---

### Post by shawn.bordeaux on 2009-12-19
Any suggestions? Thanks!

---

### Post by spillin_dylan on 2009-12-19
I don't know much about SQL, but does this work?  Trying to 'escape' the double quotes:
```
ENCLOSED BY '[COLOR="Red"]\[/COLOR]"'
```

---

