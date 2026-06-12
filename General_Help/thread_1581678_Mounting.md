---
title: "Mounting"
date: 2010-09-25
forum: General Help
---

### Post by blackmail on 2010-09-25
I have a problem, since some time whenever i insert a DVD, CD or whatever in my optical disk reader it doesn't wanna read the stuff! it says unable to mount whatever it is i try to insert this happens with both blanks and written optical disks. Anyone know what to write in FStab to solve this problem. I also would like to mention that I have used Gmount iso and maybe i screwed up something. I am purging it as we speak so i will post if any changes...

---

### Post by blackmail on 2010-09-25
I have trried chown on /dev/sr0 and on /media/cdrom0 but nothing i still receive:


Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sr0 on /media/cdrom0

Could it be that I am doing something wrong?

---

### Post by Rocket2DMn on 2010-09-25
Can you please post your current fstab?
```
cat /etc/fstab
```

Also check System->Administration->Users and Groups.  Look at the Advanced Settings for your user and ensure that "Use CD-ROM drives" is checked under User Privileges.

---

### Post by blackmail on 2010-09-25
Checked my user privileges and the check box is checkes for CD-ROMs, also the cat /etc/fstab is:

# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=12b35ffe-c92a-4d58-bc93-a254726cd779 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=69ab2f31-7baf-4a56-bffe-905294134f7a /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=75e01f37-3ac9-4409-b47a-d59eed03aebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,noauto,exec,utf8 0       0

Thank you for your prompt reply :D

---

### Post by Rocket2DMn on 2010-09-25
It looks like your line for the scd0 is malformed.  

```
/dev/scd0 /media/cdrom0 udf,noauto,exec,utf8 0 0
```

Your 3rd and 4th columns are merged together, so you haven't correctly declared the filesystem type, you have it stuck with the mount options.

Here is what I have, you might give it a try:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
The only difference between mine and yours (other than being correctly formed) is that I also included *iso9660* as a filesystem type and *user* as a mount option.

To modify fstab, run
```
gksudo gedit /etc/fstab
```

---

### Post by blackmail on 2010-09-25
THNX very very very much this did the job!

---

### Post by blackmail on 2010-09-26
I come back with YAMP (Yet Another Mounting Problem)
My main problem is the following:
I inserted a Cd and well it gave me an error again:

mount: special device /dev/scd0 does not exist

So I, the simple minded one, thought let's make this and I typed sudo mkdir /dev/scd0 and then it gave me:

mount: /dev/scd0 is not a block device

What can I do?

---

### Post by WorMzy on 2010-09-26
Don't use chown or try to create directories in /dev, it's a special directory used by the Operating System to store information about the various devices that make up, or are attached to, your PC. Messing about with it could possibly cause your system to crash. The same goes for /sys and /proc, though you shouldn't really mess around with any folders except for your own /home/username folder, unless you know what you're doing.

If you're using 10.04 or 10.10, then I recommend commenting out the /dev/scd0 line from your fstab, it's no longer necessary. Try doing that, then reinserting the CD.

Oh, lines beginning with a "#" are commented out.

---

### Post by blackmail on 2010-09-26
odd and frustrating is the thing that I don't understand why this is happening...
I just restarted my computer and now it works fine without any other modification, anyway i will comment the line you have suggested.
restart and it works... looks like windows :((
I will post if any changes regarding the fstab operation
Thank you

---

### Post by WorMzy on 2010-09-26
It could be that one of your chown commands messed the /dev folder up. /dev, /proc and /sys are automagically populated when you boot up, so any changes you might have made would have been undone.

---

### Post by blackmail on 2010-09-26
The commenting of the fstab worked, i am writing a dvd as we speak. Thank you for the info, there is just one thing, if i try to eject a normal CD from the drive's button then it does not react if i try unmount from the gnome interface it still does not work and so i have to unmount /media/cdrom0 as root. So my question is: Am I doing something wrong or this is the way it should be. not that i cant write a little bash to unmount and eject the cd/dvd :D, i am just asking

---

### Post by WorMzy on 2010-09-26
I've seen some posts around recently that suggest that quite a few people are having problems with their DVD/CD Drive eject buttons. I'm not sure what might be causing that, though posts I've seen are suggesting it could be a kernel issue, so it may be fixed in the next version of Ubuntu (released next month). For the time being, try running 'eject' from a terminal, and see if that works.

---

### Post by blackmail on 2010-09-27
yet again after a sweet restart it started working fine in all aspects :)
thnx for the help

---

