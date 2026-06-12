---
title: "Vbox, Xp64 Host, Ubuntu Guest - reboots machine !"
date: 2010-07-21
forum: General Help
---

### Post by Envomni on 2010-07-21
I'm new to trying Ubuntu. Read the manual for it, and for Vbox before even starting. I'm not the type to jump in blind. 
 
XP Pro 64bit with -all- patches/updates in place
Vbox v 3.2.6 
Ubuntu 10.04
 
XP 64 is the host. 
Downloaded the iso for Ubuntu
Guest space is setup with 512ram, 12gb HD, 12mb video (basically the vbox recommended settings, but I gave it more fixed HD space than suggested).
 
As Ubuntu begins to launch as a guest, just before it reaches the desktop screen of Ubuntu, my whole machine reboots. No error messages, no blue screen, just flat out reboots. 
 
I've tried disabling the USB pad for PS2 mode management of the mouse. Increasing guest ram to 1024. Problem remains - whole machine reboots just before reaching Ubuntu desktop/setup prompts. 
 
Anyone else run into this? I'd really like to begin my takeover of the planet with Ubuntu while I'm on vacation time here...

---

### Post by Jazzy_Jeff on 2010-07-21
Since Windows is your host system, I would have to say the problem is on that end. I have not run Windows since XP so I am not sure what to check. I have never used the 64bit version. Hopefully someone else will be able to help.

---

### Post by Envomni on 2010-07-22
Also tried boosting video ram setting in Vbox to 32mb. Same problem persists.. entire machine crashes/reboots just as the nice spacey-background appears for Ubuntu / before any config options for initial install are presented.

---

### Post by Envomni on 2010-07-22
GOT IT TO BOOT.. 
 
Each reboot, it just went through a clean reboot.. no Blue Screen or anything. But then, this last time, it mysteriously DID present a blue screen with an error about ks.sys and "system_service_exception". 
 
I remembered seeing a report in my searches about someone who also had this error here
[http://www.virtualbox.org/ticket/6542](http://www.virtualbox.org/ticket/6542)
 
So I disabled the audio entirely for the guest in Vbox, and Ubuntu is installing right now.

---

### Post by Envomni on 2010-08-05
In further follow-up to this, the lack of ability to use Audio in the Ubuntu guest is now a bother to me. I want my sound. But enabling the Audio in VM Box for the Ubuntu Guest and using the Sound Blaster 16 mode gives nothing.. no sound. If I enable the other audio option, Intel, the whole computer crashes/reboots. 
 
Has anyone found any success with getting working Audio in an Ubuntu Guest under Windows ?

---

