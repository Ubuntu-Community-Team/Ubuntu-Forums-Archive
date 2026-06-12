---
title: "Windows did something to my Kubuntu, now my comp shuts down."
date: 2006-03-03
forum: General Help
---

### Post by chapin on 2006-03-03
Okay. I am terribly sorry. Someone probably already asked this, but I swear I read a lot of threads and found nothing similar to my problem. So here I am, asking if anyone can solve this. I also apologize for not knowing the exact terms used to describe all the different things.
I installed Kubuntu breezy (dual boot with Windows XP) and all the installation process was successful. It gave me only one good run though. I looked around my new Kubuntu Linux for a while, and was quite amazed by all the cool things. I rebooted and went on to try if my Windows still worked. A screen appeared that said that it just needed to check the disc, or something. It did, and rebooted automatically, so I chose windows on the grub screen and Windows loaded without a hassle. I was so proud of my Kubuntu experience. I said to myself. Ok, big dinosaur works, let's go back to Kubuntu. Everything went okay. In the session login screen I typed what I had to type and hit enter. It starts loading, two icons appear underneath the login screen, "loading peripherals" or something like that, and then the laptop just shuts down. Booting failsafe works fine, but I don't know anything about linux or what to type. Some menus are available with the kde graphic interphase, but nothing I can modify to get it running again. Booting "recovery mode" takes me to a gray screen, and I have to pull out the chord and the battery to be able to reboot. Windows did something to it, I know it. Help me please.

---

### Post by R3linquish3r on 2006-03-03
I've had somewhat of the same experience, but what happened to me was windows overwrote the GRUB MBR and I had to re-install grub. Is windows sitting on the same hard drive as linux?

---

### Post by nalmeth on 2006-03-03
Crazy.. 
Don't worry about not knowing the correct terms and stuff.. Half the people here don't either :D 
Is there any output from kubuntu when failing to boot up? Any error windows or output of any kind?
Failsafe terminal mode will be helpful, but if you get to KDM (the login manager) you can hit cntrl-alt-F1 to go to a terminal screen, and then cntrl-alt-F7 to return to the Xserver, the graphical interface.
Once we know more about what happened you'll work from there..
Great job hooking up kubuntu though, hopefully you'll get this sorted out

---

### Post by chapin on 2006-03-03
It is sitting on the same hard drive, but the grub seems to be working fine. Although I'm not sure what a MBR is. And windows works just fine, and it does get to the KDM thing, so I think the problem lies past that stage. Thank you for your quick response.

---

### Post by chapin on 2006-03-03
Well, there's no output. It's loading the little icons  and once it gets to the "peripherals" bit it seems as though someone just yanked the chord out and it shuts down. Failsafe mode boots up with no problem and it doesn't even look bad (you know, bad resolution, funny menu displays or anything);just that the programs aren't at hand. But no "Kernel Panic" thing or anything, as did happen with a Debian distribution that never worked. I am happy to let you know that I am typing this from my other old Pentium II computer, which I brought back to life with Ubuntu breezy badger (no dual boot there). Linux systems are fun.

---

