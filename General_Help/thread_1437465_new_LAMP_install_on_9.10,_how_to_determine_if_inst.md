---
title: "new LAMP install on 9.10, how to determine if install completed?"
date: 2010-03-23
forum: General Help
---

### Post by ijason on 2010-03-23
greetings. 

i followed this thread : [http://ubuntuforums.org/showthread.php?t=1435748&highlight=LAMP](http://ubuntuforums.org/showthread.php?t=1435748&highlight=LAMP)

and used the tasksel command to install LAMP from the menu. the thing churned along and eventually asked me for a mySQL admin password, and then dropped back into a normal terminal window. 

next step was to check the config file for apache... but while typing "apache" and hitting the tab key returns "apache2", "grep httpd.conf" just hangs the terminal window and never returns anything. 

trying to follow this guide to starting apache : [http://httpd.apache.org/docs/2.0/invoking.html](http://httpd.apache.org/docs/2.0/invoking.html)

am i naive for thinking the tasksel menu actually installed the packages? did it just download them some place for me to install?

also of note (perhaps) is that i see no apache in my usr/local, and that "grep apache2" returns long wait times and no results :/

---

### Post by dcstar on 2010-03-23
> **ijason said:**
> 
........
also of note (perhaps) is that i see no apache in my usr/local, and **that "grep apache2" returns long wait times and no results** :/
Really?:

```
man grep
```

---

### Post by ijason on 2010-03-23
> **dcstar said:**
> Really?:

```
man grep
```

i'm looking through the man now, i'm assuming you're implying i'm using grep wrongly? any advise about the missing apache folder or whether the packages are installed VS downloaded by the method i used? :)

---

### Post by ijason on 2010-03-24
taking a hint from dcstar that i'm likely using the wrong tool to try and find files on the machine, i spent a minute in the actual GUI and made use of the >places>search for files

searching for apache returned very little of anything that looks like the package fully installed. 10 or so scattered files, and no main system folders named apache. no results for "httpd.conf"

when i check the synaptic package manager, it shows me as having installed apache... in /usr/lib/apache2. why did this not show up on the file search? and does that mean there IS a httpd.conf file out there but my file search is useless for finding it?

---

