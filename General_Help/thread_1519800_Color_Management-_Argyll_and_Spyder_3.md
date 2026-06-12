---
title: "Color Management- Argyll and Spyder 3"
date: 2010-06-28
forum: General Help
---

### Post by blur xc on 2010-06-28
I finally found out that I can use my Spyder 3 colorimeter in Ubuntu using the Argyll package.

So, I ran it successfully, and created defaultdisplay.cal and a defaultdisplay.icc files.  Now what do I do with them?  How do I apply them?

BM

---

### Post by j.daniel on 2010-08-30
```
dispwin -I /your/profile/here.icc
```

---

### Post by blur xc on 2010-08-31
thanks...  i got that figured, but I still can't make it load on bootup.  I' tried the .xsession file in my home directory, but it didn't work.  right now I have a panel launcher setup to run a script in my home folder to apply the icc profile.  It would be nice if it happend right when the xserver started, before even any users log in.

Thansk,
BM

---

### Post by j.daniel on 2010-08-31
Have read somewhere that you should be able to create an "event" in Gnome that applies this. Ought to be the same as adding a "Startup Application" (under System->Preferences). You can add a command line there to launch dispwin with your profile.

I believe that this is after the login screen though.

Cheers!
/ Daniel

---

### Post by Snoreis on 2011-05-27
I know this thread is kinda old, but how did you finally get your Spyder 3 to work in Argyll/dispcal.  I've been trying for some time and while the instrument pops up in the GUI, I never can get it to properly access the device for testing,

Thanks

---

### Post by rulorojo on 2011-10-07
I think many of us (new ubuntu users) would appreciate very much a synthetic description on how to get the Spyder 3 working

---

### Post by dargaud on 2012-04-14
> **rulorojo said:**
> i think many of us (new ubuntu users) would appreciate very much a synthetic description on how to get the spyder 3 working

bump!

---

### Post by dargaud on 2012-04-14
A bit more background: after installing /usr/bin/spyd2PLD.bin and removing libmtp-runtime, I'm trying to run dispcal without success:
```
$ dispcal -v -q l -y c samsung
Setting up the instrument
dispcal: Error - Configuring USB port 'usb:/bus5/dev86/ (Datacolor Spyder3)' to 1 failed with -6 (Resource busy)

$ lsusb | grep -i color
Bus 005 Device 086: ID 085c:0300 ColorVision, Inc. 

$ ll /dev/bus/usb/005/086 
crwxrwxrwx+ 1 root root 189, 597 2012-04-14 16:55 /dev/bus/usb/005/086

$ lsof /dev/bus/usb/005/086 

```
Why is it busy if nothing's using it ?

Correction: VirtualBox was grabbing it (from an old configuration). As to why it didn't show with lsof, it's apparently better to use $ sudo lsof | grep ...

---

