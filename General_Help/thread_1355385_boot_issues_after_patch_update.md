---
title: "boot issues after patch update"
date: 2009-12-14
forum: General Help
---

### Post by jadcox on 2009-12-14
running 9.10 for some time now on my laptop, and have the system set up to automatically load latest updates.

last night, it performed the update, and then when it rebooted, it would not complete the boot sequence.

Boot from (hd0,0) ext3 df48#################### (a long number)

it finally times out and give the following error

"Gave up waiting for the root device. Common problems:7be20c06802

Boot args (cat /proc/cmdline)
check rootdelay= (did the system wait long enough?)
check root= (did the system wait for the right device?)
Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/df48e556-ae87-4afc-bc06-d7be20c06802 done not exist. Dropping to a shell!

I rebooted and hit the esc key to go to the options of selecting what I wanted to boot. I used the edit option to look at all the old boot loaders and all of them have this same non-existing uuid reference.

I went to the /dev/disk/by-uuid director and found another id, but not the one listed in the boot loaders.

I am not an experenced user, but am willing to learn!

---

### Post by jbrown96 on 2009-12-14
Let's try to eliminate the UUID (that really long character string).

When the computer first boots, you should get a grub menu (might have to press Esc or Shift). The first entry should have the largest kernel number; highlight it and press "e". You should get something similar to this (but it depends if you installed 9.10 clean or upgraded). It doesn't matter if yours looks quite a bit different; the steps are the same. Here's mine >         recordfail=1                                                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                                                 
        set quiet=1                                                                                             
        insmod ext2                                                                                             
        set root=(hd0,1)                                                                                        
        search --no-floppy --fs-uuid --set 72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3                                 
        linux   /boot/vmlinuz-2.6.31-11-generic root=UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-11-generic
Basically you need to go through the entry (using the arrow keys) and remove everything that has the UUID (for me 72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3) in it and replace it with /dev/sda1 (this appears right form your post,  but we may need to try other values; post back if you have problems with /dev/sda1 or you may try /dev/sda2, /dev/sda3, but I doubt it would be past 3). At the end of a really long line is "splash" change that to "nosplash" (no quotes). There should be instructions on how to boot; it's either Ctrl+x or "b".

---

### Post by spiderbatdad on 2009-12-14
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=813090)

---

### Post by jadcox on 2009-12-14
I tried to replace the uuid with the dev/sda1 (and the others), but something else is wrong here.  When I did this (which there may be a good chance I did it wrong) it came back with a file error message.
 
When you say replace all references to the UUID with /dev/sda1 what exactly do you mean by this?  Replace the entire line?  Replace just the long *** number with it?  
 
Mine looks like this.
 
 
[COLOR=black]uuid 72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 
kernal  /boot/vmlinuz-2.6.31-16-generic root=UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 ro quiet splash
initre /boot/initrd.img-2.6.31-11-generic[/COLOR] 
quiet

---

### Post by jbrown96 on 2009-12-15
Try changing the first line to > root=hd(0,0) and then change the root=UUID=... to > root=/dev/sda1

You might also try choosing an older kernel (regular or recover). If you can get that to boot, then run ```
sudo update-grub
``` and that should fix the problem.

---

### Post by jadcox on 2009-12-15
came back with a error message from the first line.
 
"error 11:  Unrecognized device string"
 
Press any key to continue

---

### Post by jadcox on 2009-12-15
Solved!!  
 
Ok, so here's what I had to end up doing.
 
Boot system and press the "Esc" key when prompted to bring up the boot option menu
 
I chose one of the older recover options, and pressed "e" to edit it.
 
I changed the first line to "root=(hd0,0)
I changed the root=UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 ro quiet splash             to
                     root=/dev/sda1 ro quiet nosplash
 
It finally came up and performed a check disk on the sda1 disk
 
Next it came up with a menu that allowed me to go through several options of running clean up commands.  After doing this I rebooted the computer and everthing came up as normal!
 
Thank you all

---

### Post by JSulli on 2010-01-08
Thanks for these posts guys especially for jadcox's clear description of what s/he did:

> **jadcox said:**
> Solved!!  
 
Ok, so here's what I had to end up doing.
 
Boot system and press the "Esc" key when prompted to bring up the boot option menu
 
I chose one of the older recover options, and pressed "e" to edit it.
 
I changed the first line to "root=(hd0,0)
I changed the root=UUID=72700e93-eb0d-4198-b2d1-3a9d6b1cdbb3 ro quiet splash             to
                     root=/dev/sda1 ro quiet nosplash
 
It finally came up and performed a check disk on the sda1 disk
 
Next it came up with a menu that allowed me to go through several options of running clean up commands. After doing this I rebooted the computer and everthing came up as normal!
 
Thank you all

I finally managed to get Ubuntu up and running thanks to your help.
However, as soon as I rebooted or started up the line like this

 root=UUID=72700e93-e......

had been reset meaning I had to keep editing the boot option menu every time I wanted to use the machine. On reading about a bit I discovered that I was using 'legacy GRUB' not GRUB 2 (I was not given the choice to switch when upgrading). I followed the instructions here

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and upgraded. Now it boots properly.
Thanks again for your help - maybe this might help someone else at some point.

---

### Post by Ozzin on 2010-01-23
I don't know if it made a difference, but it worked for me when I changed the first line in the grub editor  (as described in jadcox's latest post) to root (hd0,x) without the "=". For me x was 5 -- it may be different for different people.

(If you change x in then you need to change the T in /dev/sdaT as well: T = x+1, so for me it was sda6. Also, it may be that you boot from hd1 rather than hd0, in which case it might be /dev/sdbT.)

---

### Post by Jimmycrackorn on 2010-02-15
thanks Ozzin and JSulli, your suggestions worked. I found my drive by incrementally increasing the value from (0,0) to the final (0,4) and adjusting /dev/sda1 to /dev/sda5. Then I installed grub2 per [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and no have no problems booting up now. Cheers

---

