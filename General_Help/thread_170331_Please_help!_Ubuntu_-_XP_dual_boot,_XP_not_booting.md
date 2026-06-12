---
title: "Please help! Ubuntu - XP dual boot, XP not booting"
date: 2006-05-04
forum: General Help
---

### Post by mailforbiz on 2006-05-04
Hi

I finally got around to installing Ubuntu on the spare free space I'd set aside on my XP HD. 

I didn't do the automatic partition and instead manually partitioned /, /usr, /home and /tmp and installed Ubuntu. The install seemed to have completed w/o any problems and when prompted, I decided to use the grub boot menu on the MBR.

Now, I can get into Ubuntu w/o any problems but when I boot into XP, i get the Windows XP logon screen for a second and the computer then reboots.

I had Norton Systemwork's GoBack on XP before which used to bring up its own splash screen before the XP one but I don't see that anymore and I'm suspecting this has something to do with the behaviour.

Any help will be greatly appreciated! Please, please, I DON'T want to have to reinstall XP (I know I'm thinking the worst case but don't know how close I'm to that :(  )

BTW, I don't see a /etc/grub/grub.conf in Ubuntu but I was able to see the following on the screen just after selecting XP on the Grub boot:

root (hd0,0)
Filesystem type, Unknown, partition type 0x44
savedefault
make active
chainloader +1

HT

---

### Post by nanotube on 2006-05-04
[QUOTE=mailforbiz]Hi

I finally got around to installing Ubuntu on the spare free space I'd set aside on my XP HD. 

I didn't do the automatic partition and instead manually partitioned /, /usr, /home and /tmp and installed Ubuntu. The install seemed to have completed w/o any problems and when prompted, I decided to use the grub boot menu on the MBR.

Now, I can get into Ubuntu w/o any problems but when I boot into XP, i get the Windows XP logon screen for a second and the computer then reboots.

I had Norton Systemwork's GoBack on XP before which used to bring up its own splash screen before the XP one but I don't see that anymore and I'm suspecting this has something to do with the behaviour.

Any help will be greatly appreciated! Please, please, I DON'T want to have to reinstall XP (I know I'm thinking the worst case but don't know how close I'm to that :(  )

BTW, I don't see a /etc/grub/grub.conf in Ubuntu but I was able to see the following on the screen just after selecting XP on the Grub boot:

root (hd0,0)
Filesystem type, Unknown, partition type 0x44
savedefault
make active
chainloader +1

HT[/QUOTE]
well, don't know precisely what your problem is, but i can tell you where to find the grub config file. 
its in /boot/grub/menu.lst

---

### Post by neouser99 on 2006-05-04
hum... interesting. could you post the output of these two commands:
```

fdisk -l
cat /boot/grub/device.map

```

im guessing that its possible that hd0,0 is not your windows partition. if it is, you might try changing
```

root (hd0,0)

```
to
```

rootnoverify (hd0,0)

```

-neo

---

### Post by mailforbiz on 2006-05-04
Thanks for the quick reply, neo. Sorry, I am not in front of my PC at the moment. But one thing that I  just remembered is that when doing the manual partitioning, I put the / 's bootable flag as on (thinking thats the way to go for dual-boot). Maybe I shouldn't have?

I'll post the fdisk results as soon as I can.

Thanks again.


[QUOTE=neouser99]hum... interesting. could you post the output of these two commands:
```

fdisk -l
cat /boot/grub/device.map

```

im guessing that its possible that hd0,0 is not your windows partition. if it is, you might try changing
```

root (hd0,0)

```
to
```

rootnoverify (hd0,0)

```

-neo[/QUOTE]

---

### Post by mailforbiz on 2006-05-10
All, 

Just as a FYI, I was able to get back into XP by changing the partition type to 7. 

Lesson:- If you have Norton Goback on your Xp, deactivate it before installing Ubuntu dual-boot as otherwise you won't be able to boot into XP. For some reason, Norton changes the partion type for XP/NT and so Lilo/grub barfs.

HT

---

### Post by gam3r4eva on 2006-07-22
Dang.  I have Norton GoBack on my computer, and I can't get grub to even work.  Guess I should have realized it wouldn't when Partition Magic wouldn't work unless I disabled GoBack.

Would you mind telling me what you did to make XP bootable?

---

### Post by mailforbiz on 2006-07-23
It has been a while but if I remember right, you'll have to boot into Linux, and edit /etc/fstab and change the partition type to 7. (0x07 in hex). I'm assuming you're still able to boot into Linux. Good luck.

---

### Post by jakechance on 2006-10-08
I'm having a similar problem. I disabled GoBack to get some space off of my windows partition. I then created a swap and root partition for ubuntu. I can boot into either OS and they work just fine. The problem comes when I try and re-activate GoBack. I can only do this from within Windows. It then restarts the computer and shows the GoBack splash screen. It then goes to GRUB but none of the options work (windows or ubuntu). I believe they say unknown partition 0x7 and return me to the GRUB menu. If I restart the computer and deactivate GoBack from its initial boot menu, everything works again. I would like to use GoBack as it is very helpful when something screws windows up.

I was reading this post and it looks like it is along the same lines as my problem, but I don't know what to change to 0x07 like the previous post suggested. Any help is greatly appreciated. Thanks.

---

### Post by jakechance on 2006-10-08
Hey,
One update to my post. It says the partition is 0x7 when I choose Windows XP Pro but it says its another 0x83 or something when I choose ubuntu. I believe this is not the error as after this and a few other statements, it says something like "Error 29: Disk write error." Again this goes away if I hit the power button and disable GoBack right before it goes to GRUB. Hope someone else has figured out the solution to this, cause I'm a bit clueless.

---

### Post by jakechance on 2006-12-13
hello? anyone?

---

### Post by rich.bradshaw on 2006-12-13
Why do people insist on having unnecessary Norton crap on their PCs? Having seen similar things a lot of times I can safely say, Norton products are not a good thing to use. :)

Sorry, don't know what to do - try searching not just this forum, this sounds like a Grub problem more than Ubuntu.

---

### Post by jakechance on 2006-12-14
It's hard to say, it's very nice having Norton AV running since there is all that nasty stuff out there for windows and incase some of it gets through (or some annoying piece of malware), GoBack will simply make it as if it never happened, in minutes. Also I actually bought them so I'd really like to be able to use them. There isn't anything else in the forum about this :(

---

