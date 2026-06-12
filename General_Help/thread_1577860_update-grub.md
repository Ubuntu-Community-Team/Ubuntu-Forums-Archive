---
title: "update-grub"
date: 2010-09-19
forum: General Help
---

### Post by ki4jgt on 2010-09-19
I had a problem that started from this thread,

[http://ubuntuforums.org/showthread.php?t=1577797](http://ubuntuforums.org/showthread.php?t=1577797)

Now it has been fixed, I've edited my grub file on my HD with the live-CD, now how do I update-grub on my HD?

---

### Post by drs305 on 2010-09-19
> **ki4jgt said:**
> I had a problem that started from this thread,

[http://ubuntuforums.org/showthread.php?t=1577797](http://ubuntuforums.org/showthread.php?t=1577797)

Now it has been fixed, I've edited my grub file on my HD with the live-CD, now how do I update-grub on my HD?

Which grub file did you edit? If it was /etc/default/grub, where you added your options, and you have currently booted to a normal running of Ubuntu (not the LiveCD) just run:

```

sudo update-grub
```

---

### Post by ki4jgt on 2010-09-19
O and yes, it was that grub file.

No, I'm on the LiveCD, and I've updated the HD. I can't get the HD to boot until noapic is working, which requires me to update-grub on the HD that isn't working :-) if this makes any sense at all, just try to understand, I haven't slept in 3 days.

---

### Post by drs305 on 2010-09-19
No, what you want to do makes sense. You need to 'chroot' into your real install from the CD.

Mount your Ubuntu partition and the necessary files (change [COLOR="Red"]sda1[/COLOR] to the appropriate device):
```

sudo mount /dev/[COLOR="Red"]sda1[/COLOR] /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Your terminal prompt should now include "root", indicating the commands above were executed. Now the commands you run will act on your real Ubuntu installation.

Since you are root, you don't use sudo:
```
update-grub
```
After G2 has updated, exit the chroot:
```
exit
```

Unmount the folders (change [COLOR="Red"]sda1[/COLOR] if needed, and reboot:
```

sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /dev/[COLOR="Red"]sda1[/COLOR]

```

If it works, go get some sleep!  ;-)

---

### Post by ki4jgt on 2010-09-19
Thank you so much!! It worked!! but now my internet won't. I can't get connected at all from my HD, yet the CD will. LOL :-O

And now it works :-) Thanks again!!!

---

### Post by drs305 on 2010-09-19
Ok, well one step at a time I guess...

Will you mark this thread SOLVED with the thread tools link at the top right of the first post if you haven't any more questions. Then start a new thread if you wish about your connection. I'm not an expert on that one and you'll get better results with a more appropriate thread title.

See you on the forums - if you can connect.  ;-)

---

### Post by Jonners59 on 2010-09-21
**Problem booting after Update/new kernal; Either blank screen or kernal will not load:**
 
I tried the suggestion below, but I found I could not mount the drive. I get a message (if I boot using the CD) if I select from "Places" that says 
 
[I]"Error mounting: mount exited with exit code 32: mount: wrong type, bad option, bad superblock on /dev/ada1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg ! tail or so"
[/I]
The cmd line route following the instructions in previous thread (with ammendments to direct to the correct directory throws up a different but similar error message:

[I]"wrong fs type, bad option, bad superblock on dev/sda1, missing codepage or helper program, or other error. In some cases useful in fo is found in syslog - try dmsg...".
[/I]
The syslog gives:

"sd 0:0:0:0: [sda] Sense key : Medium Error [current] [descriptor]
Descriptor sense data with sense descriptors (in hex) :
72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
06 84 1f 66
sd 0:0:0:0: [sda] Add. Sense: Uncovered read error - auto reallocate failed
end_request: I/O error, dev sda, sector 109322086
atal: EH complete
JBD: Failed to read block at offset 998
JBD: recovery failed
EXT4-fs (sda1): error loading journal"

Each line above starts with a number [ 1261.945015] etc.....

Now, I go from a problem on one machine to a problem on another. Last Friday (a week ago) after an update, I found that machine would not boot either and when I installed the CD I could not open the directories either. Same problem. I ended up completely rebuilding the machine and lost all my data - again!!!! I also have another machine that the same problem occured on, unable to boot and when the CD was installed I could NOT open or mount any of the directories either.  **_Maybe there is a prob with the update/kernal_** that went out.

 
**Solution to this:**
After running the Ubuntu CD in try Ubuntu mode/option
Open gPARTED from the menu.
Select each driver/directoriy and select "TEST" (right click or from the menu) and OK to all questions.  This will test and then repair the directories.
 
Reboot and all SHOULD be working.
 
Footnote:
I did find on one machine the Directory was Mounted already and had to be unmounted to get the "Test" option in the drop down menu.  Do whichever to get the "Test" option available
 
Although I did not realize this with my first problem PC, at least I was able to fix 2 machines without too much trouble.

---

