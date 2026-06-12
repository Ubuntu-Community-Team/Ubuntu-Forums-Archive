---
title: "removed raid array keeps coming back after reboot"
date: 2006-05-28
forum: General Help
---

### Post by bobdazzla on 2006-05-28
Hi there,

I had a hard system lockup while creating a 6-disk array using mdadm. After rebooting, instead of using mdama to --remove the arrays, I manually deleted /dev/md0 and /dev/md1 and then used MAKEDEV to create new md blocks. These were automatically created in my home directory, and I manually copied them over to my /dev/ directory.

Anyways, now everytime I reboot, I have  two arrays that are  automatically started. 

(cat /proc/mdstat results:)
```

bobdazzla@mmklinux:~$ cat /proc/mdstat
Personalities : [raid5]
md1 : inactive hdk5[6]
      194563072 blocks
md0 : active raid5 hdc[0] hde[1]
      390721536 blocks level 5, 256k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>

```

even after using mdadm to stop then remove these arrays...
```

bobdazzla@mmklinux:~$ sudo mdadm --stop /dev/md?
Password:
bobdazzla@mmklinux:~$ sudo mdadm --remove /dev/md?
mdadm: cannot get array info for /dev/md0
bobdazzla@mmklinux:~$ sudo mdadm --remove /dev/md0
bobdazzla@mmklinux:~$ sudo mdadm --remove /dev/md1
bobdazzla@mmklinux:~$ cat /proc/mdstat
Personalities : [raid5]
unused devices: <none>
bobdazzla@mmklinux:~$
```

They always return when I reboot. The weird thing is, these arrays look NOTHING like the ones I was originally trying to create. I really have no idea where they're coming from. I'm guessing the hard system crash messed something up, and/or I made a wrong move during the raid creation that caused such strange arrays to be created... anyways, for now what I want to focus on is permanently deleting these two arrays.

I'm guessing there is a conf file on my system somewhere that is restarting these arrays, but I have no idea where! If someone could help me permamently delete these arrays i'd appreciate it. thanks in advance.

---

### Post by bobdazzla on 2006-05-28
oops... should have tried searching the forums a little better... 

[http://ubuntuforums.org/showthread.php?t=122743](http://ubuntuforums.org/showthread.php?t=122743)

I think this will take care of my problem.

---

### Post by bobdazzla on 2006-05-28
[QUOTE=bobdazzla]oops... should have tried searching the forums a little better... [http://ubuntuforums.org/showthread.php?t=122743](http://ubuntuforums.org/showthread.php?t=122743) I think this will take care of my problem.[/QUOTE] ok, checked out all the suggestions in that thread, no luck. Any advice?

ok, i think my usage on "mdadm --remove" might be incorrect... according to this guide:
[http://www.devil-linux.org/documentation/1.0.x/ch01s05.html](http://www.devil-linux.org/documentation/1.0.x/ch01s05.html)
I need to specify the array to be removed, THEN specify the individuals disks of that array (which I haven't been doing thus far). will report back with the results...

---

### Post by bobdazzla on 2006-05-29
what finally worked was using the command at the bottom of the above link to "zero out" the superblocks on the drives themselves. I guess mdadm was automatically scanning all my hard disks during startup, saw the matching superblocks on /hdc/ and /hde/, assumed they were part of an array with each other, and automatically started a failed array at /dev/md0. Zeroing the superblocks makes "cat /proc/mdstat" return no raid arrays.

---

