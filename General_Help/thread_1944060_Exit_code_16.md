---
title: "Exit code 16?"
date: 2012-03-20
forum: General Help
---

### Post by Bozihome on 2012-03-20
I'm having a big problem today guys and I want to make this a learning experience but I'm getting a little irritated. I won't get irritated with you guys of course because your helping me but the process in general is frustrating.

Here's my story: My buddy gave me his tower to diagnose what was wrong with it, I boot it up and the hard drive starts making some clicky noises - imminent hard drive failure and the OS (Vista) is having a bunch of problems trying to boot up. I don't have the time to sit around and wait for it to repair itself if its already damaged and there's a ticking clock for the hard drive. My next step is to gain access and back up his data with my favorite live USB distro. I easily boot up in Ubuntu and head to the file manager. The hard drive is titled as OS and my live disc is titled casper-rw. I click on the OS and nothing shows up. I look in the permissions and it only gives me access to create and delete files on the free space of that hard drive. Not good enough, and I try to change the permissions but they automatically force themselves only to create and delete files. I'm locked out of this hard drive.

I try to unmount and remount the hard drive and I get this message:

Unable to mount OS

Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may already be mounted or another software may use it which could be identified for example by the help of 'fuser' command.

I do a bit of research and ask a few questions, and I'm told to try out these commands: 

sudo fdisk -lu

cat /etc/mtab

The results are here: [http://imgur.com/vHRYo,LcU6v,JTFi1#2](http://imgur.com/vHRYo,LcU6v,JTFi1#2)

Since its alot to type, I took a picture of it and posted it on imgur and hopefully you guys can help make something out of it. I know there are other ways to go about this but I want to be more experienced with linux and learn from this experience rather than using mini-XP to get the job done. So give me everything you got to help out, I appreciate it.

---

### Post by matt_symes on 2012-03-20
Hi

Before you do anything, get an image of his hard drive. Use Clonezilla or ddrescue.

For ddrescue. From the software sources, enable Universe and

```
sudo apt-get install gddrescue
```

Get a spare external drive and mount it.

```
sudo ddrescue /dev/sda /mount/point/of/external/drive/backup.img
```

If the drive is failing then don't even bother trying to mount it until you have attempted to image it.

If you can get an image off then you can copy it, mount it and play with it to your hearts content. There is a risk to this though.

Kind regards

---

### Post by Bozihome on 2012-03-20
sudo ddrescue /dev/sda /mount/point/of/external/drive/backup.img

Break it down for me please, lol I don't know how to get the point of external or how to identify the drive. I'm probably overthinking it.

---

### Post by matt_symes on 2012-03-20
Hi

> **Bozihome said:**
> sudo ddrescue /dev/sda /mount/point/of/external/drive/backup.img

Break it down for me please, lol I don't know how to get the point of external or how to identify the drive. I'm probably overthinking it.

If i think the drive is going to fail iminently, i will try to image it first. If it fails while getting an image then it would have probably failed while copying files anyway. 

There are many ways to do this. One way is using ddrescue.

You need to install ddrescue. From the terminal in a LiveCD/USB

```
sudo apt-get install gddrescue
```

Plug in an external hard drive that has enough space for the whole of the other drive.

It should be auto-mounted under /media. If not open Nautilus and click on it to mount it.

Make sure the drive (sda, the one you are trying to image) in the computuer is _not_ mounted.

External drive mounted. Internal drive not mounted.

Then from the terminal

```
sudo ddrescue /dev/sda /media/folder_in_media/backup.img
```

You need to change folder_in_media to the name of the folder that the external drive was mounted at.

You can find this with

```
ls /media
```

I hope that is clearer. Be prepared for a wait

Kind regards

---

### Post by sudodus on 2012-03-21
After a night's sleep I found your message, and read several replies in your two threads. I think that the advice by [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") is very good, and suggest that you continue along that line. I will only add a few things to make it easier.

1. Read the info page about ddrescue. It is very well written, and will   help you understand how to save a failing disk. Run ```
info  ddrescue
``` in a terminal window.

2. In particular read the following
```
Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to
/dev/hdb
Note: you do not need to partition /dev/hdb beforehand.

     ddrescue -n /dev/hda /dev/hdb logfile
     ddrescue -dr3 /dev/hda /dev/hdb logfile
     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1
     e2fsck -v -f /dev/hdb2
```I suggest that you add 'logfile' to  the command and that you clone the drive instead of making an image. The  logfile is particularly important since you think the drive is failing  right now, because it makes it possible to run a stepwise procedure to  recover as much as possible. (It is also OK to make an image. It can  also be mounted, which [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") might suggest later on, but ***I*** have not used that method together with a logfile.)

3. You need one or two more drives, one at least as big as the failing  one, 750 GB? (it is hard to read the blurry picture), and one for the  log file. I think the USB flash drive should be big enough for that. But  make sure to write the logfile to a partition on the flash drive, not  to ram-drive! The big drive should be the target, where to clone the  failing drive.

4. Use the file browser to mount /dev/sdf1 of the usb drive (the 4 GB  drive) according to the tips in replies in your thread. And after that  run the following commands.
```
sudo fdisk -lu
``````
cat /etc/mtab
``````
df
``` ***The  output of these commands can be copied and pasted into a reply window  and do it when you have connected the big drive (the target)***. Then you can surround it with code tags (mark it and click on the # sign at the top of the reply window in the thread).

5. After reading and interpreting the output of the commands in (4), you  can get a detailed instruction, how to write the command lines.

---

