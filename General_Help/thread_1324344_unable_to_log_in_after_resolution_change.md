---
title: "unable to log in after resolution change"
date: 2009-11-12
forum: General Help
---

### Post by harbingerofdoom on 2009-11-12
hey all, thought id see if anyone could help before i reinstall yet again.

i used the windows installer to get xbuntu on my laptop, not sure if that has any part or not however. 
problems started when i lost my notification area. suddenly everything started crawling and i could not get the panel manager to come up at all while it took about five minutes to start firefox. 
while digging around i changed the screen resolution (something i had been intending to do to begin with) and decided to restart the system. it was fine and did not complain about the new resolution at all for about two minutes while i continued to try and get the panel manager back and then all the sudden everything locked up.

tried to reboot and i got a message that something critical was no longer responding which was required to restart the system and from that point refused to take any input from anything (keyboard mouse stopped working).

forced the system down (yes i know, bad bad... but what are you going to do in that situation?) when it came back up everything appeared normal but when i go to log in now, the monitor does its normal shutdown-startup thing when the resolution is being changed and then it kicks me right back to the login screen.

i can boot to a console and run sudo commands so its not THAT bad and this install is only a few days old and i have never used linux on any of my laptops (let alone ubuntu) so im still in the "oops, better not do that ever again" mode of checking things out so if i have to reinstall, it wont kill me, but id rather figure this out.

---

### Post by 824957q on 2009-11-12
well i see the probblem here i had this before so this is what your gonna do..install xubuntu again... thats it theres no other way buddy

---

### Post by cariboo on 2009-11-12
Please don't tell someone to reinstall, if you don't know how to solve the problem. Reinstalling is a Windows solution and in most cases is a waste of time.

If you can start in a console, half the battle is already over. At the prompt type:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You should now be able to restart and get to you desktop, you will have to reinstall your graphics drivers, but otherwise you should be OK.

---

### Post by harbingerofdoom on 2009-11-12
> **cariboo907 said:**
> Please don't tell someone to reinstall, if you don't know how to solve the problem. Reinstalling is a Windows solution and in most cases is a waste of time.

If you can start in a console, half the battle is already over. At the prompt type:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```You should now be able to restart and get to you desktop, you will have to reinstall your graphics drivers, but otherwise you should be OK.

wow now THATS interesting.
says no such file when i try that. since that really cant be, i went & poked around in my X11 folder and sure enough, there is no xorg.conf file in there at all.

---

### Post by harbingerofdoom on 2009-11-12
also, im sure this means something i just am not sure what.... but if i drop to a root shell and then start X from there, i get to a desktop no problems, so im sure that it has something to do with the prefs for that particular user.

going to create a new login & see if that gets me in. maybe ill just have to remove and re-create the user?

---

### Post by harbingerofdoom on 2009-11-12
huh... and the strangeness continues.
if i boot to cli, log in with the offending userID THEN sudo startx, it logs in i still have no notification area and I cant pull up the panel manager still, but it does log in.

If i try to log in from the login manager, it does what i described in the first post.
created a new user and i can log in under the new user with no issues at all (need to add that user to sudoers list though)

---

### Post by harbingerofdoom on 2009-11-12
so here is the problem in a nutshell after doing some stuff... when i change the screen resolution to anything larger than 1024x768 is when this happens. change them back to 1024x768 and i can log in no problems. log in via term THEN start x with higher resolutions? no problem. anything larger + try to log in after changing? that when all hell starts breaking loose.

so, from that, it occurrs to me that x may not be the problem but something else.... so here is the hardware that im using.

Compaq nc6120
pM 740 proc
768mb ram
i915 chipset
connecting to a 21" trinitron CRT. (laptop panel stays closed except for starting the system and forced shutdowns via power button)

i have a suspicion that there is a config issue somewhere, but i dont know nearly enough to even know where to start looking in this situation... 

further ideas guys?

---

