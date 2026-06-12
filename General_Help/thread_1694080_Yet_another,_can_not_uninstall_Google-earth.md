---
title: "Yet another, can not uninstall Google-earth"
date: 2011-02-23
forum: General Help
---

### Post by Bryan55 on 2011-02-23
There are a lot of threads here on this and I have been cutting and pasting may way through all of them with out joy.

First. I installed GE following the instructions from here [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)
It worked fine until yesterday when I got an error saying. Could not launch application. Failed to execute child process "/home/bryan/google-earth//googleearth"(Permission denied)

Not sure what the problem was so decided to uninstall and try out GE 6
However no matter what I try I get "Could not find a usable uninstall program. Aborting" as below.

bryan@Bydand:~$ cd /home/bryan/google-earth
bryan@Bydand:~/google-earth$ sudo su
root@Bydand:/home/bryan/google-earth# ./uninstall
Could not find a usable uninstall program. Aborting.

Thanks for any help.
Bryan.

---

### Post by mikewhatever on 2011-02-23
I'd first check the permission: ls -l /home/bryan/google-earth//googleearth; but if you are set on uninstalling, just remove the goole-earth folder: rm -r /home/bryan/google-earth.

---

### Post by Bryan55 on 2011-02-24
I have checked the permissions.

bryan@Bydand:~$ ls -l /home/bryan/google-earth//googleearth
-rw------- 1 bryan bryan 1308 2010-09-14 22:09 /home/bryan/google-earth//googleearth


This is new ground for me so not sure what this means.

Chees
Bryan.

PS  sorry for taking so long to get back as I had forgotten to subscribe to my thread.

---

### Post by Vaphell on 2011-02-24
i think that folders should have executable bit set

from wikipedia:
> The execute permission, which grants the ability to execute a file. This permission must be set for executable binaries (for example, a compiled C++ program) or shell scripts (for example, a Perl program) in order to allow the operating system to run them. **When set for a directory, this permission grants the ability to traverse its tree in order to access files or subdirectories**, but not see the content of files inside the directory (unless read is set).

did you play with chmod (most likely 600) by any chance?

```
chmod +x <name_of_directory>
```

---

### Post by scouser73 on 2011-02-24
To install Google Earth 6, enter this command into Terminal > sudo apt-get install lsb-core

Now download Google Earth 6 from [http://www.google.com/earth/index.html]("http://www.google.com/earth/index.html")

[COLOR="Red"]**[/COLOR] Make sure you download the **.deb** file [COLOR="red"]**[/COLOR]

Install and run, it will work.

---

### Post by WorMzy on 2011-02-24
I've never used Google Earth myself, but would expect that to have the executable bit set. Open a terminal, run this, and then try launching it again.

```
chmod u+x /home/bryan/google-earth/googleearth
```

As for the uninstall problem, removing the directory would be the easiest and best method, just be careful if you do it via the terminal -- rm will not move files to the trashcan, so anything you delete that way will not be easy to recover.

---

### Post by Bryan55 on 2011-02-24
> did you play with chmod (most likely 600) by any chance?If I have it's been unknowingly.

I tried > chmod u+x /home/bryan/google-earth/googleearthThis stopped the Error but GE does not start.

I had picked up on the "lsb-core" thing in other threads but thanks anyway.

Bryan.

---

### Post by Bryan55 on 2011-02-24
I have found that googleearth-bin file was not marked as executable so I tick the box and found it would launch. However it would only launch once. Then I found if I untick the box and re-ticked it it would launch again but only one time.
How can I make it permanent?
Edit   Ignore the above it's i time thing if I wait about a minute it will restart.

Bryan.

---

### Post by WorMzy on 2011-02-24
Oh dear, you're not using an NTFS partition as your home by any chance, are you?

What's the output of
```
mount
```

---

### Post by Bryan55 on 2011-02-24
WorMzy wash your mouth out with soapy water

bryan@Bydand:~$ mount
/dev/md1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /dev/shm type tmpfs (rw)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/md2 on /home type ext4 (rw,commit=0)
/dev/md0 on /boot type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bryan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bryan)

But what is this about?       rw,errors=remount-ro,commit=0)

Bryan.

---

### Post by WorMzy on 2011-02-24
Haha, sorry, but I've seen it before.

Those are fairly standard / mount options, although the "commit=0" is redundant, and just means that the ext4 filesystem will write any pending data to the disk every five seconds.

The errors and rw options are fairly self-explanatory. If the filesystem detects an error with itself, it will be unmounted, then re-mounted in read-only mode. rw just means the filesystem is mounted in read-write mode.

What's the output of ```
ls -l /home/bryan/google-earth/googleearth-bin
``` (change that to the correct address if it's not there)

---

### Post by Bryan55 on 2011-02-24
Hi WorMzy
Did you notice my edit 2 posts ago GE seems to be starting every time now. I just need to wait 40 seconds or so after shutting it down before trying again which is probable normal.

Heres the result of your code anyway.
bryan@Bydand:~$ ls -l /home/bryan/google-earth/googleearth-bin
-rwx--x--x 1 bryan bryan 3876 2010-09-14 22:09 /home/bryan/google-earth/googleearth-bin


Thanks for all the help.
Bryan.

---

### Post by WorMzy on 2011-02-24
I saw it, but misread it. I thought that the "allow executing" checkbox was unchecking itself, which is why I asked about the NTFS partition.

Well, glad it's working now. :)

---

