---
title: "Faster and light"
date: 2010-05-30
forum: General Help
---

### Post by drakesg on 2010-05-30
Hi everybody

i use a 10 years old pc with an Amd Sempron 2400 (1667 Mhz) and 718 MB ram that appears a little too slow running Lucid.
Comparing it to my old XP install ubuntu seems heavier opening software and switching between the windows..  Ok, not really much, but I thought it needed less hardware requirements to run fine compared to what windows need.

Is there anything I can do to increase speed and make ubuntu light and faster without switching to xfce or similar?

Thank you.

Bye.

---

### Post by Ozymandias_117 on 2010-05-30
> **drakesg said:**
> Hi everybody

i use a 10 years old pc with an Amd Sempron 2400 (1667 Mhz) and 718 MB ram that appears a little too slow running Lucid.
Comparing it to my old XP install ubuntu seems heavier opening software and switching between the windows..  Ok, not really much, but I thought it needed less hardware requirements to run fine compared to what windows need.

It is, but Windows XP went to RTM in August of 2001, Ubuntu 10.04 came out in April of 2010. You can't really expect something almost 9 years newer (That's an eternity in computer years!) to run as fast as the older. If you want to compare 10.04 to Windows, it would need to be to Vista or 7. Despite this fact, Ubuntu 8.10 or so, which is still 7 years newer than Windows XP DID still run faster than XP. Also, if you put them both on newer hardware Ubuntu 10.04 will be faster, because it is more efficient with it's hardware usage.
Linux, is great because there there are versions designed to run on computers 15+ years old. It's called putting something like LXDE, or IceWM or Openbox on them.


> Is there anything I can do to increase speed and make ubuntu light and faster without switching to xfce or similar.

You could do a 10.04 Minimal install and only install exactly what you need.

---

### Post by bumanie on 2010-05-30
Lucid should run OK on those specs - as the the OP said, try xubuntu desktop instead > sudo apt-get install xubuntu-desktopYou will be able to choose which desktop environment to boot in to from the session menu at login screen

---

### Post by drakesg on 2010-05-30
thank you!

i installed xubuntu-desktop to give it a try.

At first sight it seems more reactive; good!

But now i can't find the COMPUTER menu in resources.. i used it to open my other internatl hard disk with the ntfs partition.
Where is it?

---

### Post by drakesg on 2010-05-31
Can anyone help me please?

---

### Post by Penguin Guy on 2010-05-31
> **drakesg said:**
> Is there anything I can do to increase speed and make ubuntu light and faster without switching to xfce or similar?
No.

---

### Post by drakesg on 2010-05-31
Ok, but do you have any suggestion for my new problem with xcfe?

---

### Post by cascade9 on 2010-05-31
drakesg- 10 years old? Nope, not possible. The Semperon 2400+ was a 2004 release. 

BTW, 718MB? Sounds like you have onboard video. You might find that with a video card, or with desktop effect turned off (if you have them on) ubuntu would be more responsive ;) 

> **Ozymandias_117 said:**
> It is, but Windows XP went to RTM in August of 2001, Ubuntu 10.04 came out in April of 2010. You can't really expect something almost 9 years newer (That's an eternity in computer years!) to run as fast as the older. If you want to compare 10.04 to Windows, it would need to be to Vista or 7. Despite this fact, Ubuntu 8.10 or so, which is still 7 years newer than Windows XP DID still run faster than XP. Also, if you put them both on newer hardware Ubuntu 10.04 will be faster, because it is more efficient with it's hardware usage.
Linux, is great because there there are versions designed to run on computers 15+ years old. It's called putting something like LXDE, or IceWM or Openbox on them.

For an 'everything including the kitchen sink' distro, agreed. But there are plently of new release 'non-light' distros out there that would be at least as fast as Windows XP. 

> **Ozymandias_117 said:**
> You could do a 10.04 Minimal install and only install exactly what you need.

+1. Minimal install makes a big difference IMO.

> **drakesg said:**
> Ok, but do you have any suggestion for my new problem with xcfe?

Try 'thunar'. It the Xfce file manager, and it should let you see your NTFS partition/drive. You might need to figure out where the drive is mounted though.

---

### Post by Penguin Guy on 2010-05-31
> **drakesg said:**
> Ok, but do you have any suggestion for my new problem with xcfe?
Sorry I've never used XFCE, so no, but it might help if you updated the first post with information about the new problem.

---

### Post by Joe-ubunt on 2010-05-31
> **drakesg said:**
> Hi everybody

i use a 10 years old pc with an Amd Sempron 2400 (1667 Mhz) and 718 MB ram that appears a little too slow running Lucid.
Comparing it to my old XP install ubuntu seems heavier opening software and switching between the windows..  Ok, not really much, but I thought it needed less hardware requirements to run fine compared to what windows need.

Is there anything I can do to increase speed and make ubuntu light and faster without switching to xfce or similar?

Thank you.

Bye.

Ubuntu 10.04 runs fine on my system with about the same specs as yours. I did have to change the color depth down to 16 though. 

You can change it by editing your xorg.conf file or by creating an xorg.conf file and adding a generic screen default section if yours is empty like mine. 

One way to check your color depth is by typing _xwininfo_ into a terminal and click on a page outside of the terminal. You'll notice a difference by changing the color depth from 24 to 16.

---

### Post by rizzeh on 2010-05-31
Ununtu can be heavy or light, depends how you set it up. I have Ubuntu on desktop with almost 1 gig of ram usage and ubuntu on old home file server with 60mb ram usage.
Turn off all desktop effects, look through start up programs to remove unneeded stuff will shave off a lot.
 
   If tinkering not for you, install Linux Mint distro [http://www.linuxmint.com/]("http://www.linuxmint.com/") 
I've spent less time setting up  Linux Mint laptop than i ever did with clean windows installs. Everything just worked out of the box on Vaio FN lappy

---

