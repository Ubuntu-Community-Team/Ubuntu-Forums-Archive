---
title: "Graphics driver for VirtualBox / Linux gaming."
date: 2011-12-08
forum: General Help
---

### Post by Digi984 on 2011-12-08
So since Ubuntu seems to really not like most of the windows games I try to run, even with wine, I am trying to set up a virtualbox running XP.  But the graphics driver seems to be a generic one just for virtualbox.  I added on the directx compatibility but still the graphics driver seems to only run low video settings.  Is there a way to get virtualbox to utalize my hardware video card?(Nvidia Geforce 9600GT).  I've tried to download the driver for it but can't install it because virtualbox isn't recognizing the card.  

I'm not dead set on using virtualbox but I am trying to run the following programs on Ubuntu 11.04(would prefer not to upgrade to 11.10 as I like 11.04 better, but I will if it makes things run.).  I will also list the problems I am having with each incase there is an alternate solution.

World of Warcraft - Frequent crashes when updating and lag.
Curse Client - ToC screen goes blank when tryng to install won't continue
Steam - Program itself seems to freeze alot and won't load the games it installs
Dragon Age Origins(And Awakening X-Pack) - Screen goes blank at ToC agreement and won't continue.

Mass Effect - Very choppy videos and game play and low graphics quality.


---
I really enjoy Ubuntu which is why I am refusing to go back to Windows full time but is there another linux destro that is perhaps better for games than linux?  Preferably one that is similar in operation to ubuntu.

Sorry for all the newb questions but I am doing the best I can to figure this all out.

---

### Post by wildmanne39 on 2011-12-08
Hi, virtualbox does not play most games well.

For the other issues go to this link and do what is says and it will most likely fix most of your choopy issues, however I do not play games but I have read that world of war craft plays ok in wine.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thank you

---

### Post by Digi984 on 2011-12-08
> **wildmanne39 said:**
> Hi, virtualbox does not play most games well.

For the other issues go to this link and do what is says and it will most likely fix most of your choopy issues, however I do not play games but I have read that world of war craft plays ok in wine.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thank you


I'll give that a shot thanks.  But I thought compiz was more to fix choppy internet browsers?  In either case we shall see.  Thanks.


*Edit*
Didn't help too much.  The cinematic for the game was still very choppy.

---

### Post by wildmanne39 on 2011-12-09
Hi, there are probably other settings that can be changed to help hopefully someone will post another suggestion.

Also in ccsm click on composite and set the refresh rate to 60 that should help.

Are you using unity in 11.04 or classic mode?

---

### Post by Digi984 on 2011-12-09
> **wildmanne39 said:**
> Hi, there are probably other settings that can be changed to help hopefully someone will post another suggestion.

Also in ccsm click on composite and set the refresh rate to 60 that should help.

Are you using unity in 11.04 or classic mode?

Using classic mode.  Okay I'll give it a shot.  Do you know off hand if 11.10 works better for games?  From what I have read it seems 11.10 has more problems but that could be just because it is a newer version.

---

### Post by wildmanne39 on 2011-12-09
Hi, that explains it you need to downgrade compiz settings manager before you change any settings in compiz in classic because there is a problem where it does not work right in classic mode.

Click on the second link in my signature and go down to the section in 11.04 and there is a link there to downgrade compiz.
Thank you

---

### Post by Digi984 on 2011-12-09
> **wildmanne39 said:**
> Hi, that explains it you need to downgrade compiz settings manager before you change any settings in compiz in classic because there is a problem where it does not work right in classic mode.

Click on the second link in my signature and go down to the section in 11.04 and there is a link there to downgrade compiz.
Thank you


So I followed the instructions to revert ccsm to the previous version.  It is installed but it won't open now.  And the super key(has the windows icon on my keyboard) doesn't do anything.

---

### Post by Synoc on 2011-12-09
You are better off creating a windows XP dual boot. the downside is that with Windows installed after it wipes the MBR, recommend doing a backup of /home to an external HHD and THEN installing windows to another partitoin and fixing the MBR, but to be honest... that particular gem is beyong my knowledge, I have am still trying to decipher grub2. I always start with a windows install then do an ubuntu one

perhaps someone else has a better understanding and we can both learn

---

### Post by oldtimer7777 on 2011-12-09
> **Synoc said:**
> You are better off creating a windows XP dual boot. the downside is that with Windows installed after it wipes the MBR, recommend doing a backup of /home to an external HHD and THEN installing windows to another partitoin and fixing the MBR, but to be honest... that particular gem is beyong my knowledge, I have am still trying to decipher grub2. I always start with a windows install then do an ubuntu one

perhaps someone else has a better understanding and we can both learn

Has this user tried installing their games in Wine using PlayOnLinux?

It is about 1/3rd the way down the checklist..  

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

WoW works great on my system. I don't know about those other games because I haven't tested them yet.  The other games I have worked great when I installed them with PlayOnLinux.

---

### Post by Digi984 on 2011-12-09
> **oldtimer7777 said:**
> Has this user tried installing their games in Wine using PlayOnLinux?

It is about 1/3rd the way down the checklist..  

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

WoW works great on my system. I don't know about those other games because I haven't tested them yet.  The other games I have worked great when I installed them with PlayOnLinux.


I have tried POL.  It works to install WoW but then crashing and graphics issues are still there.  Doesn't work for my other games.

---

### Post by wildmanne39 on 2011-12-09
Hi, are you sure you are using classic mode? reverting compiz should not have caused those kind of problems in 11.04 classic.

What did the super key do when you hit it before you reverted compiz? did it pop the launcher out on the left side of the screen?
Thank you

---

### Post by Digi984 on 2011-12-09
> **wildmanne39 said:**
> Hi, r u sure you are using classic mode? reverting compiz should not have caused those kind of problems in 11.04 classic.

What did the super key do when you hit it before you reverted compiz? did it pop the launcher out on the left side of the screen?
Thank you

Yup I'm sure.  Set in classic mode.   Super key doesn't do anything.  Didn't do anything before either as far as I know.

---

### Post by wildmanne39 on 2011-12-09
Hi open synaptic and make sure what version of compiz is being used and that only one is installed.
Thank you

---

