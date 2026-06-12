---
title: "urgent! slim login manager preventing (work) computer from booting to login screen :("
date: 2011-08-04
forum: General Help
---

### Post by fertileneutrino on 2011-08-04
hey guys,

yesterday i installed slim login manager on my computer (eee pc 1018p, ubuntu 11.04), and now it cannot get passed the ubuntu loading screen (with orange dots underneath) when booting. i tried booting into recovery mode and that didn't work either. i also left the computer trying to boot overnight and that didn't work. 

basically, during this loading screen that should eventually bring you to the login screen, i can alt+tab to see the progress of the load. the progress is stuck on 

Starting X display manager: slim
 *Stopping System V runlevel compatibility
 *Stopping cold plug devices
 *Stopping log initial device creation
 *Starting enable remaining boot-time encrypted block devices
 *Starting configure network device security
 *Starting CUPS printing spooler/server
 *Stopping eneable remianing boot-time encrypted block devices
 *Stopping Mount filesystems on boot

Is there anything I can do from grub to remove slim?

or, is there any way I can access my ubuntu partition and save all my files?

Thanks!!

fertileneutrino

---

### Post by matt_symes on 2011-08-04
Hi

Did you have an encrypted home folder ? If you did this may be your problem.

Kind regards

---

### Post by fertileneutrino on 2011-08-04
i did have an encrypted home folder.

edit: what do i do?

---

### Post by fertileneutrino on 2011-08-04
nevermind. i found some stuff online that helped. thanks!

---

### Post by matt_symes on 2011-08-04
Hi

An encrypted folder; that explains alot. 

Have a look at this from Bodhi.

[http://bodhizazen.net/Tutorials/Ecryptfs/#Live](http://bodhizazen.net/Tutorials/Ecryptfs/#Live)

EDIT:

Can you post a link to what you found online to help others ?

Kind regards

---

### Post by fertileneutrino on 2011-08-04
i was frantically reading on the internet and i became prompted to try and boot into a previous linux version, recovery mode. this worked. but then I couldn't connect to the internet in that version of linux (not detecting an address for wireless or ethernet), and i stupidly typed

sudo killall slim

which threw me out of the session and brought me back to the dialogue that happens under the ubuntu loading screen (see first post). 

i am now going to try what you suggested.

---

### Post by kerryhall on 2011-08-05
I am having the same problem. My home directory is encrypted, and I want to use slim rather than gdm. Tried installing slim and it hangs on boot. (dots) 
I managed to get back to gdm, but I want to use slim instead. How do I set it up properly? Is this filed as a bug yet?

Thanks!

---

### Post by fertileneutrino on 2011-08-08
> **kerryhall said:**
> I am having the same problem. My home directory is encrypted, and I want to use slim rather than gdm. Tried installing slim and it hangs on boot. (dots) 
I managed to get back to gdm, but I want to use slim instead. How do I set it up properly? Is this filed as a bug yet?

Thanks!

hey. just updating you on my situation, which will bump the thread in the process. 

it would be useful to see if anyone else got this working with a non-encrypted home folder...but I am not sure this is the problem.

slim WAS working in an older version of linux, recovery mode, but not consistently. as in, from the boot menu I would go into "older versions of linux" and then the recovery mode. 

i am thinking that maybe it's just not compatible with 11.04...i read somewhere that 11.04 has inherently disabled GDM customization, so maybe that has something to do with it.

---

### Post by alberto666 on 2011-10-15
I am having a very similar problem, but after "trying to" update to Ubuntu 11.10 from 11.04.

It starts booting, and when it seems to be going to finish, it says two thing and:
"stopping mount filesystems on boot" [OK], and hangs.

Any help???

---

