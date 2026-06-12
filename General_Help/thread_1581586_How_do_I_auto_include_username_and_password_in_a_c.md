---
title: "How do I auto include username and password in a command?"
date: 2010-09-25
forum: General Help
---

### Post by jeight on 2010-09-25
I'm using the seamless mode in rdesktop to connect to a windows host machine. The command looks something like this:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p password
I need to put this on each desktop and I would like to copy paste the command.  Is there anyway I can write the command so it automatically takes the name and password of the current session user. 

Thanks in advance!

---

### Post by Tibuda on 2010-09-25
For the username you can use $USER, but not for the password, as it would be a security failure.

---

### Post by jeight on 2010-09-25
Then how can I mask the users password in the command line.  I don't want other people to be able to get their password.

---

### Post by bodhi.zazen on 2010-09-25
Take a look at expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/archive/feed/56066](http://www.linux.com/archive/feed/56066)

---

