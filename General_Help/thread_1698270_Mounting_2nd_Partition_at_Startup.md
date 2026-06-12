---
title: "Mounting 2nd Partition at Startup"
date: 2011-03-02
forum: General Help
---

### Post by trackmagic on 2011-03-02
Can somebody tell me how to make my other partition mount at Ubuntu startup? I have a shortcut to my windows XP documents folder, but the shortcut is broken every time I restart because the other partition has not been mounted.

I assume there is a terminal command I need to type into my start-up manager?

Thanks!

---

### Post by Pooch on 2011-03-02
Try installing NTFS Configuration Tool:

```
sudo apt-get install ntfs-config
```

I believe that will mount your Windows partitions on start-up. Let me know if that works.

---

### Post by trackmagic on 2011-03-02
I ran that script. It did something, but I am not sure exactly what.

Just to clarify... Right now if I go to "Places" I see "95 GB File System", which is my XP partition. If I click on that it mounts fine and an icon pops up on my desktop.

If I click on the "my documents" link to the XP partition "my documents" folder BEFORE I do the step listed above it says the link is broken and asks if I want to delete it. If I click places>95 GB file system it loads it and then if I click the link it works fine.

I just want the link to work when I startup Ubuntu without having to do that intermediate step.

I also made a startup command with that command you suggested, but it still did not work. Thanks for the reply though!

---

### Post by arpanaut on 2011-03-02
This should work for you:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

and this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by trackmagic on 2011-03-02
That worked perfect. Thanks!

A quick summary of what I did:
1) Type: "sudo apt-get install ntfs-config" in the terminal
2) Went System>administration>NTFS Configuration Tool
  2.1) Clicked "Enable write support for external devices"
  2.2) Clicked "Enable write support for internal devices"
3) Type: "gksu gedit /etc/fstab" in the terminal
4) added ",auto " between "nosuid," and "nodev," to automatically  
   mount the drive.

---

### Post by trackmagic on 2011-09-21
Hi, I had to reinstall Ubuntu 10.10 and when I click on NTFS config tool and after I enter my password nothing happens. I do not get the dialog box that I had before. Any ideas?

---

### Post by GuitarRocker2562 on 2011-09-21
Avoid double posting. Anyway NTFS config tool is unnecessary. You just need to edit the file /etc/fstab

---

### Post by GuitarRocker2562 on 2011-09-21
Manual Configuration
 First you need to find the device location of the NTFS partition(s) you want to mount. In terminal, run:

sudo fdisk -l | grep NTFS | awk '{print $1}'
The name of each partition should be something like /dev/hdxn or /dev/sdxn, where x is an alphabetical letter (ranges from a to z) and n is a number (e.g. /dev/hda1).

If the drive is internal, you will now need to edit your file systems table configuration file, /etc/fstab. If the drive is an external USB or firewire drive, hal should automount it. Now, be sure to save a backup of fstab first, then open the file for editing:

sudo cp /etc/fstab /etc/fstab.orig
gksudo gedit /etc/fstab
After entering your password, find the line that matches the device location you just found and change it to the following. If there is no entry yet, add a new line like the following:

<your partition> /media/<mount point> ntfs-3g defaults,user,locale=en_US.utf8 0 0
NOTE: If it displays your NTFS partition with a UUID, you can check the relevant device location by running one of the following commands. It is OK (and even advisable) to keep the UUID setup if that is what already exists.

sudo blkid
ls -l /dev/disk/by-uuid/
Replace <your partition> with the name of the partition you identified earlier. Replace <mount point> with the location you would like the partition to be mounted at, so you have something like /media/windows or /media/documents for that column.

Note: you can also change your locale option (ex: locale=fr_FR.utf8). Execute locale*-a in a terminal to know which ones are supported on your system.

Save and close the file. You will now need to create the mount point for each NTFS partition before you can actually mount them:

sudo mkdir -p /media/<mount point>
Now remount each partition with

sudo umount <your partition>
sudo mount -a
If you want to revert to your previous configuration, run:

sudo mv /etc/fstab.orig /etc/fstab
sudo umount /media/<mount point>

---

### Post by trackmagic on 2011-09-21
I seem to be doing something wrong. Every time I restart it says there is an error mounting the partition.

This is my fstab file code for my windows/secondary partition:


**UUID=b761cc86-818e-4adc-b010-aa600021bf59 /media/home/ben/Desktop ntfs-3g defaults,locale=en_US.utf8 0 0**



For the location I have also tried /home/ben/Desktop (leaving out "/media" since I am not familiar with that.

Does this step look ok? I don't know if this code is wrong or if maybe I'm doing one of the other steps wrong.

---

### Post by trackmagic on 2011-09-21
By the way, the partition seems to mount ok through the places menu, but I just want it to show up automatically on my desktop when I log in. The old code was:

[B]# swap was on /dev/sda7 during installation
UUID=b761cc86-818e-4adc-b010-aa600021bf59 none            swap    sw              0       0[/B]

That seemed to work fine, but it just did not make the partition show on the desktop automatically.

---

### Post by Elfy on 2011-09-21
> **trackmagic said:**
>  Every time I restart it says there is an error mounting the partition.What is the error?

It looks ok - but have you made the folder for it to mount to?

> **trackmagic said:**
> That seemed to work fine, but it just did not make the partition show on the desktop automatically.That's swap - it won't show on the desktop.

---

### Post by Morbius1 on 2011-09-21
> **trackmagic said:**
> I seem to be doing something wrong. Every time I restart it says there is an error mounting the partition.

This is my fstab file code for my windows/secondary partition:


**UUID=b761cc86-818e-4adc-b010-aa600021bf59 /media/home/ben/Desktop ntfs-3g defaults,locale=en_US.utf8 0 0**



For the location I have also tried /home/ben/Desktop (leaving out "/media" since I am not familiar with that.

Does this step look ok? I don't know if this code is wrong or if maybe I'm doing one of the other steps wrong.
No it does not look OK.

UUID's have different lengths and different formats depending on the filesystem. "**b761cc86-818e-4adc-b010-aa600021bf59" **is the UUID of a Linux filesystem ( ext4 perhaps ). The UUID of an ntfs partition would look something like this: DA9056C19056A3B3 ( no dashes - 16 characters long ).

Run the following command to confirm that the partition you are trying to mount is in fact ntfs:
```
sudo blkid -c /dev/null
```[COLOR=Blue]EDIT: BTW, you do not want to mount any partition to your desktop for a number of reasons. [/COLOR]
Any partition mounted to your home folder or /media will automatically create a mount icon on your desktop. A mount point created anywhere else will not. So make the mount point something like:
**/home/ben/WinXP**
OR
**/media/WinXP**

---

### Post by linux2001 on 2011-09-21
Isn't possible.

---

### Post by Morbius1 on 2011-09-21
> **linux2001 said:**
> Isn't possible.
What isn't possible?

Mounting a second partition at startup?
Mounting an ntfs partition at all?
Finding bipartisan cooperation in the U.S. between Democrats and Republicans on anything?

---

### Post by Elfy on 2011-09-21
> No it does not look OK.You're right - missed that, long time since I saw a NHTFS UUID in the wild. 

Re - the missing post - looks like a bean hunter - gone now.

---

### Post by Morbius1 on 2011-09-21
Appreciate you removing mine as well. Had you let it remain it would have made me look loonier that I already do :)

---

