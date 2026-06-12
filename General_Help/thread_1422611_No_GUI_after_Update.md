---
title: "No GUI after Update"
date: 2010-03-05
forum: General Help
---

### Post by fester225 on 2010-03-05
Update Manager told me to do an Update for 9.10 last night (4MAR2010) which started with a CUPS update.

After the update, I was supposed to restart the machine. On restart the machine would no longer boot to the GUI. Instead I go to a command line. I tried using one of the recovery options during boot, but all I get is the command line.

How do I get my GUI back?

---

### Post by QIII on 2010-03-05
Did you notice a line "The following packages have been held back:"?

Using 

```
sudo apt-get upgrade
```will often hold back linux-image and linux-headers.  You might want to upgrade them and see what happens.

There is some confusion about "dist-upgrade".  This will not automatically upgrade you to the next version.  ("do-release-upgrade" will, so DON'T do that, particularly with the "-d" switch, which will get you the current development version.)

So long as you have not changed your sources.list, "dist-upgrade" will upgrade you to the latest and greatest for everything in your current version.

When I do "upgrade", I usually follow it immediately with "dist-upgrade".  That will catch the new kernel.  It is possible that something you upgraded is not playing well with your older kernel.  I got a new kernel last night.

So (AFTER you wait for someone else to chime in and tell you I am an idiot!), try

```
sudo apt-get dist-upgrade
``` in the terminal.

---

### Post by patchwork on 2010-03-05
Will x load if you login in the console and type

```
startx
```
?

---

### Post by Jonah Bron on 2010-03-05
I have this problem, too.  I have to use links2 (which, by the way, is a life-saver) to browse this site.  I am experiencing the exact same symptoms.  What is the deal?

---

### Post by QIII on 2010-03-05
In Karmic (and from now on), I believe the command to issue is

```
sudo service gdm start
```

assuming you are using GNOME.

If KDE, I think it's ... kdm start...

---

### Post by Jonah Bron on 2010-03-05
I ran that command, and nothing happened.  It just said
```
gdm start/running, process 6022
```
Any other ideas?

---

### Post by patchwork on 2010-03-05
Jonah, answered you back in your other post.

QIII, you can start the x server without running gdm, though, yes, gdm start will work just fine

---

### Post by krakra on 2010-09-30
> **QIII said:**
> Did you notice a line "The following packages have been held back:"?

Using 

```
sudo apt-get upgrade
```will often hold back linux-image and linux-headers.  You might want to upgrade them and see what happens.

There is some confusion about "dist-upgrade".  This will not automatically upgrade you to the next version.  ("do-release-upgrade" will, so DON'T do that, particularly with the "-d" switch, which will get you the current development version.)

So long as you have not changed your sources.list, "dist-upgrade" will upgrade you to the latest and greatest for everything in your current version.

When I do "upgrade", I usually follow it immediately with "dist-upgrade".  That will catch the new kernel.  It is possible that something you upgraded is not playing well with your older kernel.  I got a new kernel last night.

So (AFTER you wait for someone else to chime in and tell you I am an idiot!), try

```
sudo apt-get dist-upgrade
``` in the terminal.
Thank you QIII. Your advice about using "dist-upgrade" solved my problem.

---

### Post by mistypotato on 2010-11-20
same dilemma...

didnt work for me ):P

---

