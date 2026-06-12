---
title: "Using Old Drives in New Computer"
date: 2011-07-31
forum: General Help
---

### Post by strange_cathect on 2011-07-31
Hi everyone,

My computer's motherboard died a few days ago and I'm buying a new machine today. Since I've already got 2 hard drives with Ubuntu on them and all my files, I'd like to just place them into the new machine and fire it up.

My question: what will happen if you just "transplanted" the drives into a new computer and turned it on?

Will I need to edit fstab or something?

Thanks

---

### Post by surajrajpurohit on 2011-07-31
hi,
   Well i'm newbie to ubuntu...but i can advice u sumthing....
i hve faced smilar situtation...
u can connect both hard disk to ur computer. den u can install new ubuntu in one of dis harddisk and den after installing ubuntu u can access all the data in second hard disk which u don't want to delete...

---

### Post by strange_cathect on 2011-07-31
I was considering doing just that. But I'd really hate to have to go back through and reinstall my Ubuntu OS to my specifications. It may be what I have to do, though...

---

### Post by CharlesA on 2011-07-31
Should be fine.

Might have to edit /etc/udev/rules.d/70-persistent-net-rules (not sure on the path), to get the network to be recognized as eth0, if you want.

---

### Post by strange_cathect on 2011-07-31
CharlesA,

Just to clarify...the "transplant" should work w/o problems? Even w/o editing fstab or reinstalling / ??

---

### Post by coffeecat on 2011-07-31
> **strange_cathect said:**
> 
Will I need to edit fstab or something?


No. You'll be OK. The only real issue is if you have installed a proprietary video driver and the card in the new machine is a different make. For example, the presence of the proprietary nvidia driver will cause problems with an ATI card and vice versa. If you uninstall the proprietary driver first you'll be fine because the system will detect what card you have on bootup and use the appropriate open source driver.

However, because your motherboard has died, booting into a GUI might be problematic if you are in this situation. If so, post back with more details.

---

### Post by CharlesA on 2011-07-31
> **strange_cathect said:**
> CharlesA,

Just to clarify...the "transplant" should work w/o problems? Even w/o editing fstab or reinstalling / ??

Should be fine. As coffeecat says, if you are using a different GPU on the new mobo, you might have problems booting into the GUI.

---

### Post by strange_cathect on 2011-07-31
Great, thanks everyone. The new machine should be very similar in the graphics department: Nvidia on both. I'll try it and see.

---

### Post by strange_cathect on 2011-07-31
Hey Coffeecat,

One last question about the graphics card. In my old machine I was using a Nvidia card. The new machine doesn't have a separate graphics card and it is Intel integrated.

Let's just say I put in the drives and fire it up, and the proprietary driver is wrong, how difficult is that to fix on the new machine? (I can't get the old one to even boot).

I could spend more $$ and get a machine with a Nvidia card, but money is a bit tight at the moment.

Thanks!

---

### Post by CharlesA on 2011-07-31
It should see the intel card fine. If not, I think you just remove the nvidia drivers and it *should* work.

---

### Post by quadproc on 2011-07-31
There might be a problem with fstab - depending on how you specify the drives, your new hardware might require different names for the drives.  If you use UUIDs to specify the drives then this should not be an issue, but if you use names such as /dev/sda then the new hardware might require different designators.

quadproc

---

### Post by zero244 on 2011-07-31
I would be interested how that comes out.

I have switched out video cards without problems, but have never brought a hard drive from a completely different computer and tried to boot off the drive.
Windows will balk big time if you try that, and just stop on boot up.

---

### Post by CharlesA on 2011-07-31
> **zero244 said:**
> 
Windows will balk big time if you try that, and just stop on boot up.

Linux is different.

---

### Post by coffeecat on 2011-08-01
> **CharlesA said:**
> Linux is different.

+1

@zero244, the behaviour of Windows when confronted with different hardware has absolutely nothing to do with Linux. The main reason why Windows balks at different hardware is to do with anti-piracy measures. I have often swapped Linux hard drives from one machine to another. The only issues are with proprietary video drivers and the network card designation that CharlesA mentions.

> **strange_cathect said:**
> One last question about the graphics card. In my old machine I was using a Nvidia card. The new machine doesn't have a separate graphics card and it is Intel integrated.

Let's just say I put in the drives and fire it up, and the proprietary driver is wrong, how difficult is that to fix on the new machine? (I can't get the old one to even boot).

I agree with CharlesA - try it and see. The worst that can happen is that the GUI fails to start and then you would need to boot into recovery mode and remove the nvidia driver and the xorg.conf file from the command line. The system will detect the Intel card while booting up and should load the appropriate driver. However, with the nvidia proprietary driver you have a small /etc/X11/xorg.conf file which references the nvidia driver. This could cause problems. If you do have problems, post back and someone can give you the terminal commands to disable the nvidia driver.

---

### Post by strange_cathect on 2011-08-01
I did uses UUIDs for all my drive partitions. So that should help me with fstab.

The computer will be here in five days. I'll post an update. And thanks again for all the advice and helpful suggestions.

---

### Post by zero244 on 2011-08-01
Hey guys I realize Linux is different than Windows.
I was just making the point that Windows definitely wont allow you to move a hard drive from a different computer and boot up.

And it has nothing to do with anti piracy, if that were the case you could just input a new registration code.
Instead you have to do a repair install to get Windows up and running again.

This may work but I suspect it will take some tweaking to get it running right.
I would  do a fresh install, I think in the long run you will have a better setup.

PS: By the way how old was the computer that got toasted.?

---

### Post by CharlesA on 2011-08-01
> **zero244 said:**
> Hey guys I realize Linux is different than Windows.
I was just making the point that Windows definitely wont allow you to move a hard drive from a different computer and boot up.


It depends on the hardware. I've moved a Windows 7 drive to a new machine without it totally flipping out before. It's mostly a driver thing, not a anti-piracy thing.

---

### Post by coffeecat on 2011-08-01
> **zero244 said:**
> And it has nothing to do with anti piracy, if that were the case you could just input a new registration code.

Actually, it is to do with anti-piracy. When you install Windows it assigns a number of points to various identifiable parts of the hardware and generates a unique activation code which, when you activate Windows, is sent to the Microsoft server. This activation code is based on a number of hardware characteristics (I believe 10) which allows you to make some changes to your hardware without re-activation. This product activation allows a certain amount of change over a period of time, but if too much change occurs over too short a time period, you have to re-activate Windows. This is when you may be required to phone Microsoft and convince them you are not doing something against the EULA. And best of luck to you if you ever find yourself in this situation. :wink:

Most of the hardware parameters - such as GPU, amount of RAM, processor serial number, and so on - score one point in this system. The MAC address of your network card scores 3 points, and this is why changing the motherboard is more likely than not to change the score too much and to send Windows into a tail spin.

I do not dispute that Windows is less tolerant than Linux with regard to drivers and changing hardware, but this tally and activation code system is the main reason that simply moving a hard drive from one machine (motherboard) to another can be a cause of Windows refusing to work. Windows is programmed to interpret the change of hardware as an attempt at piracy - hence the requirement to re-activate.

I think the transplant of Windows 7 that CharlesA mentions must have (fortuitously) come out just below the threshold for the score. @CharlesA, did you move any of the old hardware to the new machine, apart from the HD?

---

### Post by CharlesA on 2011-08-01
> **coffeecat said:**
> 
I think the transplant of Windows 7 that CharlesA mentions must have (fortuitously) come out just below the threshold for the score. @CharlesA, did you move any of the old hardware to the new machine, apart from the HD?

Nah just the hard drive. It wasn't being seen on the other PC and I wanted to see if the drive was good or not.

I think it triggered the "windows needs to be activated" thing, but it booted up to the desktop.

---

### Post by zero244 on 2011-08-01
If you swap out a motherboard with a different model or make Windows 99.9 times out of 100 will hardware fault and stop.
Windows can take peripheral changes but it goes into its does not compute mode on motherboard changes.
That has been my experience with every version of Windows, with the exception of Wiindows 7.
I haven't changed out a motherboard with Windows 7.

Before Windows can decide if the activation code is valid it has to boot up to a certain point.

Unlike Linux if you change the motherboard to one with a different chipset configuration Windows just cant handle it and requires a reinstall to get it working again.

If all it took was a call to MS that would be great, that never worked for me.
Microsoft would always give me a new regcode and tell me sorry you have to reinstall.

---

### Post by strange_cathect on 2011-08-10
UPDATE:

Ok, now that we got all that Windows stuff out of our system.

I promised that I would write and tell of my experiences with dropping old drives into a new machine. And.....it worked flawlessly. I did end up purchasing a similar video card (Nvidia). But I did not have to update a single thing or play with fstab. Worked right out of the box. 

Yay LINUX!!!!

---

### Post by zero244 on 2011-08-10
Thanks for the update....and its very good to know you can swap drives like that with Ubuntu.
Ive always assumed you had to do a fresh install to make such big changes.

---

