---
title: "Can't sudo, root account not enabled, locked out of machine!!"
date: 2009-12-04
forum: General Help
---

### Post by bcn17 on 2009-12-04
At the beginning of the holidays I traveled back home and thought it would be fun to mess around with my server a bit. This was quickly cut short because I managed to make my account with sudo privlages not a part of the sudo group anymore when I tried to add it to another group I had just made. Now that I am back at the same location of my server I figured I could just plug in a keyboard and monitor and fix everything. However, I still can't sudo and I can't get into the root account because it is not enabled, furthermore, I need sudo to enable the root account....

I went ahead and booted with a install cd and brought up a shell prompt. I then went to the /etc/group file with the idea of adding my user account to the admin group, or sudoer or something. Maybe enable the root account. However, I figure since I am in a recovery cd anything I will have to do will be editing text files. The thing that surprised me is that when I opened up the /etc/group file it only had 1 line. 

root:x:0:   <- where the mad face is a : and a x. Not sure how to change that.... heh heh

Where all the rest of the groups went I have no idea. I assume it has something to do with using a recovery cd... I am stuck. Please help me get back into my server!

---

### Post by fluffman86 on 2009-12-04
I don't know if the server has a recovery mode, but if it does, you can boot into that as root.

---

### Post by bcn17 on 2009-12-04
Okay, so I figured out part of the problem. The /etc/group I tried editing is just a temporary file in the ram that the rescue disk uses. Apparently my HD is mounted on /target. However, /target does not exist. How do I mount my HD then? And when I do, is there a way to enable the root account by editing a text file? Or should I just try and add my normal user account back to a sudoer or admin group by editing /etc/group?

---

### Post by riste on 2009-12-04
You can mount it by finding out which partition your filesystem is on and running mount [device] [directory].  It is likely on /dev/sda; you can find out by listing the partitions:

fdisk -l /dev/sda

 and if one of the partitions comes up as Linux

/dev/sda3           13715       19065    42971040   83  Linux

whatever appears in place of the /dev/sda3 up there is the device with your filesystem.  If it's not on /dev/sda, you might try /dev/hda, /dev/sdb, or something similar in /dev/.

If /target doesn't exist, make it with

mkdir /target


and then

mount [device] /target

then you should be able to edit your group file in /target/etc/group.  If the only problem is that you removed yourself from the admin group, just add your name back to the group and save it.  

admin:x:114:yourusername (that's fullcolon x instead of the emoticon)

When you boot your system again you should be able to sudo.

---

### Post by bcn17 on 2009-12-05
I fixed it! Unfortunately I never managed to mount my HD using the recovery disk. the fdisk command gives an error that says: NO fdisk command. However, ```
ls /dev/disk/by-uuid -alh
``` works well. Google: ubuntu how to fstab  for a great tutorial that is located here on the ubuntu forums. 

Anyways, so when I tried to mount. ```
mount /dev/disk/sda1 /target
```

and ```
mount -t ext3 /dev/disk/sda1 /target
``` 

I got errors as well. Something to the tune of it not being a directory. Although I did make the /target/ directory... hmm. 

Anyway, my fix ended up being to boot to the recovery option instead of the recovery cd, because then my HD was already mounted considering I was using the root account that is part of my system and not a virtual one loaded in ram from the cd. ```
nano /etc/group
``` worked great. ALthough, if anyone else tries this, make sure to followo rista's directions carefully. your username must be added to admin:x:114:, not adm:x:4:. The latter does not work ... heh heh. Thanks for the help everyone. If you know why the mounting didn't work please tell, I got it fixed but am still curious.

---

