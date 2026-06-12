---
title: "Compiling PenguinTV 1.75 help . . ."
date: 2006-06-19
forum: General Help
---

### Post by neub on 2006-06-19
Hi all,

I am a first time poster and have been using Ubuntu for a few months now.  Please tell me if I have posted this in the wrong place!

Anyway, I really like a program called PenguinTV on Dapper.  Unfortunately the version in the repositories (v 1.03) is quite out of date and doesn't really work very well. So feeling adventurous, I decided I would try to compile the latest version (1.75).  It is available here 

[http://prdownloads.sourceforge.net/penguintv/PenguinTV-1.75.tar.gz?download](http://prdownloads.sourceforge.net/penguintv/PenguinTV-1.75.tar.gz?download)

I uninstalled the version I had using the synaptic package manager.  I then "untared" the 1.75 version and explored to the directory using the command line.  

I ran the command 

sudo python setup.py install

and some stuff happened.  Then in the command line I type PenguinTV and voila!  Version 1.75 works!  I close the application and try to reopen it.  Now I get the following in my terminal

andrew@TabletUbuntu:~$ PenguinTV
Traceback (most recent call last):
  File "/usr/bin/PenguinTV", line 41, in ?
    penguintv.main()
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 1221, in main
    app = PenguinTVApp()    # Instancing of the GUI
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 84, in __init__
    self.firstrun = self.db.maybe_initialize_db()
  File "/usr/lib/python2.4/site-packages/penguintv/ptvDB.py", line 132, in maybe_initialize_db
    self.migrate_database_one_two()
  File "/usr/lib/python2.4/site-packages/penguintv/ptvDB.py", line 147, in migrate_database_one_two
    self.c.execute(u"""CREATE TABLE tags
pysqlite2.dbapi2.OperationalError: table tags already exists
andrew@TabletUbuntu:~$

and I can't use PenguinTV anymore!  I tried this on two computers and the same thing happens!  Anyone know whats going on?  

Thanks, I will give any other info that could help.

---

### Post by unf on 2006-06-19
Download **stable** version 1.05
Download **unstable** version 1.75
so it is not old


Have you got all dependencies

PenguinTV requires a relatively large number of python libraries.  Many of them come standard with distributions, but some must be downloaded separately.

    * Pysqlite version 2 or higher (version 2.2 strongly recommended) 
    * PyCurl
    * python-xml
    * python gtkhtml2 (on ubuntu, python-gnome2-extras package)
    * gnome bindings, including gconf and glade
    * pyrex is optional, and enables experimental mozilla renderrer

---

### Post by neub on 2006-06-19
Hey thanks unf!  It is working now.

I guess they arent kidding when they say its unstabe!

---

