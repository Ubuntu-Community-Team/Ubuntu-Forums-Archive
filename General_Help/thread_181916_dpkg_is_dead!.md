---
title: "dpkg is dead!"
date: 2006-05-25
forum: General Help
---

### Post by orlox on 2006-05-25
Hi. A friend of mine is getting this error on trying to use dpkg:

/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file

He tried to reinstall dpkg by synaptic to no avail...Is there anyone who knows a reason for this failure, or a solution???

---

### Post by rykel on 2006-05-25
[QUOTE=orlox]Hi. A friend of mine is getting this error on trying to use dpkg:

/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file

He tried to reinstall dpkg by synaptic to no avail...Is there anyone who knows a reason for this failure, or a solution???[/QUOTE]

I suggest that he try the following commands while connected to the internet:
[INDENT][B]
sudo apt-get update
sudo dpkg -i <any .deb file>[/B][/INDENT]

Of course, if he is using Dapper Drake Beta, then he does not even need to use the commandline to install deb files, because the job is done with gdebi, a GUI for dpkg/apt-get...   :)

---

