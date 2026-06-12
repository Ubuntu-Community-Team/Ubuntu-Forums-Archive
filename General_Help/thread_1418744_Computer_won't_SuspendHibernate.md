---
title: "Computer won't Suspend/Hibernate"
date: 2010-03-01
forum: General Help
---

### Post by Brotherbrat13 on 2010-03-01
Before I start, Id like to point out that I have tried suspend on Ubuntu, Kubuntu, and Xubuntu and it works on none of them.

The problem is simple. My computer doesn't power down when going into suspend or Hibernate. My computer goes to a black screen with a blinking white _ in the top left corner, then my monitor goes to sleep but the computer stays on. If I try to take the computer of of suspend or hibernate, it doesn't respond and stays with the sleeping screen.

Anyone have a fix for this?

---

### Post by WubiNoob on 2010-03-01
If you are dual booting your computer, you cant sleep your computer. Only with a fresh install.

---

### Post by Gumbyy on 2010-03-01
> **Brotherbrat13 said:**
> Before I start, Id like to point out that I have tried suspend on Ubuntu, Kubuntu, and Xubuntu and it works on none of them.

The problem is simple. My computer doesn't power down when going into suspend or Hibernate. My computer goes to a black screen with a blinking white _ in the top left corner, then my monitor goes to sleep but the computer stays on. If I try to take the computer of of suspend or hibernate, it doesn't respond and stays with the sleeping screen.

Anyone have a fix for this?

   Is it a labtop? I have a Asus Eee PC and in my case I have my power settings set for hibernate when I close the lid to my labtop.Then to turn it back on I open the lid and hit enter and it boots right up.I have to put my password in.Go into power management and see what it says in there.

---

### Post by laceration on 2010-03-01
> Anyone have a fix for this?
Tuxonice does.  Ubuntugeek.com has a good tutorial for it.

---

### Post by drewsus on 2010-03-01
WubiNoob is not correct, fyi.


-Do you have an SD card inserted in your computer?

-Is your SWAP partition greater than 2x your system RAM?
[INDENT]when you installed Ubuntu did you partition your harddrive manually or did you let the installer do it for you?[/INDENT]

---

### Post by Brotherbrat13 on 2010-03-01
I don't have an SD card in it, and its a desktop. My swap is much less then my installed RAM. I have 3.5 Gigs (4 Total) of RAM, and my swap space says its only 243.7MB. I Manually partitioned my hard drive because I dual boot with windows 7, but I left 2 gigs for swap space.

I'll check out Ubuntugeek.com.

---

### Post by drewsus on 2010-03-01
if you want suspend/hibernate to work your swap space needs to be >= RAMx2

this is your problem

---

### Post by bcbc on 2010-03-01
Your swap has to be at least as big as your RAM. When you repartition your drive the UUID of the swap will change. It has to be updated in not only your /etc/fstab but also your /etc/initramfs-tools/conf.d/resume and after editing this you must run:
```
$ sudo update-initramfs -u
``` 

That's how I got hibernate to work on my machine (1GB RAM, 1GB swap).

---

### Post by Brotherbrat13 on 2010-03-01
Since the install is only a day old, I'll just re-install and change the amount of swap space.

Thanks for the help!

---

### Post by drewsus on 2010-03-01
I really dont know why this isnt mentioned when partitioning your hdds when installing ubuntu. it should be a warning or tool tip or something. and should be done automatically if you dont manually edit your partitions during install

---

### Post by Brotherbrat13 on 2010-03-03
Well, I gave myself 5 Gigs of Swap space, and no luck.. But its different now. Now when I press suspend.. The screen fades out.. the monitor turns off.. then a second or two later the screen pops back on. If I press suspend again, the computer crashes.

Any new suggestions? =l

---

