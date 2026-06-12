---
title: "/usr/local"
date: 2006-06-20
forum: General Help
---

### Post by flipkick on 2006-06-20
I'm trying to install several webtools on my dapper installation.

[This guide]("http://www.linuxjava.net/howto/webapp/#ant") will show me how to do this. My question:

Is the suggested path below appropriate for ubuntu ?

And where is my java folder where i put the jdk ?

Install Jakarta ANT
tar xvfz jakarta-ant-1.6.0
mv jakarta-ant-1.6.0 /usr/local
cd /usr/local
ln -s jakarta-ant-1.6.0 ant
ln -s /usr/local/ant/bin/ant /usr/local/bin/ant

Thanks for some basic help.

---

### Post by taurus on 2006-06-20
Don't forget to include the "sudo" in front of those commands since you need to be root to write to /usr/local...  Otherwise, you will get an error message about permission.

---

### Post by flipkick on 2006-06-20
Alright, that's for sure. Thanks :)

Does anyone of you know a similiar tutorial that is more contemporary ?

I'm not looking for the ubuntu howtos and .deb packages installation.

Because if I install everything from synaptic (apache, postgre, tomcat, ant..) i don't understand how this stuff is working.

Thanks for some advance tipps.

---

### Post by giants_fan on 2006-06-20
You can pretty much install these things anywhere.  The /usr/local directory is a very common place for it.  /opt is also appropriate.

The other (very good) option is to install them in your /home directory--that way you don't need to run the application as root.  Tomcat, for instance, will write log files out into it's "logs" directory and if it's in /usr/local, you'll need to run as root (using sudo).

One thing I would recommend is using symlinks and make say /usr/local/tomcat point to /usr/local/jakarta-tomcat-5.0.28.  That what I do and that lets me test my stuff against different versions by just changing the symlink.  You would set your CATALINA_HOME, then, to /usr/local/tomcat.  Works like a charm.

---

