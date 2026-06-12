---
title: "Xubuntu 9.10 login issue"
date: 2010-03-15
forum: General Help
---

### Post by s1mp13m4n on 2010-03-15
Hello everyone.  I was given an older Gateway laptop.  It has these specs:

Celeron 1.6GHZ cpu
512MB Ram
40GB HDD
shared Intel video
802.11g wireless

I installed Xubuntu 9.04 on it and performed the upgrade via the update manager.  Yesterday the laptop worked fine, but today I can not log in to it at all.  I type in my username and password and the screen flickers and goes back to the login screen.  How do I fix this?  Why after all this time that 9.10 has been out has Ubuntu not fixed this in an update or a patch?  Thank you for the help.

---

### Post by bobcollard on 2010-03-15
> **s1mp13m4n said:**
> Hello everyone.  I was given an older Gateway laptop.  It has these specs:

Celeron 1.6GHZ cpu
512MB Ram
40GB HDD
shared Intel video
802.11g wireless

I installed Xubuntu 9.04 on it and performed the upgrade via the update manager.  Yesterday the laptop worked fine, but today I can not log in to it at all.  I type in my username and password and the screen flickers and goes back to the login screen.  How do I fix this?  Why after all this time that 9.10 has been out has Ubuntu not fixed this in an update or a patch?  Thank you for the help.
At the login screen try to open the Sessions menu on the bottom and click on Xfce.  It is looking for a desktop.  Mine did that before, its as if it lost the settings at shutdown.

---

### Post by s1mp13m4n on 2010-03-15
On the bottom of the login screen there is a selection of two XFCE sessons and one Xtern sesson.  I have tried both XFCE sessons and it will not log in and I have tried the Xtern sesson but I do not know the command line, even though I did try the command startx and when i did that I got an error message saying that the user Paul which is me did not have permissions for something or other.  I am the one who installed Linux and set the user and password so why would I not have permission on my own machine?  LOL  :)  Something told me not to upgrade from 9.04 to 9.10 but I did it anyway.  :)  Now how to go about fixing it.  I am not finding much on Google other than the fact that yes there is a problem.  :)

---

### Post by bobcollard on 2010-03-15
> **s1mp13m4n said:**
> On the bottom of the login screen there is a selection of two XFCE sessons and one Xtern sesson.  I have tried both XFCE sessons and it will not log in and I have tried the Xtern sesson but I do not know the command line, even though I did try the command startx and when i did that I got an error message saying that the user Paul which is me did not have permissions for something or other.  I am the one who installed Linux and set the user and password so why would I not have permission on my own machine?  LOL  :)  Something told me not to upgrade from 9.04 to 9.10 but I did it anyway.  :)  Now how to go about fixing it.  I am not finding much on Google other than the fact that yes there is a problem.  :)
If this is an upgrade and not a full install then you have answered your own question.  Forums across the board. I belong to eight of them, have warnings in all distributions against upgrading.  Any sudo command calls for a password, that's a given.

---

### Post by the_karmic_koala on 2010-03-15
i'm not an expert but i would suggest you open a teminal session,create a partition,save all docs to it then reinstall/re format that partition...i dont know the command line but i'm sure you can do it...then just copy from partition delete the partition and resize the new xubuntu one...??..have you tried the RESCUE option on xubuntu disk?...i've never had to use it but it might be useful..

---

### Post by s1mp13m4n on 2010-03-15
OK here is what I know.  If I boot the laptop and it boots normally...I slect my username and hit enter.  I type my password and hit enter...all of this is in the Xubuntu GUI.  It goes back to the login screen.  Now if when Linux is booting up I press the esc key can select (recovery mode) and then from the menu that pops up after some text goes by I then select the first option whcih is boot from hard drive, it then goes to a command prompt asking me for my username and password, then it logs in the CLI.  At that point if I type startx from that CLI the machine logs in to the GUI and works just fine.  So, what is going on here?  Why can I not just log in from the GUI in the first place?  Something must be crashing.

---

### Post by bobcollard on 2010-03-15
I just installed Xubuntu 9.10, fresh, from a Live CD.  Restarted it six times with upgrades added, applications and configured it since I wrote last.  No startup issues.  Either you have a bad disk or you need to start from scratch.  Since you can get on and your computer works, I doubt it is the disk.  I've been running Xfce for awhile now, mostly with other distributions like PC/OS which I have just erased and started from scratch.  I cannot tell you the lengths I went through to help you and I have failed because I cannot get the same problem to show itself. I know this shows Gnome, but, if you look at your system monitor you will see the same thing, the only proof I have.  Look at this attachment:

---

### Post by monsoongroover on 2010-03-15
I had the same problem.  See post # 8567501 by Psumi.

---

### Post by s1mp13m4n on 2010-03-15
> **bobcollard said:**
> I just installed Xubuntu 9.10, fresh, from a Live CD.  Restarted it six times with upgrades added, applications and configured it since I wrote last.  No startup issues.  Either you have a bad disk or you need to start from scratch.  Since you can get on and your computer works, I doubt it is the disk.  I've been running Xfce for awhile now, mostly with other distributions like PC/OS which I have just erased and started from scratch.  I cannot tell you the lengths I went through to help you and I have failed because I cannot get the same problem to show itself. I know this shows Gnome, but, if you look at your system monitor you will see the same thing, the only proof I have.  Look at this attachment:

Thank you for all of your hard work and effort.  :)  I will do what you said and try a fresh install and a new dick.  :)  Thanks for all the time you spent working this out.  I have nothing on the laptop to worry about getting rid of, so we can just start over.

---

### Post by s1mp13m4n on 2010-03-15
> **monsoongroover said:**
> I had the same problem.  See post # 8567501 by Psumi.

You know, I just read those posts and I have changed my screen resolution to make things bigger for me.  I have a visual impairment (legally blind) so I need a larger screen to see things.  I wonder if that is my issue.  I will try the fix listed in that other post.  If it does not work, I can always re-install the OS from scratch.  I am not interesting in a pretty looking GUI, I am more interested in function and a quality OS.  I am trying to use Windows less and less.  Thanks for the help.

I did what was listed in that post and it seemed to work.  What it seemed to do was now I log into the laptop via the command line and when I type startx, the GUI loads and all seems to be fine.  I can live with that, I do not need the GUI login.  :)I will let you know how it goes.  Thanks for the help.

---

### Post by bobcollard on 2010-03-16
> **s1mp13m4n said:**
> Thank you for all of your hard work and effort.  :)  I will do what you said and try a fresh install and a new dick.  :)  Thanks for all the time you spent working this out.  I have nothing on the laptop to worry about getting rid of, so we can just start over.
Be sure to check the md5sum before you burn the disk.

---

