---
title: "cd program: cd: disk-1: permission denied"
date: 2009-08-25
forum: General Help
---

### Post by billdotson on 2009-08-25
I am still having issues with permissions these days. I have /media/disk-1 (a FAT32 volume) mounted but I can't copy without gksudo nautilus or sudo cp'ing the files. So I did sudo chmod -R 744 /media/disk-1 and the computer worked for a little bit and then acted like it was done. However, now if I try to do: 

```
cd /media/disk-1
``` I get a permission denied error. I thought 744 would give everyone at least read access, what is going on? If I do gksudo nautilus and try to change them in the folder menu it just automatically changes them back.

I am confused. Also, I guess I am a bit paranoid about it but I have an XP backup image and some other installers that I am worried if I change the permissions it will mess the files up in some way. Am I paranoid or could that happen (some of them are .exe files)

If I just try to do "sudo cd /media/disk-1" I get an error that says it cannot find the command cd. Why is that? I surely shouldn't have to write a bash script saying "cd /media/disk-1" and have to run it as root to do it would I?

Thank you.

---

### Post by tgeer43 on 2009-08-25
I'm not sure about all of the issues you are having and this is just a stab in the dark but how about making sure that you are the owner of the drive with:
```
sudo chown tgeer:tgeer /dev/hda2
```replacing tgeer and hda2 with your username and the drive specifier for your hard disk.

It's a start at least and won't change any of the individual file permissions.

tgeer

---

### Post by oldos2er on 2009-08-25
FAT32 does not support Linux permissions; you need to set them when the partition is first mounted. See [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and scroll down to 'Mount the Drive'.

---

### Post by billdotson on 2009-08-25
I just tried sudo chmod -R 766 on a media mount folder for an ext3 partition and sudo chown ubuntu:ubuntu (using livecd) and now it won't even let me see anything in the mount point. Why is it doing this for ext3 as well?

Here is another example:
I mounted an ext3 partition on a mount point in the live cd. Doing sudo chmod -R 744 /media/RARG makes it so normal users can't even cd in there or see anything in it via nautilus. However, if I give r,w,x or r,x rights to normal users they can. What gives?

If I just try to do "sudo cd /media/disk-1" I get an error that says it cannot find the command cd. Why is that? I surely shouldn't have to write a bash script saying "cd /media/disk-1" and have to run it as root to do it would I? Do you have to run "su" and login as root terminal for some things?

---

### Post by oldos2er on 2009-08-25
I am somewhat confused. You shouldn't need "sudo" for a simple "cd" command. What command do you use to mount the FAT32 partition?

 Here's more info: [http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)

---

### Post by billdotson on 2009-08-26
well if I give a mount point chmod 744 or less I can't even cd into it anymore or see the files in nautilus. cd'ing as a superuser is the only way to get into it. Same thing is happening with an ext3 partition.

---

