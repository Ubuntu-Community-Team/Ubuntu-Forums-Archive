---
title: "I briefly used 11.04 and now 10.04 has disappeared"
date: 2011-05-24
forum: General Help
---

### Post by oopsie on 2011-05-24
Long story. I'll try to keep it brief. There's a TL;DR at the bottom

I have three hard drives.

On my 27GB HD, I mess about, install various distros and OSes. Before today I had fedora on it, but it doesn't matter

On my 76GB HD, I had Ubuntu 10.04, which I use most of the time.

On my 250GB HD I have Ubuntu 11.04

I usually use 10.04 because the graphics drivers on 11.04 don't work for me. I wanted to play a windows game, but couldn't get it working on Wine 1.2 on Ubuntu 10.04. I remembered I had Wine 1.3 on my Ubuntu 11.04, so I booted that OS.

It had been a month since I last used 11.04, so there were 180MB of updates which I installed. Then I tried my windows game in Wine. I still couldn't get it to work, so I gave up and rebooted my PC so I could go back to my main OS, Ubuntu 10.04.

But I couldn't. Apparently something I did above was enough to mess up GRUB, and it wouldn't boot any OS. I think it couldn't find my hard drives or something. GRUB just stopped working.

I read a few guides about reinstalling GRUB from the liveCD, but I couldn't understand them. So I thought I'd just install Ubuntu 10.04 on my 27GB hard drive, which then should install GRUB along with it and automatically find my other OSes, Ubuntu 10.04 on my 76GB HD and Ubuntu 11.04 on my 250GB.

I did this, and GRUB now works, but for some reason it can only see Ubuntu 10.04 which I just installed on my 27GB HD and Ubuntu 11.04 on my 250GB HD, and not Ubuntu 10.04 on my 76GB HD, which is my main OS!

Does anybody know why and how I can fix this?
[U][B]
TL;DR[/B][/U] I have three hard drives. Ubuntu 10.04 on my 27GB HD and my 76GB HD, and Ubuntu 11.04 on my 250GB hard drive. For some reason GRUB can only see Ubuntu 10.04 on my 27GB HD and not my 76GB hard drive. Does anyone know how I can fix this?

---

### Post by searchfgold6789 on 2011-05-24
Here are some instructions for you that will probably help:

[LIST=1]
[*]Make a 11.04 Live CD and boot from it.
[*]Enter into a terminal window.
[*]Type:
[/LIST]
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```That will install the latest version of grub onto your first hard disk {/dev/sda} and it will detect your 11.04 installation.
If not, post back and we'll help you add an entry for it in your GRUB config.

---

### Post by oopsie on 2011-05-25
Didn't work. Grub can still only see two of my three operating systems.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Try 

sudo os-prober
sudo update-grub

---

### Post by oopsie on 2011-05-25
Didn't work. It only sees two of my three OSes

---

### Post by oopsie on 2011-05-25
I've just found out some information that's probably relevant. 

GParted says the partition with the missing OS's root on is an "unknown filesystem", and if I click information it says "Unable to detect filesystem!"

---

