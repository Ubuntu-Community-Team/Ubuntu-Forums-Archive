---
title: "Need to remove Ubuntu"
date: 2011-05-20
forum: General Help
---

### Post by nikus@rocketmail.com on 2011-05-20
Need help removing Ubuntu from my HP desktop with Vista,  I had downloaded 11.04 to run side by side, it had reset my monitor settings which disabled my monitor, then I downloaded 10.10 to replace it, now I cannot get into safe mode or get Vista to come up unless I use the 10.10 install disk to bring my system up. Without the 10.10 install disk the system boots into Ubuntu without giving me a choice.   If it wasn't for all the documents and records on Vista I wouldn't care, but as it is I need to somehow delete Ubuntu and get Vista working again.

---

### Post by Mr. Shannon on 2011-05-21
There are several ways to do this.  To answer your question I need to know what you want to do with the partition you currently have Ubuntu installed to.  Let us know what you wish to do so we can either guide you in restoring the Windows boot loader or fixing grub.

---

### Post by wildmanne39 on 2011-05-21
> **nikus@rocketmail.com said:**
> Need help removing Ubuntu from my HP desktop with Vista,  I had downloaded 11.04 to run side by side, it had reset my monitor settings which disabled my monitor, then I downloaded 10.10 to replace it, now I cannot get into safe mode or get Vista to come up unless I use the 10.10 install disk to bring my system up. Without the 10.10 install disk the system boots into Ubuntu without giving me a choice.   If it wasn't for all the documents and records on Vista I wouldn't care, but as it is I need to somehow delete Ubuntu and get Vista working again.
HI this link should do it. This will help also if you deciede to fix ubuntu. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by Rasa1111 on 2011-05-21
> Without the 10.10 install disk the system boots into Ubuntu without  giving me a choice.   If it wasn't for all the documents and records on  Vista I wouldn't care,

You can easily access the files on the vista side from within Ubuntu. 
(if that's your main concern). 

Just find the vista file system (however many GB's it is) in your "Places" menu.
So if the vista partition is, for example 200GB's... 
In your "Places" menu, you would see a "200 GB File System"

Just click that and open it up..
and there are all the files from Vista.
(if you haven't deleted them, of course)

Good luck.

---

### Post by kirill578 on 2011-05-21
> **nikus@rocketmail.com said:**
> Need help removing Ubuntu from my HP desktop with Vista,  I had downloaded 11.04 to run side by side, it had reset my monitor settings which disabled my monitor, then I downloaded 10.10 to replace it, now I cannot get into safe mode or get Vista to come up unless I use the 10.10 install disk to bring my system up. Without the 10.10 install disk the system boots into Ubuntu without giving me a choice.   If it wasn't for all the documents and records on Vista I wouldn't care, but as it is I need to somehow delete Ubuntu and get Vista working again.

I had the same problem, you should run the installtion of ubuntu 11.04 on "nomode"
if you you want to access you vista, just insert vista installation cd and follow this guide 
[http://www.youtube.com/watch?v=fMwfWP2ahyw](http://www.youtube.com/watch?v=fMwfWP2ahyw)

However you won't be able to access  your Ubuntu unless you reinstall GRUB menu

---

### Post by nikus@rocketmail.com on 2011-05-21
This is the listing of the partitions, I don't see /dev/sbd, I don't know for sure which is vista or ubuntu, and I've never deleted a partion so I'm gun shy on how to safely do this without damaging vista, I want to put the system back to the pre-ubuntu state and just remove the partitions I created.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b76cf6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   161463783    80731860+   7  HPFS/NTFS
/dev/sda2       464246370   488392064    12072847+   7  HPFS/NTFS
/dev/sda3       204656638   464244735   129794049    5  Extended
/dev/sda5       460320768   464244735     1961984   82  Linux swap / Solaris
/dev/sda6       204656640   287662079    41502720   83  Linux
/dev/sda7       287664128   291291135     1813504   82  Linux swap / Solaris
/dev/sda8       291293184   453337087    81021952   83  Linux
/dev/sda9       453339136   460310527     3485696   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by Mr. Shannon on 2011-05-21
I'm trying to decipher that information but since it's not in order it is very confusing.  Could you give us a screenshot of **gparted**.  You can either use the installed Ubuntu or the live CD.  Thanks!

---

### Post by nikus@rocketmail.com on 2011-05-21
Trying to get screen shot of gparted

---

### Post by matt_symes on 2011-05-21
Hi

@nikus

If that is your real e-mail address, do yourself a favour and ask the forums staff to change your user name before some bot scrapes it and you get inundated with spam. 

Kind regards

---

### Post by Lateralis on 2011-05-21
It looks like you might have three different installations of Linux there, alongside your Vista installation, which I'm guessing is on /dev/sda1.  

When you restart your system, hold down the shift key - that should bring up the grub menu.  You may find a listing in there for Windows Vista.  If not, boot into Ubuntu, download the Bootinfo script from the link in my signature and follow the instructions.  Post the results between *code *tags and we'll see what we can do to help. =)

---

### Post by Rasa1111 on 2011-05-21
> **nikus@rocketmail.com said:**
> Trying to get screen shot of gparted

Press the "Prt/Scr" button on your keyboard. 
That will screenshot your whole desk.

Or press Alt+Prt/Sc to take a shot of just the current (gparted) window.

---

### Post by Mr. Shannon on 2011-05-21
I don't know why you have two NTFS files systems but I am going to assume that those are part of your windows instalation.  **Warning:** the following steps will remove all partitions and operating systems exept for the two NTFS file systems that I am assumng Windows is on.  In other words these steps will completely remove any operating system except for Windows.

1. First make sure you have burned any Vista bootloader recovery media you may need from this site [[COLOR="Blue"]http://neosmart.net/blog/2008/how-to-repair-the-windows-vista-bootloader/[/COLOR]]("http://neosmart.net/blog/2008/how-to-repair-the-windows-vista-bootloader/").

2. Backup your files from you windows partition as there is always a possibility of data loss when resizing partitions.  You can access these files by using the method given in post #4.

3. Use gparted on your live CD to delete all the Linux partitions.  Thats all of them except for /dev/sda1 and /dev/sda2 in your case.

4. Use the instructions [[COLOR="blue"]here[/COLOR]]("http://neosmart.net/blog/2008/how-to-repair-the-windows-vista-bootloader/") to repair the windows boot loader.

5. Boot into windows and defrag twice and then use the instructions [[COLOR="Blue"]here[/COLOR]]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") to reclaim the hardrive for your windows installation.  Note: I am not sure if this is the correct way to resize a windows partition that you are currently using so if I am wrong will someone please correct me.  Another (safer) option would be to format the blank space as a windows compatible partition and use it as a separate drive in windows.

A word of caution, I have never attempted to recover a windows boot loader or resize a windows partition so use the instructions above at your own risk.

---

### Post by Thewhistlingwind on 2011-05-21
Press shift at BIOS screen and hold it. Don't stop until you boot into something. If you see the words "loading grub" instead, don't stop holding until you get a menu of operating system selections, choose vista from the list.

---

### Post by nikus@rocketmail.com on 2011-05-21
Sorry for not replying, my monitor will not come on, only blinks, so until I get that to work I'm at a dead end

---

### Post by wildmanne39 on 2011-05-21
> **nikus@rocketmail.com said:**
> This is the listing of the partitions, I don't see /dev/sbd, I don't know for sure which is vista or ubuntu, and I've never deleted a partion so I'm gun shy on how to safely do this without damaging vista, I want to put the system back to the pre-ubuntu state and just remove the partitions I created.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b76cf6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   161463783    80731860+   7  HPFS/NTFS
/dev/sda2       464246370   488392064    12072847+   7  HPFS/NTFS
/dev/sda3       204656638   464244735   129794049    5  Extended
/dev/sda5       460320768   464244735     1961984   82  Linux swap / Solaris
/dev/sda6       204656640   287662079    41502720   83  Linux
/dev/sda7       287664128   291291135     1813504   82  Linux swap / Solaris
/dev/sda8       291293184   453337087    81021952   83  Linux
/dev/sda9       453339136   460310527     3485696   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$Hi, yuo do have a mess there, the windows partition is the ones marked with hpfs and ntfs.

---

### Post by nikus@rocketmail.com on 2011-05-21
That is what I thought, but wasn't sure, I am still not able to get my monitor to work, when I get it to work I will delete the Ubuntu partitions.  Thanks

---

### Post by wildmanne39 on 2011-05-21
> **nikus@rocketmail.com said:**
> That is what I thought, but wasn't sure, I am still not able to get my monitor to work, when I get it to work I will delete the Ubuntu partitions.  Thanks

your welcome.):P

---

### Post by nikus@rocketmail.com on 2011-05-22
I think I may have lost the baby,,  no boot, no beep, no bios.. nothing.......ultimate boot CD doesn't even work.

any ideas before I nuke the whole thing??

---

### Post by Mr. Shannon on 2011-05-23
Have you tried the Ubuntu Live CD?

---

### Post by nikus@rocketmail.com on 2011-05-23
yes I've tried a live CD, nothing..  It sounds like it is reading the CD, but I have no display on my monitor, and its not the monitor,  I get no beep on booting up,  I've reset the bios, still nothing.  
Once in a while I'll get a flash on the monitor of whatever stage its at,  but it last a second and then back to black..

---

### Post by nikus@rocketmail.com on 2011-05-29
I have the monitor now working, realized the driver for my LCD was corrupted, hooked up an older CRT and could see my screen, the vista mbr was gone, which was why no vista, I downloaded a new mbr then could sometimes get vista to work, it usually booted into Ubuntu, I deleted the Ubuntu partitions then upon restart got a "no grub" and now no vista either, even though I could see the partitions, I am now reloading 10.10 alongside Vista, should then be able to pick OS if all works as planned.  11.04 and Vista conflict too much to together. Will post results when I'm finished.

---

### Post by nikus@rocketmail.com on 2011-06-05
Having "no grub" error even though Ubuntu has been removed from the system.

---

