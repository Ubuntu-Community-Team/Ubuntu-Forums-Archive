---
title: "Live CD....10.04"
date: 2010-05-01
forum: General Help
---

### Post by pcura on 2010-05-01
Hello All,

Has anybody encountered any issues regarding the Live CD of Kubuntu? I'm just trying to do a live CD of Kubuntu and its not boorting up.....right now I'm still at the logo of Kubuntu with the dots moving verrrrrrry slowly. Is it me or its the LiveCD is the issue?

Already tried my computer with intel centrino, as well as dual core processor......nothing is happening? Any inputs on this is much appreciated.


Thanks in advance

---

### Post by Rubi1200 on 2010-05-01
Hi,
I am having the same issues with both the new versions of Ubuntu and Kubuntu 10.4 LiveCD's. I have tried downloading from other mirrors, burning with different programs, brand new blank CD's and NOTHING; it gets to a certain point and then either the screen goes blank or it hangs and I have to do a hard shutdown. 
I am beginning to suspect that either the ISO images are somehow corrupted or, and this worries me more, the new version no longer recognizes older hardware (my laptop is 7 years old).
I have had no such issues with Karmic or other LiveCD's.

---

### Post by pcura on 2010-05-03
I tried both (9.10 and 10.04). they don't work at all. I tried different disto over the weekend so far there is one that I really like. 

PM me if you want to know what distro I'm referring to.......the only different though is that kubuntu, i believe uses ext4 but per ubuntu's forum there are some bugs that needs fixing.

 [FONT=Arial][SIZE=3][COLOR=black][http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)[/COLOR][/SIZE][/FONT]



[FONT=Arial][SIZE=3][COLOR=black][/COLOR][/SIZE][/FONT]

---

### Post by hxcobd on 2010-05-13
Bump because I've burned a Xubuntu and 2 Kubuntu discs now, and none of them will boot properly...

All of them get to the "intro" screen with the "Try distro from disc" and "Install distro" options, and after hitting enter, just sit there until I hard reboot...

---

### Post by hxcobd on 2010-05-13
Moved into Windows to try out trusty ol' ImgBurn...

Kubuntu CD failed again, this time ImgBurn is telling me the unreadable sectors are in the libc6 .deb file that's on the CD.

Burning a Xubuntu right now, but I suspect the same thing will happen...

I'm curious as to how people are using these images? I used different mirrors/sources for 3 different ISOs.

---

### Post by colorlessprism on 2010-05-13
this may not be the answer for you, but ive noticed lately people's md5's have  not been matching up, this can  cause any number of errors from install to boot failures. i had to  download 10.04 three times before the  checksums matched. if your using  XP (or any other windows operating  system) you need to use a  special  program,[  winMD5Sum]("http://www.nullriver.com/products/winmd5sum") is open source and calculates the MD5   checksum of a file or an ISO image.
   if your using linux you should be able to open a terminal and go to the correct directory.  to check a downloaded  iso file: 
 
[I]cd /your/download/directory
 md5sum <your file name should be here.iso>[/I]
 
 it should print something like this:
 *712277c7868ab374c4d3c73cff1d95cb ubuntu-10.04-netbook-i386.iso*

if  you have verified its hash  you might try booting from the CD and  test its  integrity.

md5 is one of the most common signature  to make sure that a  file that  you have downloaded is not corrupt. once  you have downloaded the the  ISO, use winMd5Sum/md5sum to get the checksum of the file on your  computer.  then  make sure that the checksums match. if they do, then your file is   exactly the same on your computer as it was/is on the server. tt is a   very good idea to  run an md5 hash  comparison check when you have a  file like an operating  system install  CD that has to be 100% correct.

Compare the result your computer made with the corresponding hash:
[http://releases.ubuntu.com/10.04/MD5SUMS:](http://releases.ubuntu.com/10.04/MD5SUMS:)
a54366aa72d6b576ee8fc0215f8a13b9 *ubuntu-10.04-alternate-amd64.iso
5b2dadacfd692b4f2d5c7cf034539262 *ubuntu-10.04-alternate-i386.iso
3e0f72becd63cad79bf784ac2b34b448 *ubuntu-10.04-desktop-amd64.iso
d044a2a0c8103fc3e5b7e18b0f7de1c8 *ubuntu-10.04-desktop-i386.iso
0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso
8ee25c78f4c66610b6872a05ee9ad81b *ubuntu-10.04-server-amd64.iso
15342636441181f7a19c65984b44e24c *ubuntu-10.04-server-i386.iso
e81f931b1de017520f6d4aa4f78c5c8b *wubi.exe

---

### Post by hxcobd on 2010-05-13
Hey color,

Thanks for the reply. Yeah, that's sort of the conclusion I've come to as well; running into posts all over the internet about corrupt ISOs, invalid MD5s, and the like.

I did end up booting into Windows and burning the Xubuntu CD, and that worked properly using ImgBurn. No idea why it didn't work in linux; I'm assuming just bad burns, as my CD burner tends to default to higher speeds in Brasero and K3b for some reason.

I'm currently in the process of downloading ANOTHER Kubuntu ISO, this time from kernel.org, so hopefully it will be legit.

Weird!

---

### Post by JC Cheloven on 2010-05-13
Downloading by bittorrent has the advantage for you that the checksum is done automatically. And it's quite fast, as ubuntu images are well seeded.
Also it benefits the ubuntu servers, by reducing its load.

Please see here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

---

### Post by hxcobd on 2010-05-13
I'll give the torrent a try, thanks JC.

The ISO from kernel.org was corrupt as well. This time it gave me the sector containing the linux kernel header.

I'm starting to go insane here... I just want a working Kubuntu disc!!!

---

### Post by hxcobd on 2010-05-13
Another failed Kubuntu disc, this time the error in the GCC package...

This is getting ridiculous... This torrent is my last hope

---

### Post by hxcobd on 2010-05-13
Torrent ISO failed as well... Error in the GCC folder again...

I'm seriously going insane over here... What could I possibly be doing wrong? I've burned hundreds of ISOs in my day...

---

### Post by JC Cheloven on 2010-05-24
> **hxcobd said:**
> Torrent ISO failed as well... Error in the GCC folder again...

I'm seriously going insane over here... What could I possibly be doing wrong? I've burned hundreds of ISOs in my day...

This indeed doesn't make sense. Specially if you succesfully burn other iso images. All those you downloaded by different methods can't be all corrupted. Try any (apparently) stupid thing, as dowloading from the pc of a friend at his home (even if he/she uses win2). There must be something in your internet provider/connection/pc/OS/.../

Hope you get this solved.
JC

---

### Post by choochoousmc on 2010-05-24
new user here.
Downloaded the 10.04 lts, created the live cd with power to go in vista.
System crashes at 48% of the install process. errno5   tried three times.
so downloaded and burned the alternate image. get same problem keeps crashing at about 48%
Did a checksum and several files in the live cd are corrupted.
so much for the claim "IT JUST WORKS"
As much as I distrust and hate windows, at least it works.
Beginning to think none of the unix / linux / solaris OS'es are worth a damn.
Just take too much work to get loaded and running. Most don't automatically recognize
all the hardware.

tried to order the "FREE" cd ubuntu, No can do. Donation is required.
And you can NOT contact any one person to get it resolved!

[email]choo_choo@millect.com[/email]

---

### Post by colorlessprism on 2010-05-25
did you request a CD from "https://shipit.ubuntu.com/"? i just got a 10.04 disc a few weeks ago and diddnt have to pay. i would be more than happy to send you a disc  (if you live in the states) if you would still like to try it. ubuntu may not be for everyone, but i would hate to see you give up before you even get to try it.

---

### Post by JC Cheloven on 2010-05-25
@choochoo: we are millions who succesfuly download and install the iso images every now and then, be it by http or by torrent. But there seem to be a handful of people who have trouble with this, and unfortunately we don't figure out why. 
Just a word of hope: you probably would be satisfied if you happen to try ubuntu. I think it's worth solving that cd download problem in any expedient way, as for example asking a friend to do it for you, as I suggested before. I don't think it's an ubuntu fault anyway, the problem has to be somewhere else...

---

