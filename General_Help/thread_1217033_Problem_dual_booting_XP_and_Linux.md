---
title: "Problem dual booting XP and Linux"
date: 2009-07-19
forum: General Help
---

### Post by Harout tuoraH on 2009-07-19
Hi, I'm new here, and I'm not sure if this is the right category to put this in, but lets see if you can help me. 

So I swaped my old hard drive with another one that has an 80 gb xp partition. I thought I would give Linux a try on this new hard drive. I split that 80 into 2 40's, and sucessfully installed ubuntu 9.04 on the free 40 gb partition. Everything was fine with linux, but when I tried to run xp, my computer restarted. So after no success with xp, I decided to reformat the xp partition. I popped the xp disc in, deleted the xp partition, and tried to put xp on it. After a few minutes, I get the bsod, and have to manually shut down the computer. When I turn it back on, delete xp partition again, and try to install xp again, same thing happens. 

When I turn the computer on without the xp disc, windows starts to load, but to no success, it restarts before loading completley, and continues to do this in an endless loop. The option to choose linux at startup was not available as it was before.
So I had to restore the grub with the live disc and linux worked fine, but I was basically back to when I just installed linux.

I would just delete the windows partition and add it on to the linux partition instead of trying to figure this out, but there are some programs that I need to use which wont work on wine.

If anyone could help me out as to why I cant install xp on the second partition, that would be great.

Any help is appreciated.

---

### Post by DeMus on 2009-07-19
> **Harout tuoraH said:**
> Hi, I'm new here, and I'm not sure if this is the right category to put this in, but lets see if you can help me. 

So I swaped my old hard drive with another one that has an 80 gb xp partition. I thought I would give Linux a try on this new hard drive. I split that 80 into 2 40's, and sucessfully installed ubuntu 9.04 on the free 40 gb partition. Everything was fine with linux, but when I tried to run xp, my computer restarted. So after no success with xp, I decided to reformat the xp partition. I popped the xp disc in, deleted the xp partition, and tried to put xp on it. After a few minutes, I get the bsod, and have to manually shut down the computer. When I turn it back on, delete xp partition again, and try to install xp again, same thing happens. 

When I turn the computer on without the xp disc, windows starts to load, but to no success, it restarts before loading completley, and continues to do this in an endless loop. The option to choose linux at startup was not available as it was before.
So I had to restore the grub with the live disc and linux worked fine, but I was basically back to when I just installed linux.

I would just delete the windows partition and add it on to the linux partition instead of trying to figure this out, but there are some programs that I need to use which wont work on wine.

If anyone could help me out as to why I cant install xp on the second partition, that would be great.

Any help is appreciated.

Are you familiar enough with Ubuntu to do some "heavy" stuff? Or is it better to do it the Windows way? Let's do that, must be easier for you.

Boot from your Windows CD.

Let it go until it says where you want to install it. You will have a list of partitions which you can delete all. The code for that is to place the blue line on the partition using the mouse keys, type D Enter L (if I am not mistaken, must have been ages ago that I did this)

Then create a new partition and make it 40GB (40000MB). Partition it the NTFS way and continue the installation.
This leaves you with a 40GB free space on your disk.

After installation boot into Windows and see if it works.

Then boot using your Ubuntu CD
Choose install on harddisk
At step 4 choose the free disk space as the place to install Ubuntu, continue till the end.
Take out the disk and reboot.

Now you will see a menu (Grub) to choose which OS you want to use. Try Windows to see if it still works. As soon as it is booted, choose Start > Restart to get out of Windows.
Then you will see Grub again and now you choose Ubuntu. This should boot without problems also.

If this does not work you could have a hard disk problem, a CD problem (either Windows or Ubuntu) or a CD drive problem.

This is the way to install a dual boot: first Windows, then Ubuntu so Grub is installed the right way.
Try it, hope it works for you.

---

### Post by Harout tuoraH on 2009-07-19
> **DeMus said:**
> Are you familiar enough with Ubuntu to do some "heavy" stuff? Or is it better to do it the Windows way? Let's do that, must be easier for you.

Boot from your Windows CD.

Let it go until it says where you want to install it. You will have a list of partitions which you can delete all. The code for that is to place the blue line on the partition using the mouse keys, type D Enter L (if I am not mistaken, must have been ages ago that I did this)

Then create a new partition and make it 40GB (40000MB). Partition it the NTFS way and continue the installation.
This leaves you with a 40GB free space on your disk.

After installation boot into Windows and see if it works.

Then boot using your Ubuntu CD
Choose install on harddisk
At step 4 choose the free disk space as the place to install Ubuntu, continue till the end.
Take out the disk and reboot.

Now you will see a menu (Grub) to choose which OS you want to use. Try Windows to see if it still works. As soon as it is booted, choose Start > Restart to get out of Windows.
Then you will see Grub again and now you choose Ubuntu. This should boot without problems also.

If this does not work you could have a hard disk problem, a CD problem (either Windows or Ubuntu) or a CD drive problem.

This is the way to install a dual boot: first Windows, then Ubuntu so Grub is installed the right way.
Try it, hope it works for you.

So I should delete both partitions, and try to do it again by installing windows first?

 The problem with that is I have data on my linux partition that I cannot lose, and I do not have a thumb drive large enough to hold it all while I format my whole hard drive. I have been sitting here with only linux working for about a month now, so the data on it has added up. It also contains a lot of data from the windows partition that I have deleted because I mounted that drive in linux, and copied everything that was important when I figured out xp wouldn't work.

Another thing is I had windows first, and after I installed ubuntu, windows wouldn't work. So I'm not so sure it will work if I try the same thing again. I don't think the drive is bad either. XP worked fine before linux, and linux worked fine after I installed it. For some reason, they won't work together.

Thanks for the help, but I'm looking for an option without having to format my linux partition. But if all else fails, that would be my only option left.

---

### Post by merlinus on 2009-07-19
Post results of

```
sudo fdisk -l
```

---

### Post by Harout tuoraH on 2009-07-19
> **merlinus said:**
> Post results of

```
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4627    37166346    7  HPFS/NTFS
/dev/sda2            4628        9726    40957717+   f  W95 Ext'd (LBA)
/dev/sda5            4628        9247    37110118+  83  Linux
/dev/sda6            9248        9726     3847536   82  Linux swap / Solaris

---

### Post by merlinus on 2009-07-19
It certainly would seem that you could reinstall xp to sda1, which is formatted as ntfs.  I wonder if your xp disk has gotten corrupted?

Can you try it on another machine to ensure that it is still good?

There might be some useful info here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Harout tuoraH on 2009-07-19
> **merlinus said:**
> It certainly would seem that you could reinstall xp to sda1, which is formatted as ntfs.  I wonder if your xp disk has gotten corrupted?

Can you try it on another machine to ensure that it is still good?

There might be some useful info here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


That website is actually what I followed to do it, but as I said, after deleting the xp partition, and trying to install xp on it, I got the bsod, and thats where I stopped on that website. 

The xp disc is fine, and has worked on another computer after I have tried it on mine.

---

### Post by merlinus on 2009-07-19
Perhaps you have already done this, but have you tried deleting sda1 and leaving it as unallocated, and then trying to install xp into that space?

I know this will wipe out grub, but you already know how to restore it.

---

### Post by Harout tuoraH on 2009-07-19
> **merlinus said:**
> Perhaps you have already done this, but have you tried deleting sda1 and leaving it as unallocated, and then trying to install xp into that space?

I know this will wipe out grub, but you already know how to restore it.

Yes, that is what I did. Sorry if I didn't explain it clearly before, but I deleted the xp partition, which is sda 1, and then tried installing xp into that 40 gb of free space.

So since there is still an ntfs partition, I am assuming the xp disc left some trace of xp before I got the bsod. I just restarted my computer, and chose xp on the menu. It started loading, but I got the bsod after about 5 seconds. I think I will try to delete the partition and install xp on it one more time right now to make sure it doesn't work. I will get back to you with the results as soon as I can.

But keep coming with ideas, becuase I am pretty sure it wont work.

---

### Post by x33a on 2009-07-19
Is there any chance that the xp partition has some bad sectors, which are preventing the installation?

or try another xp cd as merlinus said.

---

### Post by merlinus on 2009-07-19
Since you asked for ideas, what about your cd drive having defects?  And if you can boot from a usb flashdrive, copy the xp install cd to it on another computer and try that on this one.

---

### Post by Harout tuoraH on 2009-07-19
[FONT=Arial][SIZE=2]The cd drive works fine. All my other discs work on it. How ever, there might be a chance that the xp partition has bad sectors in it.

I just tried to delete the xp partition, and put xp on it again. XP started installing, and finished setup, it then restarted the computer, and started loading xp, after about 5 seconds, the bsod [/SIZE][/FONT][FONT=Arial][SIZE=2]came up.
[/SIZE][/FONT]**[FONT=Times New Roman][SIZE=2][FONT=Arial][SIZE=2]I got a Stop 0x0000007B error at the botom of the bsod, don't know if that helps.[/SIZE][/FONT][/SIZE][/FONT]**

I think I am going to try putting ubuntu on what it currently the xp partition to check If I have bad sectors.

---

### Post by Harout tuoraH on 2009-07-19
So I ended up trying the first Idea posted. I created a fat32 partition, put all important data on it, then I deleted both the linux and windows partitions.

All I had left was a 40 gb fat32 partition, and 40 gb of free space. I thought windows would work this time, but again, I got the bsod after a little while. 

I don't know why, but nothing I do seems to work. Ubuntu works fine, after windows failed, I installed ubuntu again. 

The disc is working because it has worked on another computer recently. I checked the hard drive for bad sectors, and its fine.

Any other ideas on why I get the bsod trying to install xp?

Thanks for all the replies so far.

---

