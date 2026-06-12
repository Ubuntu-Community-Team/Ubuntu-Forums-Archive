---
title: "What are the difference between xubuntu and ubuntu??"
date: 2009-08-11
forum: General Help
---

### Post by twiztid-kid on 2009-08-11
I currently have xubuntu installed.  I was wondering if ubuntu is worth the extra hassle of re-booting my HDD and installing it.

---

### Post by zkriesse on 2009-08-11
Hey...first welcome to Ubuntu and Linux...glad you decided to join the Force...lol. Yes, there is a difference between Xubuntu and Ubuntu...Xubuntu is somewhat lighter than Ubuntu but other than that I'm not sure if there's much of a difference...let me know if this helped.

---

### Post by twiztid-kid on 2009-08-11
> **Zachk18 said:**
> Hey...first welcome to Ubuntu and Linux...glad you decided to join the Force...lol. Yes, there is a difference between Xubuntu and Ubuntu...Xubuntu is somewhat lighter than Ubuntu but other than that I'm not sure if there's much of a difference...let me know if this helped.

I have pretty much set my xubuntu up for my 512mb acer aspire one.  It runs alot faster than my xp partition.
I love linux, ive already familiared myself with the commands.  Already even used aircrack-ng.

How  much lighter would xubuntu be compared to ubuntu?
There is certain things i cannot seem to use as there is also limited guides and resources for xubuntu.  It seems to be widely less used than ubuntu.

---

### Post by TheNosh on 2009-08-11
you don't need to pick one. you can just install the ubuntu-desktop package on your existing xubuntu installation and then you can pick either desktop environment each time you boot up.

---

### Post by twiztid-kid on 2009-08-11
> **TheNosh said:**
> you don't need to pick one. you can just install the ubuntu-desktop package on your existing xubuntu installation and then you can pick either desktop environment each time you boot up.


Okay, is that feasible with limited loss of performance to a fresh installation.

---

### Post by zkriesse on 2009-08-11
> **twiztid-kid said:**
> I have pretty much set my xubuntu up for my 512mb acer aspire one.  It runs alot faster than my xp partition.
I love linux, ive already familiared myself with the commands.  Already even used aircrack-ng.

How  much lighter would xubuntu be compared to ubuntu?
There is certain things i cannot seem to use as there is also limited guides and resources for xubuntu.  It seems to be widely less used than ubuntu.
Ubuntu is fairly fast and although I've never played with Xubuntu I have used Kubuntu and I've found the regular Ubuntu to be much faster...

---

### Post by TheNosh on 2009-08-11
> **twiztid-kid said:**
> Okay, is that feasible with limited loss of performance to a fresh installation.

it shouldn't cause any loss in performance, you can have both desktop environments installed, but you'll only be running one at a time. so Xfce will be as fast as always, and gnome will be available as a choice on startup (under "session") so you can play around with it and see which one you preffer.

i should also mention that "ubuntu-desktop" is a meta-package that comes with several programs. i'm not sure if there's a simple way of installing gnome without that though.

---

### Post by zkriesse on 2009-08-11
> **TheNosh said:**
> it shouldn't cause any loss in performance, you can have both desktop environments installed, but you'll only be running one at a time. so Xfce will be as fast as always, and gnome will be available as a choice on startup (under "session") so you can play around with it and see which one you preffer.

i should also mention that "ubuntu-desktop" is a meta-package that comes with several programs. i'm not sure if there's a simple way of installing gnome without that though.
there isn't a way of installing ubuntu without having the startup apps and stuff. at least i don't think so...but they can be removed after the fact.

---

### Post by twiztid-kid on 2009-08-11
> **Zachk18 said:**
> there isn't a way of installing ubuntu without having the startup apps and stuff. at least i don't think so...but they can be removed after the fact.
 
 
Its cool man.
I'm burning Ubuntu 9.04 to a disk as we speak.
 
If it has sub optimal performance is still have my xubuntu disk to re-install.

---

### Post by TheNosh on 2009-08-11
> **twiztid-kid said:**
> Its cool man.
I'm burning Ubuntu 9.04 to a disk as we speak.
 
If it has sub optimal performance is still have my xubuntu disk to re-install.

i think be easier to just install a second desktop environment than reinstall your whole OS.

---

### Post by pewterbot9 on 2009-08-11
Qutoing from [http://en.wikipedia.org/wiki/Xubuntu:](http://en.wikipedia.org/wiki/Xubuntu:)

"Because the Xfce desktop environment uses fewer system resources than the default GNOME, Xubuntu is often used on older computers, systems with limited resources, laptops, netbooks and high-efficiency workstations."

---

### Post by Barafu Albino Cheetah on 2009-08-11
just install (ubuntu-flavor-you-want)-desktop package.  For example, edubuntu-desktop. It will switch you to another flavor, while keeping current too. You will have to select required session on login screen. If you use autologin then just log out and change the session. 
I have all three main dsktops installed - and no problem, except menu containig too many apps in KDE.

---

### Post by twiztid-kid on 2009-08-11
Okay so it would just be
sudo apt-get install ubuntu-desktop
 
How much extra space am i looking at taking up with this?
(i cannot get to my HDD atm)

---

### Post by zkriesse on 2009-08-11
It shouldn't be that much space...how big is your hard drive and ram? Use this command in your terminal and post results here....

df -h

and to check folders use and size use this command

du -h

---

### Post by twiztid-kid on 2009-08-11
Acer Aspire One - 1.6Ghz Atom, 512mb ram, 60Gb external drive (15gb for linux, rest as fat32 storage)
 
Ill post after my install.
I started again with xubuntu and installing the ubuntu environment.

---

### Post by zkriesse on 2009-08-11
Cool my man

---

### Post by slakkie on 2009-08-11
> **Zachk18 said:**
> there isn't a way of installing ubuntu without having the startup apps and stuff. at least i don't think so...but they can be removed after the fact.

That is called a cli install or server install. They don't provide any of the desktop shizzle. You can convert such installations to desktop installs in a minute by install *tu-desktop meta-packages.

---

### Post by twiztid-kid on 2009-08-11
> **Zachk18 said:**
> It shouldn't be that much space...how big is your hard drive and ram? Use this command in your terminal and post results here....

df -h

and to check folders use and size use this command

du -h



Okay, so i have got xubuntu 9.04 running the GNOME environment(ubuntu).
It runs a little slower but i have all the compiz effects enabled (which still wont work in xubuntu.

Also that command will not work.

---

### Post by TheNosh on 2009-08-11
> **twiztid-kid said:**
> i have all the compiz effects enabled (which still wont work in xubuntu.

```
compiz --replace
``` should do it. (it's kind of annoying to disable it afterwards though)

---

### Post by twiztid-kid on 2009-08-11
> **TheNosh said:**
> ```
compiz --replace
``` should do it. (it's kind of annoying to disable it afterwards though)


Thanks alot man.

Also i am trying to set desktop cube up but i can only seem to get it to rotate with 2 windows like a 2d sheet of paper.

---

### Post by TheNosh on 2009-08-11
> **twiztid-kid said:**
> Thanks alot man.

Also i am trying to set desktop cube up but i can only seem to get it to rotate with 2 windows like a 2d sheet of paper.

i seem to recall getting it to work some how, that was back in hardy though. (i haven't used Xfce much since then other than with Puppy where i wouldn't use desktop effects anyway) i may log in to Xfce later and see if i can figure it out. i have a few books to read and a few essays to write first though.

---

### Post by twiztid-kid on 2009-08-11
> **TheNosh said:**
> i seem to recall getting it to work some how, that was back in hardy though. (i haven't used Xfce much since then other than with Puppy where i wouldn't use desktop effects anyway) i may log in to Xfce later and see if i can figure it out. i have a few books to read and a few essays to write first though.

its the same with GNOME too.

---

### Post by TheNosh on 2009-08-11
> **twiztid-kid said:**
> its the same with GNOME too.

well i know in gnome you can just right click the "workspaces" panel applet and go to "preferences", then set it to "columns: 4" and "rows: 1"

then you'll have a cube

cheers

---

