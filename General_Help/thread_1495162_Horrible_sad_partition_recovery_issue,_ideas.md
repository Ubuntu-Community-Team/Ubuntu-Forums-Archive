---
title: "Horrible sad partition recovery issue, ideas?"
date: 2010-05-27
forum: General Help
---

### Post by searchfgold6789 on 2010-05-27
Hi!

I haven't used ubuntu for awhile because my RAM wasn't good enough for it and I had to reinstall (see sig for RAM, it's dirty old pc100). I figured Xubuntu would be easier on it, for some reason, and actually I was right.

And now for admittance: I overwrote my precious Windows XP NTFS partition with a xubuntu install :guitar::guitar::guitar:so so cool of me

I used a partition recovery program from a usb disk I made, and I think it must have recovered, but with injuries: gparted won't touch it because the file system's broken, when i force mount it (I have my means) there's only one 800 megabyte file on it, the XP recovery console thinks it's a FAT partition and doesn't ask me for a password or partition selection, and chkdsk of course (now get this!) ... **won't run because the file system's broken **lol! Isn't chkdsk supposed to fix those problems?
Anyway, I went ahead and foolishly overwrote my MBR and did a fixboot. Now CMOS apparently knows there is a bootable thing on the disk (probably because it's a primary partition) but doesn't want to boot it for some reason and just takes forever to not do anything. I'm on the live cd with 256 MB of RAM right now.

What i think I should do is find a command that will clean the NTFS partition for me, but I don't know of any. By recovering that partition did I just screw it up even more?


[COLOR=SandyBrown][SIZE=4]Noobs can answer this, all I'm looking for is a program to clean an NTFS partition :)
[SIZE=1]
[/SIZE][COLOR=Black][SIZE=2][SIZE=1]Yours truly,
 - search[/SIZE]
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by geet89 on 2010-05-27
i think (assuming that you have already lost all the data.. and dont want to recover it..)
install xp on the remaining good partition and then use something like hard disk sector repairer 2.0..(google it)..if u are not able to find it u can email me and i will host it and send u the link. or u could even use partitiion magic, if it works, it will be great..

and after that u can start all over again with your xubuntu live cd..

or if you want to recover your data you could send it to some data recovery company who can do it for you at a premium..

hope this helped..:guitar:


[email]geet.89@live.com[/email]

---

### Post by DeMus on 2010-05-27
Do you still need your "precious" Windows? If not, reboot from CD and do a clean install of Xubuntu, choose the partitions setup the way you want it and enjoy.
If you do need Windows, install it on about half of the disk and use the other half to install Xubuntu. You'll have a dual install that way and can choose which OS to boot every time you start-up the computer.
Install Windows first and then Xubuntu. That way the bootloader program Grub will take care of the dual boot. When you do it in the reverse order Windows will take over your computer. That's just the way Windows is,

---

### Post by searchfgold6789 on 2010-05-27
I know, but I do need windows, im sorry. Data recovery companies are worth checking out at this point.
The reason I need windows so badly is because I had a torrent running on it that was downloading 20GB worth of (mostly) public domain sheet music, and I can apparently only start it again from windows, where it left off. And also I spent an entire summer when I was 12 working to earn money to buy that windows cd. :cry: What if I got wine and put a shareware recovery suite on it? Nope, won't work never mind. What are some good companies that will restore your data for you? can they recover my whole partition?

---

