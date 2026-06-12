---
title: "newbie access problems"
date: 2009-10-07
forum: General Help
---

### Post by bloodyminded on 2009-10-07
I'm sure this has been answered, yet when I search I still cannot resolve my problem.

My friend lent me a Linux Computer running Umbuntu, and I was mainly using it for the internet. I just got my Windows XP computer back that had died and we wiped the hard drive clean. However, it was missing some driver files and would not access the internet, so my dad emailed them to me. I have to get these files from the Linux machine, which can access the internet, to the Windows computer, which can't.

NO PROBLEM! Or so I thought.

I have USB thumb drive, I was just going to put the files on there and be done. However, when I went to do that, I now no longer have access or permission to mount the USB drive. 

I probably made a mistake, I deleted some users to get rid of them, for when I get rid of the computer. Now, those administrative powers I had are gone. I used to be able to go to Users and Groups and make changes, now I can't.

I JUST NEED THESE FILES! I can't even burn a disc on this machine...

I have been looking up Sudo and things, it does nothing for me.

PLEASE ADVISE! I have been wasting hours on this issue.



[and to why I don't just ditch the windows XP computer all together - this is a SLOW, loud 2002 Dell running Linux, doesn't meet my needs at all]

---

### Post by bresdog on 2009-10-07
Install ubuntu on the laptop that has xp?

---

### Post by DeBOBAHer on 2009-10-07
Can you use the "restore" mode in loader? I think it could give you the possibility to run root shell where you can modify your user.

---

### Post by nothingspecial on 2009-10-07
Reboot and when the grub loading dialougue appears press escape and boot into the root shell prompt (or whatever its called)

Create a new user with admin powers

```
adduser bob admin
```

Log in as bob and you can administer at will.

Edit *** just found it - boot into recovery mode and select "Drop to root shell prompt" *** Edit

---

### Post by bloodyminded on 2009-10-07
THAT DIDN'T work.  Never thought moving 3 files to a thumb drive would take hours. Such is the Linux way I've learned.

I hit ESCAPE as it started up. 

I got these options:

Kernel 2.6 17-10 generic
Kernel 2.6 17-10 generic (recovery mode)
Memtest86+

HOWEVER, when I tried to scroll with the arrows or press any key at all, it was UNRESPONSIVE.

---

### Post by t0p on 2009-10-07
> **bloodyminded said:**
> THAT DIDN'T work.  Never thought moving 3 files to a thumb drive would take hours. Such is the Linux way I've learned.

I hit ESCAPE as it started up. 

I got these options:

Kernel 2.6 17-10 generic
Kernel 2.6 17-10 generic (recovery mode)
Memtest86+

HOWEVER, when I tried to scroll with the arrows or press any key at all, it was UNRESPONSIVE.

Don't blame Linux, Linux didn't tell you to delete users willy-nilly. Get your friend's  Ubuntu CD and start a live session. Mount the hard disk. Now you can transfer the files to your  USB drive.

---

### Post by DeBOBAHer on 2009-10-07
Also after mounting from liveCD you can chroot to you hard disk and adduser as on your system from hard disk.

---

### Post by bloodyminded on 2009-10-07
My friend lives 40 miles away and doesn't have the disc. This insanely stupid. I guess now I have to call up and beg some friends "can I come over and get a file off of your PC?" I just moved to a new city and don't know many people. Linux is NOT WORKING for me. I just want these THREE FILES. Not a big deal.

None of your suggestions work for me. How about a plan D, E, F, G?

---

### Post by bloodyminded on 2009-10-07
Another way Ubuntu is costing me money and preventing me from getting crucial things done..... I have my printer hooked up, it acknowledges it, knows the name of the printer, but WILL NOT PRINT A SINGLE PAGE. I put in my disc for the computer, nothing happens because Ubuntu/Linux doesn't run .exes So here I do my part to do ANOTHER VERY SIMPLE, BASIC thing like..... PRINT A PIECE OF PAPER, and ubuntu FAILS. Everything is an ordeal with this operating system. I can't wait to get it out of my life. I don't want to learn how to do all these little things. NO. I just want these three files and then to be done with it. Guess my best option is to go out of my way, pay money at a internet cafe, and get the files off there. What a waste.

---

### Post by oboedad55 on 2009-10-07
> **bloodyminded said:**
> Another way Ubuntu is costing me money and preventing me from getting crucial things done..... I have my printer hooked up, it acknowledges it, knows the name of the printer, but WILL NOT PRINT A SINGLE PAGE. I put in my disc for the computer, nothing happens because Ubuntu/Linux doesn't run .exes So here I do my part to do ANOTHER VERY SIMPLE, BASIC thing like..... PRINT A PIECE OF PAPER, and ubuntu FAILS. Everything is an ordeal with this operating system. I can't wait to get it out of my life. I don't want to learn how to do all these little things. NO. I just want these three files and then to be done with it. Guess my best option is to go out of my way, pay money at a internet cafe, and get the files off there. What a waste.

Tell us which printer you have so you can get more help.

---

### Post by bloodyminded on 2009-10-07
It's an HP Laserjet 1020

---

### Post by bloodyminded on 2009-10-07
Also, now no audio can be played. It's permanently - not on mute but somehow the sound card is gone or I can't control it or anything. How useless. 

ALSO I forgot - this computer never could play MP3s.... the software to do so is loaded, but I spent an hour trying to get it to work, never happened. Can't wait to just ******* CLICK on something and have it open, work, function, complete. I've wasted so many hours of my life on LINUX.

---

### Post by oboedad55 on 2009-10-07
> **bloodyminded said:**
> Also, now no audio can be played. It's permanently - not on mute but somehow the sound card is gone or I can't control it or anything. How useless. 

ALSO I forgot - this computer never could play MP3s.... the software to do so is loaded, but I spent an hour trying to get it to work, never happened. Can't wait to just ******* CLICK on something and have it open, work, function, complete. I've wasted so many hours of my life on LINUX.

I did a google search for your printer and Ubuntu and came up with a number of hits.

---

