---
title: "Hard disk backup using live CD"
date: 2010-06-08
forum: General Help
---

### Post by mccarun on 2010-06-08
Hi all,

I'm using a dell XPS M1530 laptop with windows vista and ubuntu 10.04. Last week when I turned on my laptop I got an error saying internal hard disk not found. When I called dell support, I have been told that my hard disk is dead. 

I have few important stuffs in my hard disk for which I don't have any back. So I tried using ubuntu live CD to back up my data as in the link below.

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

I'm using ubuntu 10.04 live CD(64 bit). When I go to my places after booting from the live CD I can't see any partition showing my hard disk. I can see "Computer". When I go in it I can only see "File System" and nothing related to my partitions in my HDD. What should I do now? Do I need to mount my hard disk or is my HDD completely dead?

Is there any other way to back up my data? Any help would be appreciated as I have some really important data. 

Thanks
Arun

---

### Post by Irony on 2010-06-08
Using your live CD install palimpsest (it may already be installed) and then run it and see if it shows your hard disk partitions.

If it does then open the partition concerned and copy your files (by dragging them) to an external drive.

If you want an exact copy of the Ubuntu partition which you can later copy back then use;

```
sudo cp -ax /mnt/folder1/. /mnt/folder2/.
```

Where the respective paths must be your actual paths - note for this to work your external drive must have a partition formatted to ext4.

If no drives are seen then your disk is dead and would need specialists to recover data from it.

---

### Post by mccarun on 2010-06-08
Thanks Irony.

Can you tell me how to start  palimpsest? Is this the one System -> Administration -> Disk Utility ? I tried running disk utility. It just pops up in the task bar and then vanishes.

Am I doing it correctly or is it different from what I did ?

I searched for  palimpsest in synaptic package Manager and it shows  palimpsest under gnome-disk-utility and Its already been installed.

---

### Post by mccarun on 2010-06-08
Sorry. My disk utility did ran and I can see the following:

Local Storage
 - PATA Host Adapter
     - CD/DVD Drive
 - SATA Host Adapter
 -Peripheral Device
    - 699 MB File

Its showing STATA Host Adapter, but not showing anything under it. Is it something to worry about?  When I click the SATA host adapter its shows the Vendor, Model, Revision, Driver, No of ports etc and nothing about the hard drive?

What does it mean? Is my hard hard disk properly connected or is it completed dead? 

Any other ways to solve this issue will be so useful to me.

---

### Post by Irony on 2010-06-10
What you are seeing in Disk utility as;

```
Local Storage
- PATA Host Adapter
- CD/DVD Drive
- SATA Host Adapter
-Peripheral Device
- 699 MB File
```

Indicates that the connectors to your drive are seen but no drive, i.e. it is dead.

Try System > Admin > Gparted, toggle through the sdaX button - you should see your drive diagrammed - if it isn't that confirms it is dead.

Also in terminal try;
```

sudo fdisk -l
```

If your drive isn't listed then your drive is dead.

The only other option after that is to put your drive into another computer and try the above options to confirm its deadness - the purpose of this being to confirm that it is your drive rather than something to do with your computer.

---

