---
title: "Trying to find a file on my Wubi Install Of Ubuntu"
date: 2011-10-08
forum: General Help
---

### Post by PayPaul on 2011-10-08
[SIZE=2]I had a low disk space error today. I had tried to make a backup of my system using commands found in this forum for backing up and restoring the system. Unfortunately those commands produced a file that was 17 gbs in size. Hence the low disk error. I tried to delete the file and found it was in the root. I could not delete because I discovered my user name did not have administrator privileges on the root. My user account had been set to "custom". I changed that to Administrator and tried to log in again. I was getting the login screen over and over again. Further research pointed to the low disk space as the cause. Ultimately my problem may be trying to delete the 17gb file. At present I am typing this from a LiveCD trial of Ubuntu. From there I am trying to find that file with no success. It has the default name of backup.tar.gz. I've searched for it on the entire computer with no results. 

Please help me someone!! I'm dead in the water at this point.

Update: I did find a file called "root.disk" that seems to match the size of my Wubi Ubuntu install. Could it be that I cannot access this file at all to delete it? I'll still have logon problems. I'm I stuck with this logon problem and should I just do my reinstall of Ubuntu now? The only thing I've been able to backup so far prior to this problem is my installed packages.
[/SIZE]

---

### Post by mike555 on 2011-10-08
If you can still get into Ubuntu open terminal and type sudo nautilus , that should let you go to the file and delete it .

 you should do a "real" install of Ubuntu and make a big enough partition ...

---

### Post by PayPaul on 2011-10-08
> **mike555 said:**
> If you can still get into Ubuntu open terminal and type sudo nautilus , that should let you go to the file and delete it .

 you should do a "real" install of Ubuntu and make a big enough partition ...

Thanks for the tip.

Will this work from the LiveCD "Try Ubuntu" setup I am working from now? Once I put that command in how can I find the file? The file was created in the Root directory thus is something I could not delete. I discovered I had to be an administrator to do anything to files in the root directory. That's weird and I hate to say it just as problematic as Windows with regard to user privileges. Am I stuck with this file? 

More research and I've found that Nautilus is the default file manager in this distro of Ubuntu. What can sudo nautilus do for me if I already have this as the file manager? My Version is Nautilus 2.32.2.1

---

### Post by PayPaul on 2011-10-08
> **mike555 said:**
> If you can still get into Ubuntu open terminal and type sudo nautilus , that should let you go to the file and delete it .

 you should do a "real" install of Ubuntu and make a big enough partition ...


This is what I got when I tried that command from a live session.

```
ubuntu@ubuntu:~$ sudo nautilus
Initializing nautilus-gdu extension

** (nautilus:8334): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '8334'

(nautilus:8334): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:8334): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

```

I didn't think it would give me satisfaction. I saw something in the forums about mounting the root.disk file which seems to match the size of my current Ubuntu install. How do I do that? Right clicking on didn't produce any sort of mount choice.

---

### Post by bcbc on 2011-10-09
This show how to mount the wubi virtual disk and remove the backup file.
```
sudo mount -o loop root.disk /mnt 
sudo rm /mnt/backup.tar.gz
sudo umount /mnt
```

In general, when backing up your whole system, the output should be directed to some external media that has sufficient space. Most of these utilities aren't going to be able to check if you have sufficient space beforehand and handle it accordingly.

---

### Post by PayPaul on 2011-10-09
> **bcbc said:**
> This show how to mount the wubi virtual disk and remove the backup file.
```
sudo mount -o loop root.disk /mnt 
sudo rm /mnt/backup.tar.gz
sudo umount /mnt
```In general, when backing up your whole system, the output should be directed to some external media that has sufficient space. Most of these utilities aren't going to be able to check if you have sufficient space beforehand and handle it accordingly.

Thanks for that code. Yet this is the output I got when I did that.

root.disk: No such file or directory

I even tried to cd into that partition. The path to is /media/Data And Documents/ubuntu. That produced the same results. I am running this from a live session. Could that be why?

---

### Post by bcbc on 2011-10-09
The root.disk is on a partition. So you need to mount that first... and then cd to the directory containing the root.disk. Either that or modify the mount command...

e.g.
```
sudo mount -o loop /media/xxx/ubuntu/disks/root.disk /mnt
```edit: in your case:
```
sudo mount -o loop  /media/Data\ And\ Documents/ubuntu/disks/root.disk /mnt
```

(note the backslashes to escape the spaces in the path)

---

### Post by PayPaul on 2011-10-09
> **bcbc said:**
> The root.disk is on a partition. So you need to mount that first... and then cd to the directory containing the root.disk. Either that or modify the mount command...

e.g.
```
sudo mount -o loop /media/xxx/ubuntu/disks/root.disk /mnt
```edit: in your case:
```
sudo mount -o loop  /media/Data\ And\ Documents/ubuntu/disks/root.disk /mnt
```(note the backslashes to escape the spaces in the path)

Thanks for all that. Especially for the way to get around the spaces. I had a feeling terminal commands do not like spaces. Yet this was the output. I eventually did cd to that directory and tried to remove the file with no results. I'm doing something wrong here I know it.

```
ubuntu@ubuntu:~$ sudo mount -o loop  /media/Data\ And\ Documents/ubuntu/disks/root.disk /mnt
ubuntu@ubuntu:~$ sudo rm /mnt/backup.tar.gz
rm: cannot remove `/mnt/backup.tar.gz': No such file or directory
ubuntu@ubuntu:~$ cd /media/Data\ And\ Documents/ubuntu/disks
ubuntu@ubuntu:/media/Data And Documents/ubuntu/disks$ sudo rm /mnt/backup.tar.gz
rm: cannot remove `/mnt/backup.tar.gz': No such file or directory
ubuntu@ubuntu:/media/Data And Documents/ubuntu/disks$ 

```

Is there a method for finding that tar file to make certain of its name and location. I know it's in the root directory of my current Ubuntu installation.

---

### Post by bcbc on 2011-10-09
> **PayPaul said:**
> Thanks for all that. Especially for the way to get around the spaces. I had a feeling terminal commands do not like spaces. Yet this was the output. I eventually did cd to that directory and tried to remove the file with no results. I'm doing something wrong here I know it.

```
ubuntu@ubuntu:~$ sudo mount -o loop  /media/Data\ And\ Documents/ubuntu/disks/root.disk /mnt
ubuntu@ubuntu:~$ sudo rm /mnt/backup.tar.gz
rm: cannot remove `/mnt/backup.tar.gz': No such file or directory
ubuntu@ubuntu:~$ cd /media/Data\ And\ Documents/ubuntu/disks
ubuntu@ubuntu:/media/Data And Documents/ubuntu/disks$ sudo rm /mnt/backup.tar.gz
rm: cannot remove `/mnt/backup.tar.gz': No such file or directory
ubuntu@ubuntu:/media/Data And Documents/ubuntu/disks$ 

```
I was just going on the name you gave for the backup file. Likely you called it something else. Try this:
```
gksu baobab /mnt
```That will analyse the root.disk and show you the biggest files. Then note the name and path and delete the backup. (Use the command line to delete it).

---

### Post by PayPaul on 2011-10-09
I used that command and the resultant program to find the file. It actually allowed me to right click on /mnt and find the file which had an extension of .tgz. I accidentally put it in the trash but was able to move it to an external drive. I tried hitting the delete button on that file in the.trash-0 folder but another file was instantly created called backup.2.tgz. Weird but the move worked and the size of the /mnt or my current Ubuntu installation was much smaller when I refreshed the disk analyzer. Now I hope I can logon to that installation as normal. This is a set of instructions and a thread I will keep. Still crossing my fingers when I logon again.

Thanks a million!!

:guitar:

---

### Post by PayPaul on 2011-10-09
Update: It worked. The logon problem was definitely caused by a low disk space problem. Hooray! 

Now I can do my clean install....when the new release comes out on the 14th. Wubi is getting old real fast. Windows will have to be redone too on a cleaned out partition.

Thanks again BcBc!

---

### Post by bcbc on 2011-10-09
Great that it works.

Note that the backup you moved is probably incomplete if you ran out of space while making it. With a wubi install, it's easier just to backup the root.disk from Windows. (It's not efficient, but you can easily copy it back over to restore).

---

### Post by PayPaul on 2011-10-09
> **bcbc said:**
> Great that it works.

Note that the backup you moved is probably incomplete if you ran out of space while making it. With a wubi install, it's easier just to backup the root.disk from Windows. (It's not efficient, but you can easily copy it back over to restore).

When I do the "real" install like someone above mentioned I won't really have that issue. I've backuped my packages in Synaptic as a Markings file on another drive. Now I'll just find my Mozilla profile and I should be done. One of the problems i keep running into at boot is a busybox issue. I suspect that's a Wubi problem. I type in exit a few time and I'm able to boot into Ubuntu. I never had it that easy with Windows but the Windows7 needs to be reinstalled as well for access to certain programs. It was a real mess when I did the recent re-installation of it and didn't reformat that windows partition. After that the new installation of Ubuntu using the new release will have its own partition to play around in not a virtual disk. This thread and that LiveCD session did provide a great learning experience no matter how torturous it was at time. 

You've been a great help.

---

