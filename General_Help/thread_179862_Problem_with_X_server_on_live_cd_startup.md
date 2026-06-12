---
title: "Problem with X server on live cd startup"
date: 2006-05-20
forum: General Help
---

### Post by iMlazy on 2006-05-20
OK, so I am trying to use the live CD on a fairly new box, and I have downloaded the live CD stuff successfully, burned it successfully, etc.

The problem is that when it gets after the "Run level 2" (where everything is "ok"-ed), it then tells me that:
> Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Then takes me to a command line which  says "bash bash" something or other.

I have reformated my hard drive and I am using Microsoft Windows XP Media edition. I installed GTK onto the thing, and that's all I have right now. (And I know very little 'bout linux)

As the tree said to the lumberjack, I'm stumped :-k

---

### Post by dermotti on 2006-05-20
Ide try running
[B]
sudo dpkg-reconfigure xserver-xorg[/B]

and select **VESA** as your driver

then run

**ps -e | grep gdm**

and you shoul see something like

**2324 GDM**

then type

 **sudo kill 2324**

---

### Post by iMlazy on 2006-05-20
I got as far as selecting "VESA" then it threw me back into "Run Level 2".

It hung at "Checking battery level" as I am on a PC, I waited 25 minutes and nothing happened.

I didn't have the opportunity to run "ps -e | grep gdm" or "kill sudo".

:-|

---

