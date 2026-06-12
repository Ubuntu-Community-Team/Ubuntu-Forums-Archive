---
title: "Unlock Login Keyring Freeze"
date: 2010-05-02
forum: General Help
---

### Post by Kethari on 2010-05-02
Im unable to login to my computer because directly on startup the "unlock login keyring" pops up, i can move my mouse around but cant click anything or type/use commands. 

The loading also takes longer then usual.  This is in lucid 64bit.  I installed gnome-do the night before so i think it has something to do with that, but i really dont know what to do.  I tried going into terminal (alt-f2), or killing the process with ctrl-alt-esc but they keyboard is useless (though not entirely frozen as i can turn on/off numlock etc)

Is there someway i can bypass this temporarily and then get rid of it (from bug reports ive read it seems deleting gnome-do will work)

Any help would be amazing.

Thanks!

---

### Post by dino99 on 2010-05-02
hey, if nothing can be done with keyboard, there is no much way to explore.

try to boot and hold "esc" key down at the same time or with esc+alt or ctrl

same problem with recovery mode ?

have you multi-boot on that system ?

---

### Post by garvinrick4 on 2010-05-02
Can you boot up a Live Cd and mount the partition that gnome-do is on and delete gnome-do.

If you do not know how to chroot into your / let me no. Leave your sudo blkid (small L second letter) for me to look at and tell me which sda# is the one if you have more than one install.

---

### Post by Kethari on 2010-05-02
Ah thanks a bunch man! You just saved me. I deleted gnome-do in root shell through recovery mode and now everything boots like normal.  Esc, alt-esc, and ctrl did nothing, but just using shift to get into recovery worked.

Thanks again!!

---

### Post by odelay on 2010-07-19
I have/had this same issue, and it's definitely related to Gnome-Do.  Very surprised I haven't read more about it.

[https://bugs.launchpad.net/do/+bug/596772](https://bugs.launchpad.net/do/+bug/596772)

---

### Post by scotiangold on 2010-07-23
I have the same issue and am very happy to have found this thread.

Perhaps Gnome -Do should be called Gnome - S$%t :)

How does this conflict make it to daylight?

---

### Post by pclausen on 2010-07-28
Had the kind of the same problem, but it took a while finding out that it was caused by gnome-do. 

I was trying to remote connect with NX (nomachine). It had been working *before* I installed gnome-do. Now, gnome-keyring wanted a password from me which I could not enter because X (kde and gnome) totally froze.  

Fix: 
* ssh to machine
* sudo apt-get remove gnome-do

---

### Post by zerothis on 2011-08-22
Cain, Able, and Seth!
Ctrl+Alt+F1 puts you in virtual terminal where you can log in with user name and password then
sudo killall -9 gnome-do
Ctrl+Alt+F7 (or, F8-F12 depending on the number of users logged into desktop)
Back in GUI, uninstall gnome-do, or enter you keyring password and run gnome-do again (it will work fine until you login to GUI again). AND/OR, run startup applications in gnome do and uncheck it.

---

### Post by kingfisher_ph on 2011-09-20
I have the same problem! The only way i can do is using safe mode T__T!! OMG! It's sooooo bad!

---

### Post by kswenson on 2011-10-17
I have the same problem but gnome-do is not installed!
If I give the keyring manager my password then everything functions normally...
  otherwise, compiz/X doesn't work properly!

---

