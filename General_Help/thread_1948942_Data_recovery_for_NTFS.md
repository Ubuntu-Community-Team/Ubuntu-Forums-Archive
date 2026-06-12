---
title: "Data recovery for NTFS"
date: 2012-03-29
forum: General Help
---

### Post by Krazi3 on 2012-03-29
I accidentally when installing windows 7 formatted one of my ntfs drives. :(

Is there any software or app. to recover the lost data in linux (ubuntu) ?

I have tried many softwares in windows 7 but none of them work well.

Some have recovered the files but in the damaged condition. :(

Can someone help me? Please.

Thanks

---

### Post by westie457 on 2012-03-29
Hi your best chance is probably 'photorec' which comes with 'testdisk'. Testdisk is in the repositories or can be downloaded from here  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) where there is full instructions.

---

### Post by winh8r on 2012-03-29
You should be able to get your files back using testdisk.

You should run it from the live cd and recover the files to another partition on your hard drive (the Ubuntu partition would be a good idea).

Run the live cd and open a terminal by pressing control + alt + T then enter

```
sudo apt-get install testdisk
```

to run it you need to enter

```
sudo testdisk
```

there is a step by step guide here :
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

which I would suggest you READ THOROUGHLY before you proceed and if you have any questions or are unsure about anything , post back here before you attempt anything.

Hope this helps you.

Good Luck

**[B]****EDIT*** just like Westie457 said!!!!! **[/B]

---

### Post by Krazi3 on 2012-03-29
Thanks for the quick reply.... can you tell me one thing more that .. the **testdisk **app does it recover the files along with the folders as well or only the files..

---

### Post by dragonfly41 on 2012-03-29
Be aware that testdisk and photorec will not recover file directory structure or filenames.
> I have tried many softwares in windows 7 but none of them work well.
 
 Some have recovered the files but in the damaged condition

What many windows recovery programs did you try for ntfs data recovery?

I've used Recover My Files from getdata.com .. running on windows.

The other tip you'll find under data recovery posters here is to stop using the  formatted drive and try to recover from another PC (by connecting it as  slave drive) or Live CD.  Perhaps you would be advised to first backup  your formatted ntfs partition using clonezilla.

---

### Post by Krazi3 on 2012-03-29
Currently i have my hard drive linked in slave with another pc and running photorec in windows xp.

I have not created any image but i haven't written anything on that drive as well.

Can u suggest me some program which can bring out my files structurally.

Photorec has brought them out with the but renamed and unstructured.

---

### Post by dragonfly41 on 2012-03-29
I suggested one above ..

[http://www.getdata.com/](http://www.getdata.com/)      Recover My Files

***try it first*** before buying .. you will see the files which can be recovered (after buying the licence)

there are others such as Stellar Phoenix.   Search this forum "data recovery".

---

### Post by Krazi3 on 2012-03-29
Does recover my files give the data back structurally ??

Thanks for the help. I will search the forum.

---

### Post by dragonfly41 on 2012-03-29
> Does recover my files give the data back structurally ??It did for me .. but as I wrote try it our first.

See also here .. ubuntu tools ..

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

install foremost and scalpel from Synaptics Package Manager

The target partition containing the deleted data to be recovered should not be mounted.

....

and some others I've researched ..

[http://www2.opensourceforensics.org/tools/unix](http://www2.opensourceforensics.org/tools/unix)

sudo apt-get install autopsy

[http://forensiccop.blogspot.com/2009/09/experiment-14-on-deleted-files-recovery.html](http://forensiccop.blogspot.com/2009/09/experiment-14-on-deleted-files-recovery.html)

[http://accessdata.com/products/computer-forensics/ftk](http://accessdata.com/products/computer-forensics/ftk)

---

### Post by Mark Phelps on 2012-03-29
If you still want to try recovering the files from the (former) NTFS partition, look for Recuva.  It's a FREE MS Windows app and may work for you -- but you'll have to run MS Windows to use it.

Also, did you try GetDataBack for NTFS from Runtime Software?  They're the same folks that sell Recover My Files.  It's also FREE to try, but like Recover My Files, you have to buy it to actually get the files back.

The Runtime Software apps recover the complete folder structure along with the original filenames -- something you'll need unless you're just going after a handful of files.

---

### Post by ajms1989 on 2012-03-30
Sometime recovering data with free software like Recuva may wipe the data completely & leaving no chances of recovering it back at anyhow. So chose these software very carefully because it can ruin your years of efforts.
I would never recommend to with freeware.

You can Google For Some best Data recovery software and read the review posted on famous software download website like Cnet and then decide which software to go with.

Completely agree with marks that there are many software which could give you the preview of recoverable file and folders. After that, it is easy to choose weather or not you have to go with that software.

---

### Post by Krazi3 on 2012-03-30
I did try GetData back for NTFS from runtime but it just didnt work well i mean i did get some of the files back but mostly were damaged.

And thanks for the help.

---

### Post by ajms1989 on 2012-03-30
If you are still looking for the file that were gone, then why not try another one.I have some software to recommend which i have tested and got good results.

---

### Post by imachavel on 2012-03-30
all of them? Don't you mean some of them? I've never seen any data recovery software retrieve all files, and if he formatted over the previous partition completely, who can say even 1 file still exists? Well it's possible if he had a TON of files, and most people do right?

Man, I am more disappointed with windows every day, I've had the worst luck with windows data recovery software for deleted files, and you have to pay for it

---

### Post by imachavel on 2012-03-30
> **Krazi3 said:**
> I did try GetData back for NTFS from runtime but it just didnt work well i mean i did get some of the files back but mostly were damaged.

And thanks for the help.

it's unfortunate but if you have written over files completely, it's rare you'll get them all back. It is sometimes safer to repartition a disk before installing an OS. An OS installer will give you the option to create a new partition. But using a partition disk just seems slower and a safer bet that you take your time to see how much additional space is there, and recognise the new partition you create, etc.

Unless you plan to install multiple OSes through a network boot sequence, and are fresh formatting over everything, then always take your time when you install a new OS into a new partition. Take hours, take days. Ask in threads. Just be careful. Aside from frying your hardware, formatting over something is the best bet to never get your files back. Getting frustrated with configuring an OS, or trying network or internet options, or programs or applications, or learning an interface, is a task of it's own. But lost files = :confused:#-o

---

### Post by ajms1989 on 2012-03-30
Hello imachavel,
Almost every major windows data recovery software are paid and won't guarantees 100% results. Though these software are free to take preview of recoverable files but sometime they couldn't able to recover the same data after being paid. 

So, Software companies are making their bugs by fooling people sometime by charging more than $1000 without any guarantees of recovery and people would have no choices.

---

### Post by dragonfly41 on 2012-03-30
Did you try the links to forensic recovery software (linux) in my post #9 above?

---

### Post by Raileely on 2012-06-11
You should know that, if you accidentally format a critical NTFS drive or FAT drive, it is possible to get all the data back, because format does not really erase the data on the disk. But in case of data will not be overwritten, it is better to stop using the drive. A computer specialist is able to r[ecover NTFS files ]("http://www.easeus.com/resource/unformat-ntfs-fat-drive.htm")or FAT files from formatted drive with a certain method to unformat NTFS drive or FAT drive. An easier way is to try some reliable data recovery software, such as EaseUS Data Recovery Wizard, assisting with unformat of NTFS drive or FAT drive to recover files from formatted NTFS drive or FAT drive.

EaseUS Data Recovery Wizard works on all environments of Windows including Windows 2000/XP/2003/Vista/2008/Windows 7, supports NTFS file systems and FAT files system, recognizes all NTFS/FAT versions includingFAT12, FAT16, FAT32 and NTFS. It is reliable unformat software that provides you with powerful unformat, undelete function, and you can unformat NTFS drive or FAT drive easily and safely.

---

### Post by Mark Phelps on 2012-06-11
> **Krazi3 said:**
> I did try GetData back for NTFS from runtime but it just didnt work well i mean i did get some of the files back but mostly were damaged.

And thanks for the help.

IF the files are damaged, NO software recovery app is going to recover them -- repeat NONE!

As to the COST, I've yet to find a file recovery app that even costs $100, not $1000!  That is what the professional recovery services cost -- and they charge that because they disassemble your drive in clean room environments, repair the hardware damage (as best they can), reassemble the drive, and use hardware to recover the files.

---

### Post by lucycook on 2012-07-02
For all those who consider loss of data as a serious threat, then it&#8217;s high time to change that illusion because with the help of **Kernel for Windows Data Recovery** it is very much possible to recover data instantly. This software is very much capable of recovering data in almost all situations and can be considered as best option to restore the data lost from computer's hard disk.

Thanks
		 	  	 	 		 			recoveryfiles.net

---

