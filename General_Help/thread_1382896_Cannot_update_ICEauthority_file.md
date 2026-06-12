---
title: "Cannot update ICEauthority file"
date: 2010-01-16
forum: General Help
---

### Post by TBBucs on 2010-01-16
I'm running Ubuntu Studio 9.10 and just got the error **Cannot update ICEauthority file /var/lib/gdm/.ICEauthority** on boot-up and can't log in graphically (everything just hangs up and the form isn't displayed...just the background and logout button).  This error was accompanied by another one: **There was a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)**.

I've read about the first error in a ton of places, all of which say to check the file permissions.  I own the file and gave it 777 permissions (excessive, but for the sake of fixing it I decided to be generous).  That didn't work, so I tried deleting it altogether, which didn't work either.

What the heck is this file for, and how do I fix it?

---

### Post by Mickser_52 on 2010-01-16
Have you seen this post? [http://ubuntuforums.org/showthread.php?t=1382554]("http://ubuntuforums.org/showthread.php?t=1382554")

---

### Post by s_ø on 2010-01-18
I have just spent hours on that exact problem. I accidentally changed permissions on a large part of my karmic installation, trying to revert the disaster i chown almost everything to root (besides my home folder). But /var/lib/gdm and everything in it has to be owned by gdm.

so:
```
sudo chown -R gdm: /var/lib/gdm
```fixed it for me.

---

### Post by shaunfromthewildwoods on 2010-01-18
for me 

this fixed it

sudo chown shaun\: ~/.ICEauthority


replace shaun with your user name

---

### Post by vinayakgit on 2010-04-16
sudo chown -R gdm: /var/lib/gdm

This fixed the issue for me..Thanks a lot OS :)

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

### Post by jdk9 on 2010-05-07
Thanks! It runs, and a problem with sound was resolved (wich appeared at the same time)! :D

PS: Sorry for my english it's very bad.

---

### Post by zgembo on 2011-02-10
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

Works for me, too.
Thanks a lot.

---

### Post by smooth_b on 2011-05-02
What I did to get around the issue was switch to from GDM to KDM. This did not actually fix the problem but I am now able to log into my PC.

---

### Post by vanwykn on 2012-01-04
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

                                  ========0000000000000===========
This worked, after trying many other suggestions and almost going back to windows:P

---

