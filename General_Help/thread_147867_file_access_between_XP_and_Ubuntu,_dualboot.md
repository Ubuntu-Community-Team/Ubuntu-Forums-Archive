---
title: "file access between XP and Ubuntu, dualboot"
date: 2006-03-21
forum: General Help
---

### Post by baalho on 2006-03-21
Hey,
really new to linux. 
Ubuntu is really nice.

here is my question.

I would like to open my media files in xp (ntfs) and linux (ext2 of something) and maybe even from my xbox (modded).
I can access XP network share fine.
Probably have to setup smba to access ubunu share to access from xbox.

ideally i would like to accesss my files in the windows partition from xbox while running ubuntu.
security is not an issue, all behind my router and to test it i dont wanna get confused with setting up things in linux.

everything seems so hard in linux sometimes.

ok, I dual boot.
got XP sp2 and Breezy going on the same Hardisk.

trying to make sense of the guide on how to setup smba right now.

sorry for the long post.
will appreciate any help.
thanks

---

### Post by dermotti on 2006-03-21
Mount ntfs drives:

[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

i would assume then you could just share the folder with samba

---

### Post by baalho on 2006-03-21
thanks man
i should have searched before posting too :P

is it true that you cannot write to ntfs drives. I gave very little space to my linux partition.

in any case, i am using windows to post this :P

i did hear the world Mount somewhere.
now to try it...after i finish downloading :)
thanks

---

### Post by akiro.yamamoto on 2006-03-21
You can have write access to a NTFS partition but you will need an app like Captive to be able to do so. Not sure about the reliability of it, but I have heard good reports about it.
Personally I backed up my data and re-formated 1 of my NTFS partitions to EXT3 then installed the extfs drivers in windows to access the partition. Works very good for me ;) Now I have seamless read and write access to that partition  from both Ubuntu and WinXP 8)

---

### Post by nanotube on 2006-03-21
the best way to have read-write capability between win and ubuntu is to have a separate partition that is fat32, and use it as a shared data drive for both. that is what i have on my dual boot, and it works just fine.

(i even set up my thunderbird email and my gaim profile to reside on that shared drive, so that whether i open tbird/gaim on ubuntu or windows, i get the exact same stuff. though... i have not used windows in months now, so all that effort kinda turned out for nothing. but hey, it was cool :) )

check out the link in my sig for how i set up my system...

---

### Post by baalho on 2006-03-21
wow
man its working like a charm.
i just right clicked and shared that folder in the ntfs mounted directory.
now to see if i can actually access it.

how do i create a shortcut to a directory in the desktop.

when i tried it..if i were to drag it. the whole folder was about to be copied.
and i couldnt right click and drag.

this is fun:P

---

### Post by nanotube on 2006-03-21
to create shortcut, hold ctrl-shift while click-dragging. :)

---

### Post by baalho on 2006-03-21
i love you

---

### Post by nanotube on 2006-03-21
... i love you too. ;)

---

