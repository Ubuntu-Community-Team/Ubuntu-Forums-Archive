---
title: "can't mount Windows vista in ubuntu 10.04"
date: 2011-02-27
forum: General Help
---

### Post by ck07 on 2011-02-27
p { margin-bottom: 0.08in; }  Hello Everyone,
 

 I have installed Ubuntu 10.04 LTS in Windows Vista. Yesterday, I have done a update of “Abobe 9” in Windows Vista, and restart my PC. As usual, at the Grub menu, I can found the option “Windows Recovery Environment(loader)(on /dev/sda1)”, and I clicked it to boot my “Windows Vista”, but this time it did start windows, instead the PC restart again and show me the Grub start menu again.   
 And when I logged in Ubuntu, I can't mount the disk partition of Windows Vista, i.e., when I click the windows system disk in the file browser, a message error displayed “Unable to mount SW_Preload Error mounting: mount exited with exit code 2: ”
 I have downloaded the script “boot_info_script055,sh” and executed it, here the file “results.txt”, attached in the message.

 

Can anyone help me ?
 

 Thanks in advance,
 ck

---

### Post by amsterdamharu on 2011-02-27
I can't find anything funny in the boot info script results, what happens when you manually mount your Windows partition?

```
sudo mount -t ntfs /dev/sda1 /mnt
```


To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by ck07 on 2011-02-27
Hi amsterdamharu,
 
 Thanks for your reply. I execute the command, several directories are  appeared in /mnt. I have made a screenshot. Could you please tell me  what I should do next ? Because I still didn't discover any windows  files in /mnt.
 
 By the way, I forget to mention before. In ubuntu, I can't open my Windows  disk. The error message is "Unable to mount SW_Preload Error mounting:  mount exited with exit code 2: ". Where "SW_Preload" is my windows disk  name.  
 
 ck

---

### Post by ck07 on 2011-02-27
Hi amsterdamharu,
 
 Again, I have execute the command

#sudo fdisk -l

The result is:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7504fa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       23288   185520700    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29127       30402    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           23288       29127    46899201    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           23288       28882    44933120   83  Linux
/dev/sda6           28882       29127     1965056   82  Linux swap / Solaris

Partition table entries are not in disk order


Do you find anything strange here ?
 
 ck

---

### Post by amsterdamharu on 2011-02-27
Strange that it sda1 doesn't mount in nautilus (the file manger) but gives no warning when mounting it at the commandline.

I don't see anything wrong there, there is a Windows directory and boot info script and grub detected a bootable Windows (although it's a recovery one).

Maybe someone with more knowledge about Windows can fix this or boot up from Windows CD and choose restore, after you might have to re install grub2 from live CD but that could solve your problem.

---

### Post by ck07 on 2011-02-27
Hi amsterd,

Thanks for your reply. Actually, I can mount /dev/sda1 and /dev/sda3 but not /dev/sda2
I have tried the command

sudo mount -t ntfs /dev/sda2 /mnt

And there is nothing in /mnt . Any way, thank you. 
I am appreciated if someone can help me. Because I have very important data in /dev/sda2.

Best,
ck

---

### Post by oldfred on 2011-02-27
Boot script also could not mount sda2.

> /home/ck/Downloads/boot_info_script055.sh: line 892:  4653 Segmentation fault      ntfs-3g -o ro $part "$mountname" 2>> $Mount_Error

Ubuntu/gparted will not mount NTFS partitions that need chkdsk run. That is to prevent further damage that then chkdsk might not be able to repair. I would try running chkdsk on sda2 first. 

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by ck07 on 2011-02-27
Hi oldfred,

Thanks for your answer. But the another problem is that I can not start Windows Vista in Grub menu. In other words, when I restart my PC, I choose the option "Windows Recovery Environment (loader) (on /dev/sda1)", then my PC restart again and bring me to the grub menu, so there is no way for to run Windows Vista. Do you know another way to start Windows in Ubuntu ?

---

### Post by oldfred on 2011-02-27
That is why I suggested the neosmart site. Those downloads are small and just a repair CD that you can use to fix windows.

---

### Post by ck07 on 2011-02-27
Thanks oldfre. Now I see. I will do that.

---

