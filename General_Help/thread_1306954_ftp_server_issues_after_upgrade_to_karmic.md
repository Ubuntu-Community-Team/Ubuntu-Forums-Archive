---
title: "ftp server issues after upgrade to karmic"
date: 2009-10-30
forum: General Help
---

### Post by tinmanjim on 2009-10-30
Not being much of a command-line kind of guy (read: Windows User) I set up a testing server with proftpd and gadmin - proftpd.

After upgrading from jaunty to karmic, I can remotely access phpmyadmin and the http stuff, but the gadmin is telling me that it's inactive (the info bar says "Information: PRoFTP-1.3.2    Status: Deactivated". All the settings seem the same - it worked without a hitch until I upgraded, and now I can't seem to talk to it.

I've done a considerable amount of searching, but it seems that if you're a gui kind of guy there's not much info out there. I can find my way around and follow directions, but...

I did try 
> sudo /etc/init.d/proftpd start
and after a moment it said
> * Starting ftp server proftpd       [ OK ] 
After which
> /etc/init.d/proftpd status
Got me:
> ProFTPd is started in standalone mode, currently not running.

So now I'm at a point where I don't even know which direction to move or where to start. Any clues would be greatly appreciated.

---

### Post by horde on 2009-11-07
Same issue here.  Can anyone shed some light on this?

Many thanks.

---

### Post by suhana on 2009-11-07
Have a look at the "messages" log file, while you start the server:

```
tail -f /var/log/messages
```

and in a new terminal

```
sudo /etc/init.d/proftpd start
```

If nothing comes up, check the proftp server's configuration file, specifically it's log file names (I don't use proftpd so I'm afraid I can't remember the exact names)

Same setup will apply:

```
tail -f /var/log/proftpd-server.log
```
(Or whatever it's called)

and restart or attempt to start the server.

Hopefully that will direct you to a particular problem - perhaps with the configuration file itself that needs addressed.

---

### Post by horde on 2009-11-07
/var/log/messages didn't show anything interesting but /var/log/proftpd/proftpd.log said that port 21 was already bound.  So I changed the port # in /etc/proftpd/proftpd.conf and it worked again.

But how do I find out what's binding port 21?

---

### Post by suhana on 2009-11-07
```
sockstat
```

You may need to install this:

```
sudo apt-get install sockstat
```

sockstat simple lists open sockets. You can filter the information presented from it in a variety of ways, however at it's very basic usage, you should see that some "process" has bound to the relevent source address (probably *:21 in your case).

---

### Post by tinmanjim on 2009-11-07
> **horde said:**
> /var/log/messages didn't show anything interesting but /var/log/proftpd/proftpd.log said that port 21 was already bound.  So I changed the port # in /etc/proftpd/proftpd.conf and it worked again.

But how do I find out what's binding port 21?
Which port did you change to, and does it matter?

---

### Post by moorsey on 2009-12-23
not sure if this is related, but proftp doesn't appear in package manager any more in 9.10.  Although I did install it on a 9.10 box a couple of months ago.  Trying on my home server this morning and not getting anywhere!

---

### Post by aroos on 2009-12-23
Which port did you change to?

---

