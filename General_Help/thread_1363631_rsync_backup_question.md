---
title: "rsync backup question"
date: 2009-12-24
forum: General Help
---

### Post by 3pinner on 2009-12-24
I am going to use rsync to backup /home.
I have connected a usb drive (WD My Passport Essentials 320 GB), formatted it ext3 and labeled it Home Backup.
in gParted it is listed as /dev/sdg

I am using a gui front end for rsync called luckybackup, and cannot get it to "see" the attached drive.
The drive is mounted, and I can access it from the shortcut on my desktop. I created a directory called home backup on the usb drive.

So my question is:
How do I get rsync to copy files to my attached drive?
(either using luckybackup or thru the command line?)
Could it be a permissions issue? When I click on the USB drive and look at the permissions, It says "Permissions could not be determined"??

In running a test (I set the rsync destination as /dev/sdg/Home Backup/home backup)
I get the following error message:

rsync: ERROR: cannot stat destination "/dev/sdg/Home Backup/home backup/": Not a directory (20) rsync error: errors selecting input/output files, dirs (code 3) at main.c(572) [receiver=3.0.3] 

rsync: connection unexpectedly closed (9 bytes received so far) [sender] rsync error: error in rsync protocol data stream (code 12) at io.c(635) [sender=3.0.3] 
execution of task : test backup, finished

So what did I do wrong??

Thanks!

---

### Post by ajgreeny on 2009-12-24
You need to use the full pathway to the disk's mountpoint folder in your installed distro, which in ubuntu is probably **/media/passportdrive/Home Backup/home backup**.

The bit where I have written "passportdrive" may be "disk#" or perhaps the label for the disk, if it has one (that's easiest), but look in /media with it attached and mounted to find out the pathway.

---

### Post by 3pinner on 2009-12-24
> **ajgreeny said:**
> You need to use the full pathway to the disk's mountpoint folder in your installed distro, which in ubuntu is probably **/media/passportdrive/Home Backup/home backup**.

The bit where I have written "passportdrive" may be "disk#" or perhaps the label for the disk, if it has one (that's easiest), but look in /media with it attached and mounted to find out the pathway.

Thank you and I figured that out as soon as I posted this question.
A simple mistake.
In my case the correct path should have been: 
 /media/Home Backup/home backup/

I'm still getting used to how Ubuntu shows the various drives in the system. As a long time Windows user, I still tend see things the wrong way.

Thanks for the help!

---

### Post by falconindy on 2009-12-24
Since there's white space in the path, you'll either need to quote the path or escape the spaces.

Quoting:
```
"/media/passportdrive/Home Backup/home backup"
```

Escaping:
```
/media/passportdrive/Home\ Backup/home\ backup
```

Both are equivalent but the quoting method is easier to accomplish when done via scripting.

---

### Post by ajgreeny on 2009-12-25
Take note of falconindy's comment and avoid as far as possible, in the whole linux filesystem, folder names with spaces; use a - or _ instead to make life just a little bit easier.

If your backup drive's mount folder name is changeable easily, I suggest you do so, but you may need to change the disk's label with gparted, or tune2fs if it is an ext3 or ext4 filesystem.  If you can't do it or just can't be bothered, then the two ways falconindy shows will do it as well, but it is just a point worth making about names generally in linux.

---

### Post by 3pinner on 2009-12-26
> **ajgreeny said:**
> Take note of falconindy's comment and avoid as far as possible, in the whole linux filesystem, folder names with spaces; use a - or _ instead to make life just a little bit easier.

If your backup drive's mount folder name is changeable easily, I suggest you do so, but you may need to change the disk's label with gparted, or tune2fs if it is an ext3 or ext4 filesystem.  If you can't do it or just can't be bothered, then the two ways falconindy shows will do it as well, but it is just a point worth making about names generally in linux.

Thank you both. I had forgotten about that.
Old windows habit!!

---

