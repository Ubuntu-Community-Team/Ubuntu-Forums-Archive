---
title: "Can't see files on usb drive."
date: 2011-11-07
forum: General Help
---

### Post by dude1 on 2011-11-07
I have been using Mandriva for a long time. I was having troubles with updates and ended up loosing my GUI. So the easiest way for me to fix this was to install Ubuntu 11.10. I have a satellite connection and it is super slow, so Ubuntu was the logical choice. Anyway, I command line copied my file from Mandriva to a thum drive and now I want to transfer them back to this computer. The drive shows up as a 4 gig dos drive and is empty. The files should be ext3 maybe ntfs I think. So what am I missing? I'm not familiar with Ubuntu, but it should be able to see ext3 files. I tried to use a terminal to get into my thum drive and it also shows no files, AARRGG!
Thanks ...

---

### Post by raja.genupula on 2011-11-07
hi welcome to forums

```
ls -a
```

it will display all files.

---

### Post by dude1 on 2011-11-07
raja.genupula,

ls -a  I get . ..

I try ls -la I get the number  12

It sort of seems like it sees something. What about mount points, not sure what to look for though.

Thanks!

I just noticed that from the command line, in Mandriva the thum drive was /media/sdb1, on Ubuntu is /media/CENTON USB
Not sure if thats a problem or not. If so how do I change it?

---

### Post by Gatemaze on 2011-11-07
Just to make sure. Can you please do
ls /media

Then from there do
ls /media/<name of your drive from the ls /media>

do
pwd

do
ls -a

and please post back all the outputs

---

### Post by dude1 on 2011-11-07
```
dad@dad-Aspire-one:/$ ls /media
CENTON USB


dad@dad-Aspire-one:/$ ls /media/CENTON*USB
dad@dad-Aspire-one:/$ 


dad@dad-Aspire-one:/$ pwd
/

dad@dad-Aspire-one:/media/CENTON USB$ ls -a
.  ..


```
Thanks!

---

### Post by btindie on 2011-11-07
And what's the output of
```
mount | grep CENTON
```
If the partition is mounted it'll return the device name, e.g. /dev/sdb1. Replace the following with that.
```
sudo blkid /dev/sdb1
```

---

### Post by dude1 on 2011-11-07
```
dad@dad-Aspire-one:/$ mount | grep CENTON
/dev/sdb1 on /media/CENTON USB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1
,showexec,flush,uhelper=udisks)
```



I'm kind of confused with this. What do I do with this [/FONT]sudo blkid /dev/sdb1 ? 
I think this is the fstab, do I vi it and change it? 

Thanks!

---

### Post by nothingspecial on 2011-11-07
Hi,

Please use code tags when posting output from your terminal.

Just click the # in the top of the posting box and paste the output in between.

---

### Post by btindie on 2011-11-07
> **dude1 said:**
> ```
dad@dad-Aspire-one:/$ mount | grep CENTON
/dev/sdb1 on /media/CENTON USB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1
,showexec,flush,uhelper=udisks)
```

Your USB disk appears to the system as /dev/sdb1 and is monted on /media/CENTON USB, it's using the FAT filesystem and not ext3.

You just need to type the following into the terminal, it'll probably prompt you for your password as it runs the command with root privileges
```
sudo blkid /dev/sdb1
```
And also
```
df -h /media/CENTON\ USB
```

---

### Post by dude1 on 2011-11-07
[btindie,]("http://ubuntuforums.org/member.php?u=876590")
Nothing changed, I re-ran the mount | grep Centon and the same thing appears as before.

I plugged it into a windows 7 computer and it also shows the drive empty. I copied files to it in Mandriva, removed the drive at least twice and copied more files and they would show up.
Maybe they are just lost.

Oh well...  thanks for the help.

---

### Post by btindie on 2011-11-07
Did you create an ext3 filesystem on there yourself via mkfs.ext3 ?

It may be that you've changed the filesystem on the USB disk but haven't changed the partition type id from "W95 FAT32" to "Linux". Which would explain why it's mounting it as vfat and nothing is visible.

Unlink windows, there's generally a plausible reason why something isn't working as you expect. You've just got to track it down..

---

