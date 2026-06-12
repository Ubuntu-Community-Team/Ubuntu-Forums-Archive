---
title: "Howto get GRUB 1.99 boot the new disk/partition"
date: 2011-10-02
forum: General Help
---

### Post by Goover on 2011-10-02
Hi, I have an old harddisk with W7U and Ubuntu 11.04 using GRUB 1.99. I now have decided that I need more space for Ubuntu, and has moved a copy of the /dev/sda5 (Ubuntu) and /dev/sda6 (Swap) to the new disk /dev/sdc5 and /dev/sdc6 respectively.
 
The problem then being, how to get GRUB to understand that I need a new boot entry?
 
I will keep the old drive Ubuntu partitions while I test the move being successful, but I know how to get rid of them from the GRUB 1.99 boot menu, later on...
 
But how to get GRUB to boot the new dedicated drive?
 
Thanks in advance for any help!
 
G(r)oover

---

### Post by praveenthivari on 2011-10-02
Try this.
```
sudo apt-get update grub
```

---

### Post by grahammechanical on 2011-10-02
Hi

Are you able to boot into the Ubuntu on sdc5?

May I suggest that you boot into the Ubuntu on sda5 and run  in a terminal sudo update-grub. That should put the Ubuntu on sdc5 on the Grub menu. 

Then when you boot into the Ubuntu on sdc5 either run sudo update-grub from there or install Grub and then run sudo update-grub. This will make the Grub on sdc5 as the menu loader which you will need to be the case for when you remove the old drive.

You could also install Grub customizer. I would suggest on Ubuntu sdc5.

Here are the links

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

 I have these two pages bookmarked. They are very useful

Regards.

---

### Post by Goover on 2011-10-02
Thanks for that suggestion, but...
 
from terminal type the command as suggested but get the E: The update command takes no arguments. I tried to reverse your suggestion as ... grub update but then:E:Invalid operation grub.
 
Should I be in the grub directory?
 
G(r)oover

---

### Post by grahammechanical on 2011-10-02
Did you put a space between update and -grub? That would cause the terminal to see -grub as an argument to the command update.

Note this comment in the Grub 2 Basics document I linked to 

> To update the GRUB 2 menu, the command sudo update-grub will be used throughout this guide. update-grub actually runs the command "grub-mkconfig -o /boot/grub/grub.cfg" This runs several scripts and incorporates the results into /boot/grub/grub.cfg which detemines what is seen on the screen during boot. Since the GRUB 2 developers do not intend to remove the update-grub 'stub', it will be used for simplicity and ease of use.


This is where I am getting my information from. I do not think that you need to be in the Grub directory.

Regards.

---

### Post by Goover on 2011-10-02
Thanks grahammechanical!
 
I will test that, and I am just testing to boot from the new partition via the Live_CD.
 
G(r)oover

---

### Post by Goover on 2011-10-02
Well, there was no success. - 'sudo update-grub' did not find the new harddrive. (But gparted live does...) Booting normally through GRUB into the old Ubunto 11.04 andchecking what drives there are, does NOT even show the new partition. And, unfortenately the Ubuntu liveCD doesn't work since I upgraded to the NVIDIA GTX560CU, so I can't hook up to that partition from there.
 
I will have to consider aborting this method, after making a new attempt via another method to backup/move the partition one more time. But I hesitate because it is more than a weeks work to reinstall everything.
 
But before attempting any of the above I wonder if there is some method to edit, force GRUB to add a new partition available for boot.
 
I will sure use the grub configurator, which looks promising for future use, but it doesn't look like it can do exactly what I want now.
 
Does the above give anyone any clues to what may be wrong?
 
G(r)oover

---

### Post by Goover on 2011-10-03
Well, I booted from the "old" Ubuntu 11.04 partition, /dev/sda5 and installed Grub-customizer, and let it update. It found the /dev/sdc5 partition which has the same version of the OS on it.

Yes, there was in the new section Ubuntu (on dev/sdc5) and a similar recovery. Fine I thought. I took away a few non-usesful items like the serial memtest and saved and restarted the computer.

Yes, alright, I thought, because below the old statements for /dev/sda5 and the W7U I found the Ubuntu on /dev/sda5 and the item below was the recovery. So, I chose the /dev/sdc5 and it booted up fine...I thought...

...Then I went to Applications->System Tools ... and there was Grub Customizer ... which I had not previously installed before copying Ubuntu from /dev/sda5 to /dev/sdc5.

Checking with 'mount' ... yes it had booted up from /dev/sda5, not from the boot indicated by my choice of Ubuntu (on /dev/sdc5). WHAT IS GOING ON HERE?

I have tried to mount /dev/sdc5 from within the boot of the old /dev/sda5, and that works but doesnt get me any further.

Is there a problem that the new drive when I copied Ubuntu and the Swap still are partitions under a W95 extended partition, which it was on the /dev/sda disk?

Grateful for more assistance since I am apparently(?) more close to fining a solution to this...

G(r)oover

---

