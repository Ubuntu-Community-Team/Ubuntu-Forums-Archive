---
title: "My kernel is panicing!"
date: 2010-02-11
forum: General Help
---

### Post by 1awesomeguy on 2010-02-11
My desktop computer has always randomly froze since I built it three years ago (probably something to do with me not installing the processor heat sync correctly). It recently just froze so I did what I always do and hit the restart button.

This time I am met with a strange message and my computer does not boot:

```
Boot from (hd0,0) ext4   [a bunch of numbers and letters here]
Starting up ...
[    11.892273] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

My computer had recently updated using automatic update and asked me to restart. I just clicked on "I'll restart later" (not exact message), but due to the computer freezing, I did not get the chance to restart/shutdown the correct way. I hope I did not mess up my system. Any help would be very much appreciated as I have very sensitive files on the computer (I know I can probably recover them using a live CD).

Thanks!

I have Ubuntu 9.04 installed.

---

### Post by Richard1979 on 2010-02-11
[http://ubuntuforums.org/showthread.php?t=1280623](http://ubuntuforums.org/showthread.php?t=1280623)

This *may* help.

---

### Post by 1awesomeguy on 2010-02-11
> **Richard1979 said:**
> [http://ubuntuforums.org/showthread.php?t=1280623](http://ubuntuforums.org/showthread.php?t=1280623)

This *may* help.

Looks like the guy in that thread never found a solution (or never posted the solution). I will try to reinstall Grub using Giblet5's instructions from the thread and will see if that works.

---

### Post by 1awesomeguy on 2010-02-11
Still having problems...

I tried reinstalling Grub:

From [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")
> [LIST=1][*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.[/LIST]

After step 5, I get:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```


Then, I tried the GUI method from the [same page]("https://help.ubuntu.com/community/GrubHowto"):
> [LIST=1][*]Boot your computer up with Ubuntu CD
[*]Go through all the process until you reach "[!!!] Disk Partition"
[*]Select Manual Partition
[*]Mount your appropriate linux partions  / /boot swap ..... 
[*]DO NOT FORMAT THEM.
[*]Finish the manual partition
[*]Say "Yes" when it asks you to save the changes
[*]It will give you errors saying that "the system couldn't install ....." after that
[*]Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
[*]Jump to "Install Grub ...."
[*]Once it is finished, just restart your computer[/LIST]

I went through the whole process and did not format any of my partitions including the /boot partition.

I am still getting errors:

```
Boot from (hd0,0) ext4   [numbers/letters...]
Starting up ...
[    0.209065] ACPI: Aborted because invalid compressed format (err=1)
[   12.522692] RAMDISK: ran out of compressed data
[   12.522742] invalid compressed format (err=1)
[   12.566438] Kernel panic - not syncing: VFS: Unable to mount fs on unknown-block(0,0)
```

Please help...

---

### Post by 1awesomeguy on 2010-02-11
Solution:

I was afraid of doing this since the instructions on the GRUB wiki told me specifically not to, but it solved my problems.

I just reinstalled from the Ubuntu Live CD like I had done previously with one exception. I identified all my partitions on the install (like my previous post), but only reformatted the /boot partition. To solve this problem you will need to reformat whichever partition holds your /boot files. For me, I was lucky that I had /boot on a separate partition. If you have a separate / partition, then format it during the install and your system should be back to normal (though you will have to reinstall all your programs).

---

