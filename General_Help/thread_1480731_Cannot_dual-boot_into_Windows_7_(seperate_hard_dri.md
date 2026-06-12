---
title: "Cannot dual-boot into Windows 7 (seperate hard drives)"
date: 2010-05-11
forum: General Help
---

### Post by Dragonbite on 2010-05-11
I know,.. "*is that such a bad thing?*" :P

My system has 2 hard drives and I am trying to set them up as dual-boot.  
/dev/sda = Linux hard drive
/dev/sdb = Windows 7 hard drive

The system boots to /dev/sda (Linux) and Grub includes a listing for Windows 7 (on /dev/sdb1).

When I select the Windows 7 option, I get the error message:> error: no such device: fcd00f34d00ef524.
error: hd1,1 cannot get C/H/S values.

Press any key to continue...

Now, when Windows was installed, it was set as the Master drive, and then it was moved to the second place when I installed Lucid on the (now) first hard drive.

I'm not sure if this error is coming from Windows or Grub.

Since it is Grub2, I'm not sure where to lookup the list.  I know with Grub it was in /boot/grub/menu.lst, and now I don't know.

---

### Post by byStanderone on 2010-05-11
...am not sure if there is already a workaround bout this win7 issue with ubuntu...it is an mbr related, they say. perhaps you can focus on that topic.

---

### Post by byStanderone on 2010-05-13
...came across this thread, seems to have bearing to your problem:
[http://ubuntuforums.org/showthread.php?t=1481841](http://ubuntuforums.org/showthread.php?t=1481841)

---

### Post by confused57 on 2010-05-13
I don't know if you've found a solution or not, but you might want to enter your bios setup and check the status of your slave drive controller, it might be set to "off" by default, as I've experienced on my Dell.

---

### Post by Dragonbite on 2010-05-14
> **byStanderone said:**
> ...came across this thread, seems to have bearing to your problem:
[http://ubuntuforums.org/showthread.php?t=1481841](http://ubuntuforums.org/showthread.php?t=1481841)

Thanks for the link! I think my problem is slightly different but I'll comb through it and give it a whirl.

I know the hard drive is set to boot because if I plug it into the Master slot of the hard drive cable, it boots with no problems.

> **confused57 said:**
> I don't know if you've found a solution or not, but you might want to enter your bios setup and check the status of your slave drive controller, it might be set to "off" by default, as I've experienced on my Dell.

No, I haven't found a solution yet.

I am suspicious of the BIOS for the system because when I am looking through the hard drive selection I only see the Master hard disk, not the slave.

I wasn't sure if this was going to be an issue since the one it can see (/dev/sda) is the Ubuntu with Grub and from there I try and repoint it to the other hard drive (/dev/sdb)

If it is a case of the slave has to be seen as a slave (show up in the BIOS), how can I manage that?  Oh, and it is a Dell (Dimension 4600?)

---

### Post by Mark Phelps on 2010-05-14
> **Dragonbite said:**
>  I know the hard drive is set to boot because if I plug it into the Master slot of the hard drive cable, it boots with no problems.
Are these PATA drives (the ones with lots of little pins on the back)?

If so, it sounds like you've got your drive jumpered to Cable Select -- which is OK if BOTH drives are jumpered like that.

If they're not BOTH set to Cable Select, then one has to be jumpered as Master, and the other as Slave -- it's not a BIOS setting, it's a jumper on the drive.

If these are SATA drives, then there are no jumpers and none of the above applies ...

---

### Post by Dragonbite on 2010-05-14
> **Mark Phelps said:**
> Are these PATA drives (the ones with lots of little pins on the back)?

If so, it sounds like you've got your drive jumpered to Cable Select -- which is OK if BOTH drives are jumpered like that.

If they're not BOTH set to Cable Select, then one has to be jumpered as Master, and the other as Slave -- it's not a BIOS setting, it's a jumper on the drive.

If these are SATA drives, then there are no jumpers and none of the above applies ...

Yes, these are PATA (lots of bendable pins on the back)

IIRC, when I started this project both hard drives were set to cable select and it didn't work.

Currently I set one to slave but didn't change the other one (because the diagram of where the jumper has to go is burined underneath the hard drive case for fitting it in the box and I've been too lazy, so far, to take it out to look.

That was one of the things I was thinking of, though.  I think I held off originally because I was moving them back and forth on the cable for installation (Win 7 installed without the 2nd hard drive, then Ubuntu installed with Win 7 plugged into the slave slot).

Ok, so I'll give setting the jumpers to master/slave a try.

---

### Post by confused57 on 2010-05-14
Mark Phelps is probably right that it's the jumper setting for the error you're getting.

The computer I had was a Dell Dimension 4550, both drives set to Cable Select, which was initially getting a grub error 21 when trying to boot Windows on the slave drive, until I changed the setting in bios to "auto" for the slave drive controller.  FYI, in case you get error 21 after changing the jumper on the drive.

---

### Post by Dragonbite on 2010-05-14
Now I can't wait to get home and give this a try!  Once I can get it dual-booting then it is just a case of moving the users' files and setting over and the project is DONE! (and I can scratch another one off my list..)

---

### Post by Dragonbite on 2010-05-14
Changing the jumpers to master/slave and the BIOS setting for the primary Slave as "Auto" did the trick!

The BIOS part I needed to dig a little deeper than I had.

So thanks guys, for all of your help.  I'll be moving this computer into the family room this weekend (and informing them the close button is on the left side now ;) )

---

### Post by confused57 on 2010-05-14
I could only speculate based on my experience with the 4550 for what your boot problem was, glad you were able to get it working.  If you ever remove the secondary drive, you'll need to set the controller back to "off", as I found out.

---

### Post by Dragonbite on 2010-05-16
> **confused57 said:**
> I could only speculate based on my experience with the 4550 for what your boot problem was, glad you were able to get it working.  If you ever remove the secondary drive, you'll need to set the controller back to "off", as I found out.

In my BIOS, the slave driver is listed as "auto", so I'm not sure whether that will make a difference or not.  If I think of it later, maybe I'll try that out.  Thanks for the heads-up.

---

