---
title: "Bricked"
date: 2010-03-08
forum: General Help
---

### Post by LinuxFree on 2010-03-08
I was downloading a new OS on my computer, it was going to be a dual boot, and then my computer froze. When I restarted my computer I couldn't boot my old OS or install the new OS. When I go to recovery mode I don't know what to do, it says to either enter the root password or press ctrl+d to skip the recovery. How do I enter the root pass? Just entering the pass by itself makes it says 'bash: no job control in this shell'

---

### Post by hansdown on 2010-03-08
Hi LinuxFree.

Was the new OS apple?

---

### Post by LinuxFree on 2010-03-08
The old and new ones are Linux Mint. I wanted to upgrade to Mint 8.

---

### Post by rogue_0111 on 2010-03-08
You may need to boot to the live CD and recover files from your original OS and reformat. 

Or try:

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-8.04-will-not-go-to-login-screen-657755/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-8.04-will-not-go-to-login-screen-657755/)

or

[http://www.linuxforums.org/forum/installation/108610-damaged-ubuntu-installation.html](http://www.linuxforums.org/forum/installation/108610-damaged-ubuntu-installation.html)

or

[http://ubuntuforums.org/showthread.php?t=359691](http://ubuntuforums.org/showthread.php?t=359691)

or

[http://groups.google.com/group/linux.debian.user/browse_thread/thread/5ea5e8c59cce0ad7/1349f9481b6aa21e?lnk=raot](http://groups.google.com/group/linux.debian.user/browse_thread/thread/5ea5e8c59cce0ad7/1349f9481b6aa21e?lnk=raot)


good luck

---

### Post by sandyd on 2010-03-08
> **LinuxFree said:**
> I was downloading a new OS on my computer, it was going to be a dual boot, and then my computer froze. When I restarted my computer I couldn't boot my old OS or install the new OS. When I go to recovery mode I don't know what to do, it says to either enter the root password or press ctrl+d to skip the recovery. How do I enter the root pass? Just entering the pass by itself makes it says 'bash: no job control in this shell'

try booting to livecd then

//replace /dev/sdax with your linux partition. you can do this by running "sudo fdisk -l"
```

sudo fsck -y /dev/sdax
```

---

### Post by LinuxFree on 2010-03-08
I'm going to try to install xubuntu then take all my stuff from my old partition and transfer it to xubuntu then make it half xubuntu and half mint 8 then I'll decide which OS to stick with from there.

---

### Post by LinuxFree on 2010-03-08
damn, I can't access any of my files, I screwed up my computer good. I'm going to have to write over my old OS and precious smut T_T

---

### Post by hansdown on 2010-03-08
I hope it goes well LinuxFree.

---

### Post by LinuxFree on 2010-03-08
I lost many gigs of precious music, I think I'm going to cr-

Wait, I'm crying

TT_TT

BAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAW!

---

### Post by hansdown on 2010-03-08
Ouch. Sorry buddy.

Ummm... probably not the best time to preach the benefits of multiple backups, so I'll just keep quiet.

---

### Post by Rasa1111 on 2010-03-08
Ouch for sure. 
my music is the one thing i would flip if i lost. 
it stays on the external for that reason. lol

Sorry you got "bricked" bro. 
I feel for you. <3

---

