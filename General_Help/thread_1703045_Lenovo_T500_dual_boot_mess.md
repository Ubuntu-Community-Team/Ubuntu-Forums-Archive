---
title: "Lenovo T500 dual boot mess"
date: 2011-03-08
forum: General Help
---

### Post by sea_dawg on 2011-03-08
I have made a complete mess of a Lenovo T500 Win 7 and Ubuntu dual boot system.  I won't go into a long story of how and why I did what I did but jump to the final mess I have.  Win 7 is still on the machine it's original partition.  Lenovo's recovery partition is still there.  The linux swap partition is still there.  The partition Ubuntu used to live on is still there but through my own errors unallocated. 

GRUB is broken and reports this message on boot.

error: unknown filesystem.
grub rescue>

I can boot from the Live USB and see what remains after the mess I've made.  Attempts to reinstall Ubuntu onto it's original partition fail because the installer cannot see it.  It wants to put Ubuntu into the Win7 partition.

I cannot use the ThinkVantage button or F11 to access Lenovo Rescue and Recovery to restore the machine to factory settings and then reinstall Ubuntu. 

I cannot use the methods described in other threads on this forum to fix a broken GRUB requiring a Win7 rescue DVD because I don't have one.  I have come to trust Lenovo's hidden partition with rescue and recovery files to restore the machine to factory state. (This is my 3rd Lenovo, but my first Win7)

All important files have been backed up, recovery is not necessary.

In the end I need to be able to boot into Win 7.  This is a work computer, others use it from time to time and don't want to use Ubuntu.  So wiping the entire HD and running Ubuntu is not an option.  I would like to leave Lenovo's hidden partitions intact as they are usually a good way to recover from a mess.   I would very much like to have Ubuntu back as I prefer it to Win 7, Vista and XP.

I can boot from the Live USB into Ubuntu 10.10 and see that the Win7 OS and Lenovo hidden partitions are still there.  Attempts to install a fresh copy of Ubuntu 10.10 are not going well because the installer cannot find the partition Ubuntu was first on. 

Is it possible to
1 - fix or remove GRUB
2 - use GParted to repair my damage to Ubuntu's partition so that Ubuntu's installer recognizes it
3 - reinstall Ubuntu

My unskilled messing about has left my HD partitioned as follows as reported by GParted
Partition...........File System.......Label....................Size............Used..............Free..............Flags
/dev/sda1.........ntfs...................SYSTEM_DRV.....1.17GiB.......679.15MiB......520.85MiB.....boot
/dev/sda2.........ntfs...................Windows7_OS......143.58GiB....84.79GiB........58.79GiB......<none>
/dev/sda3.........extended...........<no label>.............143.58GiB....------...............143.58GiB....<none>
       unallocated...unallocated........<no label>............137.71GiB....------................-------............<none>
    /dev/sda5.....linux-swap.........<no label>.............5.87GiB.......------................------.............<none>
/dev/sda4.........ntfs ..................Lenovo_Recovery..9.77GiB.......7.40GiB..........2.37GiB........<none>
unallocated.......unallocated........<no lable>.............1.34MiB.......-------...............-------............<none>

---

### Post by blueridgedog on 2011-03-08
Welcome to the forums.  

I would boot on the LiveUSB and use gparted to create a new partition in the unallocated space within the extended partition, formatting it ext3.  Sda3 is an extended partition of 143 gig.  It has only two partitions within it, sda4 - your recovery and sda5, swap.  

After making the new partition, which should then be sda6, I would install Ubuntu to the hard drive, telling it to use sda6 as / and the existing swap as swap.  Verify that it is indeed sda6, but it should be the only ext3 partition you have.

It should re-install grub to the MBR and that should boot each OS.  If the Windows7 partition is not damaged and can boot the OS, is should work.

I am curious as to how the recovery partition ended up in the extended partition...seems odd.

---

### Post by Hedgehog1 on 2011-03-08
> I am curious as to how the recovery partition ended up in the extended partition...seems odd.

/dev/sda4 in not inside the extended partition.  It is a primary parition at the end of the disk.  Still looks really weird though, huh?

```

/dev/sda1 ntfs  SYSTEM_DRV 1.17GiB boot
/dev/sda2 ntfs  Windows7_OS 143.58GiB
[B][COLOR="Red"]/dev/sda3 extended 143.58GiB
    *_[COLOR="DeepSkyBlue"]unallocated 137.71Gig[/COLOR]_*
    /dev/sda5 linux-swap 5.87GiB[/COLOR][/B]
/dev/sda4 ntfs recovery 
```

I think I see what has happened here, and how to fix it.

We want to make your drive look like this:

```

/dev/sda1 ntfs  SYSTEM_DRV 1.17GiB boot
/dev/sda2 ntfs  Windows7_OS 143.58GiB
[B][COLOR="Red"]/dev/sda3 extended 143.58GiB
    _*[COLOR="DeepSkyBlue"]/dev/sda5 ext4 137.71Gig[/COLOR]_*
    /dev/sda_*[COLOR="DeepSkyBlue"]6[/COLOR]*_ linux-swap 5.87GiB[/COLOR][/B]
/dev/sda4 ntfs recovery 
```

**sea_dawg**, this means a manual reinstall to do the above.  Do you need guidance on how to do this?  Do a manual Ubuntu install, remove the current sda5 and make a new sda5 and sda6?

Then you will be able to grub into Win7 or Ubuntu.

***The Hedge***

:KS

p.s. Please be sure to make a  Win7 rescue CD from Win7 once you are operational again!

---

### Post by blueridgedog on 2011-03-09
> **Hedgehog1 said:**
> /dev/sda4 in not inside the extended partition.  It is a primary parition at the end of the disk.  Still looks really weird though, huh?

True, I did not catch that, but 3 is the extended (you can only have four primary).  Either way, a new partition and a manual install should work.

---

### Post by sea_dawg on 2011-03-09
Blueridgedog and Hedgehog, 

Thank you for the quick response and excellent help.

Hedge is correct, sda4 is the Lenovo recover partition and it is NOT in the extended partition.  

If I understand both of you correctly I need to:
1 - Use GParted to format the uallocated 137.7 GiB space on sda3 to ext3

2 - The system will now recognize this as sda5 and the linux-swap as sda6, both within sda3 extended partition.  Will I be able to use the GUI GParted? Or will I need to use the command line version?

3 - Reinstall Ubuntu 10.10 which will have the benefit of fixing the MBR and GRUB making both OS available to me.

Hedge suggests a manual install.  Is this the done by selecting "Specify Partitions Manually" choice on the "Allocate Drive Space" page of the install routine?  Or by some other method?

In either case I will need guidance.  I've made enough of a mess so far I want to be very careful.

Thank you.

---

### Post by Hedgehog1 on 2011-03-09
> **sea_dawg said:**
> 1 - Use GParted to format the uallocated 137.7 GiB space on sda3 to **[COLOR=red]ext3[/COLOR]** 
 
sea_dawg,
 
That will all work. Only curiosity is the ext3 vs ext4. But you got it.
 
> **sea_dawg said:**
> Hedge suggests a manual install. Is this the done by selecting "Specify Partitions Manually" choice on the "Allocate Drive Space" page of the install routine? 
 
If you have already setup the two paritions in gparted, you just need to indicate the '/' goes in sda5 and the 'swap' in sda6 in the "Specify Partitions Manually".
 
***The Hedge***

---

### Post by sea_dawg on 2011-03-09
Hedge,

Once again thank you for the quick response!

I'm understandably nervous about this having already made quite a mess.  When I run GParted GUI I get the partition map.  At that point I :

1 - Select the 137.71GiB unallocated space
2 - Choose menu "Partition\New" and am presented with a dialog
3 - In that dialog I manipulate the sliders to max.  "Create as:" Logical Partition.  "File system:" ext3

Should I enter a label?

Is this the correct action to create the required partition for re-install of Ubuntu?

Thank you for your assitance
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by blueridgedog on 2011-03-09
> **Hedgehog1 said:**
> sea_dawg,
That will all work. Only curiosity is the ext3 vs ext4. But you got it.


Sorry, showing my age.  Ext4 will be just fine.

---

### Post by blueridgedog on 2011-03-09
> **sea_dawg said:**
> 
Is this the correct action to create the required partition for re-install of Ubuntu?


Yes.  After it is created, you can install to it, alternatively you can create it in the install, but the end result will be the same.  Just make certain when you do the install that you select it to be mounted as / and do not create or format any other partition.

---

### Post by sea_dawg on 2011-03-09
I think I'm ready to install Ubuntu.

The HD partitions now look like the attached screenshot of GParted.

In the install I have selected "Specify Partitions Manually (advanced)"

Unfortunately it is less than clear what to do next.  I have hilighted /dev/sda5 in the dialog as indicated by the 2nd screenshot.

Is that all there is to it?  Hit the "Install Now" button and let it go?

---

### Post by blueridgedog on 2011-03-09
You need to set the  mount point of your new partition as root or /.

---

### Post by sea_dawg on 2011-03-09
Ok.  I don't see that as an option.

---

### Post by Hedgehog1 on 2011-03-09
It is a Non-Obvious UI thing.
 
With the sda5 parition highlighted, press the [Change] button. There is a pull down control, and one of the options in the control is '/'.
 
See how easy this isn't? OK - it is really easy after the Third install. Honest.
 
***The Hedge***

:KS

---

### Post by sea_dawg on 2011-03-10
Thank you both for your excellent help and patience!  

I can now boot into either Ubuntu or Win 7.

---

### Post by blueridgedog on 2011-03-11
Good.  I hope you can keep the dual boot working.  With the work laptop arrangement.

---

