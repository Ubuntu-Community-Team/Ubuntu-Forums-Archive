---
title: "Can't delete partition - it's mounted."
date: 2010-04-27
forum: General Help
---

### Post by shadow82x on 2010-04-27
Hello Guys,
First let me say. I am trying to actually whipe my entire hard drive and figured it may just be easiest to format the hard drive and deleting the partitions. So when I go to System => Adminstration => Disk Utility => Select the Hard Drive => Click Delete Partition => And I get the error shown in my screenshots 

I am a rather noob when it comes to Ubuntu, so what would be my best way to delete this partition and remove ubuntu completely for the time being.

Thanks :)

ETA - And yes I am using the latest RC. 10.04. However I don't suspect this is a bug.

---

### Post by Dareth on 2010-04-27
You're currently using the hard drive to run Ubuntu, so you can't delete the partitions from within it. If you have a live CD, boot it from there and delete the partitions.

---

### Post by shadow82x on 2010-04-27
I do have a 9.04 live CD. (Not sure if thats a conflict because I have 10.04 installed) Is there anyway to delete the partitions without actually installing ubuntu at the time?

---

### Post by warfacegod on 2010-04-27
dareth is correct. You can't delete a partition that the OS you are using is on. You will need to do that from a Live Environment such as the LiveCD/USB you used to install Ubuntu. When the Live Envirnoment loads, assumong you are using Ubuntu's, go to: System> Admin.> Gparted

---

### Post by Dareth on 2010-04-27
That liveCD will work. If you cancel the installation after you delete the partitions, it should leave your hard drive blank.

---

### Post by shadow82x on 2010-04-27
Thanks guys. Ill try it out let you know how it goes. :)

---

### Post by 2hot6ft2 on 2010-04-27
No need to start the installer. Like warfacegod said using the livecd "go to: System> Admin.> Gparted"
Then right click on the swap partition and select swapoff.
Right click anything with a lock on it and select unmount
then do what you want to do.

---

### Post by srs5694 on 2010-04-27
If you want to delete *all* of the partitions on a Master Boot Record (MBR) disk (which yours is, according to your screen shots), you can do the following at a shell prompt:

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

```

Change /dev/sda to whatever device is appropriate (your screen shot shows /dev/sda). When you shut down and reboot, there will be no partitions defined, so you'll need to boot from another disk, replace the disk, or whatever.

A few comments:


[list]
[*]This command is *extremely dangerous.* If you mistype something (such as specify the wrong device file as the "of=" option), you could easily wipe out another disk.
[*]This command wipes out the partition table, but it doesn't alter the data within the partitions. Thus, despite my previous point, this command is not really a secure way to destroy data. If you want to wipe the disk clean for security purposes, it won't work. (You could omit the "count=" option to wipe the whole disk. This action will probably take several hours to complete.)
[*]This command wipes out the *MBR* primary partition table, but that's insufficient for a GUID Partition Table (GPT) disk. If you have a GPT disk, you must wipe out several (probably 33) additional sectors after the MBR, as well as the same number of sectors at the end of the disk. You can do this with dd, but it's easier to use the 'z' option on the experts' menu of my [GPT fdisk](http://www.rodsbooks.com/gdisk/) program. Other partition table types have their own quirks, but MBR and GPT are the ones you're most likely to encounter.
[/list]

---

