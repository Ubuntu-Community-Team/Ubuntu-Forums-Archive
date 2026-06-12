---
title: "Duel Boot TROUBLE.  XP Pro with Ubuntu 5.10."
date: 2006-02-06
forum: General Help
---

### Post by ubuntuforums on 2006-02-06
Hey guys. I just downloaded the i386 ISO for Ubuntu 5.10 and I want to make it duel boot on my XP Professional system. Anyway I figured it would be easy, so I opened up Partition Magic, resized my XP partition and put aside 10gb for Ubuntu. I poped in my burnt cd with the iso of ubuntu 5.10 and restarted my computer. Then the computer automatically booted to CD and I chose my language, keyboard setup, and I let it automatically partition the free space. Then I let it install, after a minute or two the screen turned red and I got an error, so I clicked continue to try again, this time the screen turned read again and gave me the selection of three kernals, something like,, ubuntu i386, ubuntu image i386, and ubuntu image 2.1 something... So I chose the first kernal and it gave me an error after just a little bit, so then I did it over again,, and so on till I tried all three kernals, still got an error.

So I said whatever, restarted my computer and removed the cd. Then it checks for boot record from CD drive, then the the IDE hardrive, after the hard drive it says "...OK" then nothing, so I started to set up windows on the partition I made for Ubuntu, but when it restarted it showed BOTH OSes so I selected my old one and i booted right in. So its fine now I guess, but I dont know why Ubuntu wouldn't installl... Please help, thank you...

Specs for the sysytem im installing ubuntu on...
Intel Celeron 1.7GHz
768MBs of ram
Radeon 9600XT 256DDR
SoundBlaster Live! 24-bit 7.1
300W PSU...
40GB Maxtor hard disk driver...
LG 12x 8x 32x Recordable/Rewritable disk drive...

i think thats it for that system,,,

All help/comments are appreciated,, THANKS... I want to install Ubuntu asap.

---

### Post by ockertom on 2006-02-06
when you partitioned it did you choose to format it to receive a linux system?

---

### Post by RaiSuli on 2006-02-06
Try burning the install cd at a low speed. I ran into some weird problems when installing Ubuntu because the cd was faulty. Everything worked fine after burning it at 4x.

---

### Post by ubuntuforums on 2006-02-06
@ockertom.  I used partition magic to be sure I wouldn't lose my Windows partition, then I just deleted the partition and had ubuntu set up with the free space...  

@RaiSuli.  Okay thanks.  If no one comes up with anything else I'll try this out, hopefully it will fix my problem.  :)

---

### Post by ahh_dee on 2006-02-06
make sure that you dont create a file system with partition magic and make sure that windows is the first hard drive partition.

---

### Post by wilsonisme on 2006-02-06
from my md5 check woes, I have come to the conclusion that using bittorrent to download the .iso's ALWAYS works better then the alternatives. I too was having all sortes of problems until someone suggested I download the iso with bittorrent, check it with md5 before burning. I did, it checked out, and now im having no problems at all \\:D/

---

### Post by ubuntuforums on 2006-02-06
@ahh_dee.  I know, I just resized the partition to make room for it.  Then I used the freespace and had Ubuntu do it automatically...

I downloaded the ISO from here:
[http://gulus.usherbrooke.ca/pub/distro/ubuntu/iso/5.10/ubuntu-5.10-install-i386.iso](http://gulus.usherbrooke.ca/pub/distro/ubuntu/iso/5.10/ubuntu-5.10-install-i386.iso)

And I checked my md5, but I need the code to compare it to, I'll go and look with google i guess..  Anyone else have any ideas/suggestions...

---

### Post by wilsonisme on 2006-02-06
Form here: [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/)
you will see a MD5 text file: [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS)

It depends on where you got the download from, so be sure you are not looking at a md5 from a different place. Also use bittorrent man so much greater chance of not getting a corrupt download

There is a .torrent on that same mirror, here:
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-install-i386.iso.torrent](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-install-i386.iso.torrent)

---

