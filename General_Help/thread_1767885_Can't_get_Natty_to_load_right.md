---
title: "Can't get Natty to load right"
date: 2011-05-26
forum: General Help
---

### Post by petefan12 on 2011-05-26
I upgraded to Natty Narwhal about a week after it was released and haven't had any problems until last night. The screen froze so I had to use the power button to turn my laptop off and now I cant get it to load. I have tried the safe mode and regular startup. Please forgive my terminology mistakes. I put a hard drive with Windows 7 loaded in my laptop so I could start this thread and feel it could crash at any time. It says failure is imminent, so I'm on borrowed time. Natty is installed on my hard drive that is sitting beside me right now. So any troubleshooting will require me to switch hard drives around.

Anyway, when I tried to get Natty to load the hard drive light basically stays on, Unity desktop won't load, and the Gnome desktop sorta loads. I wish I had the error messages written down so this may be a waste of time. I'm getting messages that different applets cant load, such as the workplace switcher, clock applet, and a couple more that I can't remember right off. The home screen doesn't show the trash can, workplace windows, time, or the button to shut down, restart, etc. Nothing will load. The hard drive light runs constantly

Also, on two occasions when I tried to load, the ubuntu screen with the four little dots below the word that scroll left to right, said the hard drive couldnt be found or was not ready. it gave me the option to continue manually, continue, or skip.

I apologize for my idiotic ramble without proper terminology and hope some of this makes sense. Is my hard drive shot? Any way to check that?

---

### Post by TeoBigusGeekus on 2011-05-26
Boot up with a live cd/usb and try to scan for errors on your partitions and correct them.
```
sudo fsck /dev/sda1
```
Continue with sda2, etc.
To find out which are your partitions
```
sudo fdisk -l
```
(-L)

---

