---
title: "login problems"
date: 2004-10-19
forum: General Help
---

### Post by danip on 2004-10-19
I was using my computer in a study hall and shut it down to go back to my dorm room and when i tried to log in to gnome it kept logging me out and giving me a message about the session lasting less than 10 seconds. I tried kde and i got an error "Warning unable to read ICE authority file: /home/steve/.ICEauthority". I tried to log into failsafe and it just logged me right back out. Where should i start in trouble shooting this?

---

### Post by triad169 on 2004-10-19
This looks like the same problem that was solved on the mailing list.  Will quote sollution:

From: Ben Edwards &lt;funkytwig &lt;at&gt; gmail.com&gt;
Subject: Re: Login Failure ICEauthority Corrupt
Newsgroups: gmane.linux.ubuntu.user
Date: Mon, 18 Oct 2004 12:36:10 +0100

> 
Are you sure it is corrupt and hot that the ovnership has been
changed?  Have you recently run k3b as root (this will change the
ownership of this file)?

Try the following

Ctrl+alt+F1 to get a text console and log in.

ls -l .ICE*

Is the ovnership root?  if so do

sudo chown _username_  .ICEauthority
sudo chgrp _username_ .ICEauthority

Ctrl+alt+F7 to go back to GDM

Ben.

Note replace *_username_* with your username.
Sounds like it should solve your problem.  As a note you can browse and search mailing list via gmane.  URL is as follows:

[http://news.gmane.org/gmane.linux.ubuntu.user](http://news.gmane.org/gmane.linux.ubuntu.user)

Triad

---

### Post by flygmaskin on 2004-10-19
Just a quick confirmation. I had the same problem a couple of weeks ago, and changing the ownership did fix it.

---

### Post by oddabe19 on 2004-10-19
I HAVE THE EXACT SAME PROBLEM!! I WAS ABOUT TO MAKE A POST.

sweet, i did just run k3b in root, so lemmie run those commands and see if it works.

I don't use KDE, but i hope that fixes gnome.

[Edit] IT WORKED!!! sweet... thanks guys!!!

---

### Post by cybrjackle on 2004-10-19
Just wondering if all of you opened up your "root" account with

```

sudo passwd root

```

I had the same problem with one box (the only one that has root enabled) and another friend had the same problem and he through the idea out that maybe it was from enableing the root account.

---

### Post by danip on 2004-10-19
awesome it worked just wondering though since i cant run k3b as root how am i supposed to run it with my reg user account.  It wont let me run it right now unless im root

---

### Post by Rancoras on 2004-10-19
That's where sudo comes in.

```
sudo k3b
```

Enter the password for your own account and you should be set.

---

### Post by HungSquirrel on 2004-10-19
Aren't you supposed to set UID of cdrecord to root before running K3B?  Then you should be able to run it as a regular user.  At least, that's how it was on another distro I used.

---

### Post by Clanman on 2004-10-22
[quote=Rancoras]That's where sudo comes in.

```
sudo k3b
```

Enter the password for your own account and you should be set.[/quote]

I also have the same problem. 
The above works for me (k3b runs) but the .ICEauthority file changes to root ownership and groupe

---

### Post by Rancoras on 2004-10-22
This should help with the K3B issues:

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988)

---

