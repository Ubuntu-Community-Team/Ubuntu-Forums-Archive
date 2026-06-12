---
title: "kernel panic - not syncing: Attempted to kill init!"
date: 2009-11-15
forum: General Help
---

### Post by Bucky Ball on 2009-11-15
Hi all. You can read what I did to get here at this post:

[http://ubuntuforums.org/showthread.php?t=1322547](http://ubuntuforums.org/showthread.php?t=1322547)

Thought I might have some more luck tackling the issue at hand with a more concise thread. Boot the machine, get to grub, choose kernel, progress bar goes up and back and then stops in the middle, caps light starts flashing and that's it. Hard boot the only way to fix. Run recovery and halts at:

```
Begin: Running /scripts/init-bottom
run-init: /sbin/init : no such file or directory
kernel panic - not syncing: Attempted to kill init!

```Help!

I can boot into Windows no problem and boot off the liveCD no problem so we know this is not a hardware problem. 

Reinstall the kernel? Get in with the liveCD and fix something? Wouldn't know where to start. I have researched this for hours and there is no fix or real explanation I can find.

All help and suggestions appreciated as I am getting desperate. I can save my files but really don't have the time right now (nor do I want) to reinstall. This must be reasonably straight forward. Just have no clues.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
This [http://www.linuxquestions.org/questions/linux-software-2/explained-kernel-panic-not-syncing-attempted-to-kill-init-353920/](http://www.linuxquestions.org/questions/linux-software-2/explained-kernel-panic-not-syncing-attempted-to-kill-init-353920/) might be useful. I'll try to find something more specific though.

This [http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/](http://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/) says bad RAM. Might not be a bad idea to run memtest.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
A lot more specific [http://www.linuxquestions.org/questions/linux-kernel-70/sbininit-kernel-panic-not-syncing-attempted-to-kill-init-723355/](http://www.linuxquestions.org/questions/linux-kernel-70/sbininit-kernel-panic-not-syncing-attempted-to-kill-init-723355/)  Hope it helps

---

### Post by Bucky Ball on 2009-11-15
> **Sin@Sin-Sacrifice said:**
> A lot more specific [http://www.linuxquestions.org/questions/linux-kernel-70/sbininit-kernel-panic-not-syncing-attempted-to-kill-init-723355/](http://www.linuxquestions.org/questions/linux-kernel-70/sbininit-kernel-panic-not-syncing-attempted-to-kill-init-723355/)  Hope it helps

Thanks but been there. Will check your first two links.

Repeat: This is not a hardware issue. All Windows and LiveCD working no problem. It was specifically caused by some commands I put into to try and get my wireless dongle working as outlined in the link in my first post to my original thread. First I killed the wired connection as well and when I tried to fix and reboot, this issue is what I got.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
According to all I've read those commands might have somehow corrupted the /sbin/init section of the hard drive and perhaps other parts as well. Have you run fsck from a live cd? I would do that first... from there it may fix the corruption or you can try to refurbish those corrupted sections of the HDD elsewhere.

---

### Post by Bucky Ball on 2009-11-17
Okay, downloaded the alternate cd and hit 'rescue broken system'. Dropped to a shell and input this:

```
fsck.ext3 -v -f -p /dev/sda6
```From here:

[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

Nothing else seemed to work, not plain 'fsck /' or 'fsck /dev/sda6'. It took awhile and gave me a description of blocks etc. Reported no bad one. I reboot the system and no different ...

Any other suggestions? I have handed in my last assignment for the year today (yay
!) so I now have some time to get stuck into fixing this. :-)

** I almost forgot: When I boot the liveCD, open a terminal and DO run:

```
sudo fsck /dev/sda6
```... it tells me:

```
/dev/sda6: clean
```... followed by the number of files and blocks. Still makes no difference. Just checked again and /sbin/init is definitely there, unless I'm looking at the one on the liveCD if one exists.

If I run:

```
sudo fsck /
```

I get this error:

```
fsck: fsck.unionfs: not found
fsck: Error 2 while executing fsck.unionfs for unionfs
```

---

### Post by Dale61 on 2009-11-17
Got the kernel panic message this morning, so just deleted 9.10.

I had it installed via WUBI, so it's easy enough to re-install, which I'll consider in a few days.

---

### Post by Bucky Ball on 2009-11-17
> **Dale61 said:**
> Got the kernel panic message this morning, so just deleted 9.10.

I had it installed via WUBI, so it's easy enough to re-install, which I'll consider in a few days.

Thanks, but not sure what this has got to do with this thread. This is a rock solid 16 month old install of 8.04 LTS that I am trying to avoid wiping. If you have an issue with 9.10 you are not alone and should perhaps post in a new thread.

I am currently working out how to save configuration, settings and packages so I can just reinstall / and set the machine up exactly how it is/was as fixing the kernel panic is proving to be a difficult and time consuming pursuit. A mysterious one as people only ever reinstall or replace hardware. There must be a fix.

I NEVER use wubi. Only ever full install to hard disk from CD/DVD. ;-)

(btw, Dale, my in-laws live in Clifton Springs just down the road from Geelong and I built my MILaw an open-source box in Feb of this year! That build is the basis for the HOWTO in my signature.)

---

### Post by Dale61 on 2009-11-17
Considering this thread was started yesterday, there is no mention that your install is 8.04 (other than under your username).

I just assumed it was another of the many threads relating to the same problem now encountered with 9.10.

---

### Post by Bucky Ball on 2009-11-18
More info. I tried a few things booting from the liveCD and here's the output:

                                       ```
root@ubuntu:/sbin# sudo e2fsck -C0 -p -v -f /dev/sda6 
                                                                                   
      345010 inodes used (56.37%) 
        **7376 non-contiguous inodes (2.1%) **
             # of inodes with ind/dind/tind blocks: 14212/128/0 
     1899512 blocks used (77.85%) 
           0 bad blocks 
           1 large file 
    
      274422 regular files 
       37675 directories 
          69 character device files 
          26 block device files 
           3 fifos 
         630 links 
       32804 symbolic links (30097 fast symbolic links) 
           2 sockets 
    -------- 
      345631 files 
```

7376 non-contiguous inodes (2.1%)? ... and:
    
    
   ```
root@ubuntu:/sbin# sudo blkid 
    /dev/sda6: UUID="36bd7710-ca84-48c9-9011-e96d336ba192" SEC_TYPE="ext2" TYPE="ext3" 
    /dev/sda1: UUID="FC42EAD442EA9326" LABEL="Vista" TYPE="ntfs" 
    /dev/sda5: TYPE="swap" UUID="653d41d1-f3d8-4e3c-8fdd-a298084b754c" 
    /dev/sda7: LABEL="bigboy" UUID="4317640b-79fe-4ee4-a761-84f84991256e" TYPE="ext3" 
    /dev/sda8: LABEL="FATSO" UUID="4893-E3A6" TYPE="vfat" 
    **/dev/loop0: TYPE="squashfs**
```

The line I have in bold, is that the liveCD boot?

---

### Post by P4man on 2009-11-18
There is nothing wrong with those outputs, non contingeous is similar to fragmentation, and that loop filesystem is indeed your live cd.

Id try chrooting in to your harddisk install and try reinstalling the kernel. Try this from the live cd:

First make your life easier by getting into a full root session

```
 sudo su
```
```
 mount /dev/sda6 /mnt
```

```
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
```

```
 chroot /mnt
```

Then try reinstalling the kernel:
```
sudo apt-get install --reinstall linux-image-whatever-latest-8.04-kernel
```

---

### Post by Bucky Ball on 2009-11-18
Rockin' P4Man. I have been searching trying to figure out how to reinstall the kernel using the liveCD. I figure if it's a kernel panic, maybe if I install it again it might not be panicky!

I'll give that a go. Cheers!


UPDATE: I tried your commands to see if all was happening but when I get to 'chroot /mnt' I get:

```
chroot: cannot run command '/bin/bash'; No such file or directory.
```I do a 'locate for /bin/bash and it is there.

---

### Post by Bucky Ball on 2009-11-18
I got the laptop online! Makes things a lot easier. Still won't chroot but I tried this anyhow and got this result:

```
root@ubuntu:~# sudo apt-get install --reinstall vmlinuz-2.6.24.25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmlinuz-2.6.24.25-generic

```

---

### Post by P4man on 2009-11-18
> **Bucky Ball said:**
> Rockin' P4Man. I have been searching trying to figure out how to reinstall the kernel using the liveCD. I figure if it's a kernel panic, maybe if I install it again it might not be panicky!

I'll give that a go. Cheers!


UPDATE: I tried your commands to see if all was happening but when I get to 'chroot /mnt' I get:

```
chroot: cannot run command '/bin/bash'; No such file or directory.
```I do a 'locate for /bin/bash and it is there.

Thats not good. You sure you mounted the correct partition? Can you browse that partition (/mnt) after mounting it ? Can you check if there is a /bin folder in it (with bash and all the rest) ? At this point it sounds a lot more like a drive (or filesystem) failure than anything else

**edit**: /bin/bash is your livecd filesystem. Check /mnt/bin/bash after mounting sda6

---

### Post by Bucky Ball on 2009-11-18
Okay, bad news.

I booted the liveCD to finish backing up my partitions before getting back into it. Switch the laptop on and boot the liveCD, go make a cup of tea. I come back just in time to briefly glimpse the screen fade to black. Hmm. Hit the space bar. No, not power saving. Hold down power button only option and reboot. Goes to black screen. Power lights are on but nobody's home. Yes, they are home because the lights go out then back on again ... to a black screen. This repeats ad infinitum, the machine attempting to boot, hitting a black screen for about 20 seconds then restarting itself. I can't even get to the BIOS. Screwed.

I think this is related to another issue. This is a HP DV6000. HP USA eventually admitted there was a problem with them where one of the symptoms was wireless card dying afer coming out of suspend. Mine died. But that wasn't the end of it. There wasn't a problem with the wireless card, it actually generates from the motherboard which will sooner or later die. Probably sooner. Here's a link to a thread which explains my whole HP adventure. Go from post #3.

Wish me luck and thanks for all the help but I think that is the end of the line for the laptop for now. If I manage to resurrect it I'll post back. I have so much work on that hard drive which I was halfway through backing up. YAAAAAAAAAGH! :-(

---

