---
title: "Where are the mysql data?"
date: 2010-02-06
forum: General Help
---

### Post by mac666 on 2010-02-06
Hey
My ubuntu computer died where i have my webserver, and i cant seem to find where the mysql data files are.

Anyone no where they are hiding? could i just copy them into my new mysql computer without hassels?

my conf file is pointing to /var/lib/mysql as data folder, but i dont have that folder? :|

---

### Post by cje on 2010-05-01
Hi mac666
I suppose you your looking for the var/lib/mysql directory

---

### Post by mac666 on 2010-05-03
> **cje said:**
> Hi mac666
I suppose you your looking for the var/lib/mysql directory
And the winner is you for reading my whole post

---

### Post by Mazin on 2010-05-03
My MySQL files are in /var/lib/mysql like one would expect, and that's the default configuration.  You're absolutely sure that folder doesn't exist?  Maybe you need to be root to see it?

---

### Post by WorMzy on 2010-05-03
That is where mine are, I can only assume that you have either a) set your mysql up differently, or b)  deleted the folder.

Try doing this:
```
sudo updatedb && locate mysql/[COLOR=Red]*<A DBNAME HERE>*[/COLOR]
```For example, 'locate mysql/wormzy_db1' tells me it is located in /var/lib/mysql/

---

### Post by mac666 on 2010-05-06
this topic is way to old
i did everything in my power to find it but it wasnt there anymore. case closed

---

