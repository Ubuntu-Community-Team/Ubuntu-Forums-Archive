---
title: "Evolution Does Not Start"
date: 2009-10-31
forum: General Help
---

### Post by dlobo on 2009-10-31
Dear All,

I just upgraded to 9.10 64-bit version and I am having issues starting Evolution.
I tried to start it from the command line to check if I could see any output and this is what I get:
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by evolution)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libemiscwidgets.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libetable.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libeutil.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libeutil.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libebook-1.2.so.9)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libedataserver-1.2.so.11)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libsoup-2.4.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: relocation error: /usr/lib/evolution/2.28/libeutil.so.0: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference

Has anybody come across this problem?

Thanks a lot
Respectfully

dmlobo

---

### Post by martinezo on 2009-11-10
I have the same problem with Ubuntu 9.10 32bits after update Postgresql 8.4

---

### Post by yurx cherio on 2009-11-12
This is very bizarre!
PostgreSQL 8.4 messes up python libraries!!!
I spent an hour trying to find out why my Printer configuration screen doesn't start. Running it from terminal window (system-config-printer) revealed that there is a problem with python library versioning:

>> system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 108, in <module>
    from GroupsPane import *
  File "/usr/share/system-config-printer/GroupsPane.py", line 21, in <module>
    from GroupsPaneModel import *
  File "/usr/share/system-config-printer/GroupsPaneModel.py", line 19, in <module>
    import libxml2
  File "/usr/lib/pymodules/python2.6/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference

Now, I searched for instances of libxml2.so:

>> locate libxml2.so
/opt/PostgreSQL/8.4/lib/libxml2.so.2
/opt/PostgreSQL/8.4/pgAdmin3/lib/libxml2.so
/opt/PostgreSQL/8.4/pgAdmin3/lib/libxml2.so.2
/opt/PostgreSQL/8.4/pgAdmin3/lib/libxml2.so.2.6.32
/usr/lib/libxml2.so.2
/usr/lib/libxml2.so.2.7.5
/usr/lib32/libxml2.so
/usr/lib32/libxml2.so.2
/usr/lib32/libxml2.so.2.7.5

And the last step - I uninstall PostgreSQL 8.4 ........ and my Printer configuration dialog showed up!
Everything is working without errors. I couldn't believe my eyes!

---

### Post by puldzian on 2009-11-13
my situation:
if launched in terminal: the pointer just blinks and blinks and nothing happens. 
if launched via menu/gnome-do: evolution appears on the panel then just disappears.
oh, and then it sits in gnome-system-monitor eating around 4mb. i don't know if it's the same cause as in above posts, but the result is obviously the same. postgresql is not installed.

---

### Post by camurgo on 2009-11-25
> **dlobo said:**
> Dear All,

I just upgraded to 9.10 64-bit version and I am having issues starting Evolution.
I tried to start it from the command line to check if I could see any output and this is what I get:
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by evolution)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libemiscwidgets.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libetable.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libeutil.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.28/libeutil.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libebook-1.2.so.9)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libedataserver-1.2.so.11)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libsoup-2.4.so.1)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: /opt/PostgreSQL/8.4/lib/libxml2.so.2: no version information available (required by /usr/lib/libgnomevfs-2.so.0)
evolution: relocation error: /usr/lib/evolution/2.28/libeutil.so.0: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference

Has anybody come across this problem?

Thanks a lot
Respectfully

dmlobo

The exact same thing is happening to me, exact same output. I'm on Ubuntu 9.10 32 bits, and the problem started after I upgraded to Postgres8.4 (which I did weeks after upgrading from Jaunty to Karmic).

---

### Post by dlobo on 2009-12-03
Uninstalling Postgres 8.4 did the trick for me too. Now I just need to figure out a way to install Postgres again without breaking Evolution. :-)

---

### Post by dcstar on 2009-12-03
> **dlobo said:**
> Uninstalling Postgres 8.4 did the trick for me too. Now I just need to figure out a way to install Postgres again without breaking Evolution. :-)

Download a previous version from here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by camurgo on 2009-12-06
> **dlobo said:**
> Uninstalling Postgres 8.4 did the trick for me too. Now I just need to figure out a way to install Postgres again without breaking Evolution. :-)

Yeah, for me too. I actually went to the postgresql mailing lists and reported this problem (that is, postgresql "one-click install" messing up system libraries and rendering other applications, such as Evolution, unable to function). They acknowledged it was a bug and they will fix it as soon as possible.

But either way, for ubuntu the recommendation is to install the repositories package, in which such problem wouldn't happen, that is:

sudo apt-get install postgresql
or
sudo aptitude install postgresql

(that will install postgresql8.4 which is the supported version on Karmic)

At the beginning the above was what I tried, but I couldn't get postgres to start, so I decided downloading and installing it manually. But then the evolution problem started.
After hearing from them that I should go back and install it from the repositories, that's what I did. This time I purged all postgres configuration files and did a "fresh reinstall" from the repositories, now everything is working(postgres, evolution, etc)! Finally :)

---

### Post by Abhijit Navale on 2010-07-20
I have the same problem too. Please help.

---

### Post by leehach on 2011-04-25
This is an old thread, but I just ran into the same problem installing Postgres 8.4 on a new machine, specifically that I couldn't start the Printer applet (system-config-printer). I was installing EnterpriseDB Postgres Standard Server, and the Printer applet stopped working. I Googled the error message about python not importing libxml2mod, and found this thread.

Note that I was able to avoid having to uninstall Postgres or switch from the non-repository installer (I really like the EnterpriseDB packaging) by using StackBuilder to upgrade from 8.4.1.2 to 8.4.7.1. Possibly most people won't run into this problem if they keep their Postgres updated to the most recent version, but I hadn't gotten around to it since first doing the install last month.

--Lee

---

