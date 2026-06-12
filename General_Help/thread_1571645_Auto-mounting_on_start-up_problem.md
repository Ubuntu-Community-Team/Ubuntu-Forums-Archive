---
title: "Auto-mounting on start-up problem"
date: 2010-09-09
forum: General Help
---

### Post by Captain Chirac on 2010-09-09
Hello.

I think the regular Ubuntu actually automatically mounts the other partitions on boot-up, but I'm using Ubuntu Studio, and apparently this distro does not. Not sure if this thread should fundamentally be posted in the Ubuntu Studio section, though. Forgive me if I'm wrong.

Anyhow. I'm using 3 hard drives. One for Linux, one for Windows and one for the documents. I want Ubuntu and Windows to have the image, music, and all these kind of folders on a common hard drive, so that I have everything in one place.
For more convenience, I installed pysdm to try and have all disks mounted on start-up. It works, but since then I get this annoying error message on the Ubuntu loading screen, that tells me to press S to skip  the mounting or M to repair manually. It won't boot until I pressed S.  After which everything runs normally. And the other drives are even mounted as I wish!
When I put everything back to default in pysdm, it boots normally, but obviously without mounting the 2 other drives as I would like. And when I try to access another hard drives, it tells me the following:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1My account type is Administrator.

Any help would be appreciated. Thanks.

---

### Post by Captain Chirac on 2010-09-10
Dang. I knew this problem was way too technical.
It's quite strange that no one else has similar issues. Auto-mounting is sort of a huge concern. It would almost make me like Windows more!
Just kidding. I guess I'll have to do find a way out myself.

Thread can be closed, thanks.

---

### Post by drs305 on 2010-09-10
Captain Chirac,

Welcome to the Ubuntu forums.

Sometimes it takes a while for someone to respond, but you will find a large and helpful group willing to assist you. One of the reasons may be that your post is tagged with "Ubuntu Studio". Many of us have no experience with it and a significant number of forumites may have skipped reading your post.

If you will post the results from the following commands we can fix up your fstab file. In addition to the command results, tell us what you want the mount point to be.

```
sudo blkid
mount
cat /etc/fstab
```

Place the results between "code" tags, which you can generate by pressing the # icon in the post's menu.

As an forum staff member, if you would still like to close the thread, I can do that as well although I think you can find your answer here. I'm about to log out but should be back in the morning and can address your problem if nobody else has.

---

### Post by Captain Chirac on 2010-09-10
Hi. Thanks a lot for the answer.
When I checked my thread, less than 30 minutes after its creation, it was already drowning on the fourth page. I guess I shouldn't have been that honest about using Ubuntu Studios!

Here's the result of the commands:

[[IMG]http://tof.canardpc.com/preview/283e33ca-5790-4fc8-a922-f3f2406a84da.jpg[/IMG]]("http://tof.canardpc.com/view/283e33ca-5790-4fc8-a922-f3f2406a84da.jpg")

For some reason, in pysdm both FAT hard drives (Windows [sda/sda2] and STOCK [sdc/sdc1]) are sharing the same name and mount point: /media/sdc1 while they are clearly different on the terminal. I can't modify one of them alone, as they are both linked.
I'd like both sda2 (sda1 being some sort of system reserved space for Windows 7) and sdc1 to be mounted on boot. Currently, they are, but I get the annoying message on start-up, and the hard drives are owned by root, which prevents me from modifying their contents.

---

### Post by drs305 on 2010-09-10
I can't see what is displayed in the jpg file so I can only give you generic advice at the moment. Generally we would like the information in text format- using copy/paste. In Linux, you copy the contents of a terminal with CTRL-SHIFT-C. You paste into a terminal with CTRL-SHIFT-V. For other applications, it's the same as Windows (CTRL-C and CTRL-V).

I am assuming that you can boot into Ubuntu, but that during the boot you are getting error messages and may have to press a key to continue.

First we can deal with your sdc1. Most of this post deals with fstab, but there are other reasons devices don't mount. For removable drives, one of the first things to try is to mount it in Windows and then properly unmount/remove the device via Windows. Unclean shutdowns can cause problems when Ubuntu tries to use the device. 

If the problem device is located in fstab, we can usually fix the error. It may not be listed as sdc1, however. It may be listed by it's UUID, which you can find with this command:
```
sudo blkid
```

To edit fstab from a normally running system, open gedit or the default text editor with the following command (substitute the app name if you use something other than gedit). The first command makes a backup copy.

```

sudo cp /etc/fstab /etc/fstab.bak
gksu **gedit** /etc/fstab
```

If sdc1 is listed, or its associated UUID is listed, place the comment # symbol at the start of the line and save the file.

If you have others causing error messages, we can try to determine which device is generating the error message by running the commands below. I'll explain them first, then you can execute them.  If you are able to determine which device it is, disable it the same way (# symbol at the start of the line). 

Next, find the device that is causing the problem during boot. If you already know which one it is, place a # symbol at the start of the line. This makes the entire line a "comment" and anything after the # symbol is not acted upon.  Save the file and continue with the next set of commands.

The first command unmounts any non-system partitions. You may get a "Busy" error message, which is OK. 

Next you will run the second command. This one attempts to mount all the entries in your fstab file. 

```
sudo -umount -a
sudo mount -a
```

You will get some "device is busy" messages when you run the "umount" command. They should be system partitions which are in use. Those messages are OK. The one that is incorrect and causing the boot problems will also display an error message when you run this command. 

It may be something along the lines of "UUID <somelongalphanumericstring> not being found." This is the one you want to comment. Find it's listing in fstab and place a comment at the start of that line. 

After making the change(s) and saving the file, run the commands again. When you have successfully 'fixed' the boot error you will get no error messagesreturn when you run the second command. 

In Linux, if a command executes successfully, you often get no feedback in the terminal. If there is an error, you get a message.

If at all possible post the results of the commands from my previous post in text format. Don't type them out manually, as that is too much work. But for some reason I cannot view the image and we really need that information to proceed if the above didn't help.

Additionally, if you would like to learn more about fstab, here is an excellent post by *bodhi.zazen*:

[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Captain Chirac on 2010-09-10
Thank you very much for this thorough reply. With your help and some tweaking of my own, I managed to solve my issue, except for a minor detail, which really doesn't matter. I'll still post what happened, in case it's of any help.

I wanted to make a screenshot so that my problem with pysdm could be clearer, as it is not the easiest thing to describe.
I will post the results of the first commands you told me to make.

```
captainchirac@CC-Desk-Linux:~$ sudo blkid
[sudo] password for captainchirac:
/dev/sda1: LABEL="RM-CM-)servM-CM-) au systM-CM-(me" UUID="9430072730071042" TYPE="ntfs"
/dev/sda2: LABEL="Windows" UUID="BE82092D8208EC29" TYPE="ntfs"
/dev/sdb1: UUID="6c458e60-fb4e-4e33-bef8-b26bdeaa583b" TYPE="ext4"
/dev/sdb5: UUID="1c9b5cb0-691a-4f1e-8e7f-01fb02ac6b88" TYPE="swap"
/dev/sdc1: LABEL="STOCK" UUID="DCDB-4B38" TYPE="vfat" 
```

```
captainchirac@CC-Desk-Linux:~$ mount
/dev/sdb1 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosThere's certainly a way to do it manually other than using pysdm.uid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/captainchirac/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=captainchirac)
/dev/sr0 on /media/MAFIA_CD_1 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
```

```
captainchirac@CC-Desk-Linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0 
# / was on /dev/sdb1 during installation
UUID=6c458e60-fb4e-4e33-bef8-b26bdeaa583b  /            ext4  defaults             0  1 
# swap was on /dev/sdb5 during installation
UUID=1c9b5cb0-691a-4f1e-8e7f-01fb02ac6b88  none         swap  defaults             0  0 
# /dev/sdd1                                  /media/sdd1  vfat  defaults             0  0
```

Apparently, I wanted to mount /sda2 (sda1 being that reserved Windows thing) and sdc1. These two aren't listed in the fstab.
However, making "sdd1" (seemingly being the DVD drive) a comment solved the booting error.
So I figured out that the booting problem certainly came from that, and nothing else. And I was right. After disabling it from the fstab, I activated sdc1 in pysdm again, and rebooted. Everything went fine, and STOCK is now automatically mounted on boot-up.

Now, there is still the problem that the Windows partition (sda2) appears as sdc1 in pysdm. So, it just won't get mounted, as pysdm sees it as STOCK.
There's certainly a way to do it manually other than using pysdm.
It is definitely not a problem, I doubt I'll ever need to have the Windows partition to be automatically mounted on start up, but it's still strange, and probably easily solved.

In any case, thanks a lot again, I couldn't have done it without your insight.

---

### Post by drs305 on 2010-09-10
Glad you figured things out!  :-)

I was about to write out the method for mounting your Windows partition in fstab, but here is a good guide, complete with some screenshots:
[http://www.psychocats.net/ubuntu/mountwindowsfstab]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

*psychocat* built a great site which serves the Ubuntu community very well. He has a lot of other good information there as well.

If you don't have any other related issues, would you please mark the thread SOLVED via the "Thread Tools" link near the top right of the first post?  It allows 'helpers' concentrate on unresolved issues and points those looking for solutions to threads which may help them.

Enjoy Ubuntu Studio. See you on the forums!

---

