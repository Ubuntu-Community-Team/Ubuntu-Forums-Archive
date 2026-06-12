---
title: "Hard drive full"
date: 2011-11-08
forum: General Help
---

### Post by mblack3nd on 2011-11-08
Hello

Excuse my noob-yness. I have been having a hard time with my ubuntu recently. Sometimes it is difficult to log-in and when I do log-in, I get a notice that my there is only "24MB" or sometimes of space left. I ran Gparted and it shows more than 1GB. 

I haven't downloaded a bunch of music or anything like that...most of my files are on a different partition. But it is nearly impossible to watch more than 3 secs of a youtube video etc.

Hope this makes sense and hopefully you can help me figure out what is wrong (like if there are actually a bunch of files that came from somewhere or whatever)

---

### Post by collisionystm on 2011-11-08
> **mblack3nd said:**
> Hello

Excuse my noob-yness. I have been having a hard time with my ubuntu recently. Sometimes it is difficult to log-in and when I do log-in, I get a notice that my there is only "24MB" or sometimes of space left. I ran Gparted and it shows more than 1GB. 

I haven't downloaded a bunch of music or anything like that...most of my files are on a different partition. But it is nearly impossible to watch more than 3 secs of a youtube video etc.

Hope this makes sense and hopefully you can help me figure out what is wrong (like if there are actually a bunch of files that came from somewhere or whatever)

open a terminal

sudo apt-get clean

This will remove the install files of packages you installed from software center. Should make some space

---

### Post by mblack3nd on 2011-11-08
Cool did that...didn't notice anything dramatic happen (i.e. typed in the password and that was it) but hopefully that works

---

### Post by mblack3nd on 2011-11-08
Sadly...that didn't do much :'(

---

### Post by btindie on 2011-11-08
Please paste the output of **df -h** in code tags, above there's a hash sign #.

---

### Post by drs305 on 2011-11-08
Take a look at the following thread about investigating disk space issues. 

Most of the problems I've dealt with on these forums usually involve unemptied trash bins (your's and root's), large log files, and backups which are incorrectly made on / rather than the backup partition.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by mblack3nd on 2011-11-08
```
/dev/sda4              21G   20G  151M 100% /
udev                  1.5G  308K  1.5G   1% /dev
none                  1.5G  2.3M  1.5G   1% /dev/shm
none                  1.5G  224K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda5              89G   65G   25G  74% /media/Media
/dev/sda1              36G  4.0G   32G  12% /media/ME

```

---

### Post by mblack3nd on 2011-11-08
drs305,

I have gone through the guide and it didn't really help me much :(...thanks though!!!

---

### Post by blind2314 on 2011-11-08
Post the output of the following (ran from a terminal session):

```
cd /
sudo du -sh *
```

---

### Post by mblack3nd on 2011-11-08
```
4.0K	afs
5.4M	bin
57M	boot
0	cdrom
492K	dev
19M	etc
14G	home
0	initrd.img
0	initrd.img.old
372M	lib
16K	lost+found
69G	media
4.0K	mnt
163M	opt
du: cannot access `proc/10309/task/10309/fd/4': No such file or directory
du: cannot access `proc/10309/task/10309/fdinfo/4': No such file or directory
du: cannot access `proc/10309/fd/4': No such file or directory
du: cannot access `proc/10309/fdinfo/4': No such file or directory
0	proc
8.0K	recovery
8.5M	root
7.9M	sbin
4.0K	selinux
200K	srv
0	sys
632K	tmp
4.9G	usr
627M	var
0	vmlinuz
0	vmlinuz.old

```

---

### Post by blind2314 on 2011-11-08
> **mblack3nd said:**
> ```
4.0K    afs
5.4M    bin
57M    boot
0    cdrom
492K    dev
19M    etc
14G    home
0    initrd.img
0    initrd.img.old
372M    lib
16K    lost+found
69G    media
4.0K    mnt
163M    opt
du: cannot access `proc/10309/task/10309/fd/4': No such file or directory
du: cannot access `proc/10309/task/10309/fdinfo/4': No such file or directory
du: cannot access `proc/10309/fd/4': No such file or directory
du: cannot access `proc/10309/fdinfo/4': No such file or directory
0    proc
8.0K    recovery
8.5M    root
7.9M    sbin
4.0K    selinux
200K    srv
0    sys
632K    tmp
4.9G    usr
627M    var
0    vmlinuz
0    vmlinuz.old

```

So, as you can see, 14G of your space under / is being taken up by the /home directory (your home directory, as well as any other users besides root). I would start there and check for things that can be removed. You can repeat the above command with the /home directory, and it'll give you the culprits there as well.

```
cd /home
du -sh *
```

---

### Post by mblack3nd on 2011-11-08
OK...I have done that... in /home there is just /mblack3 with the same 14G...

when I do the same for /mblack3, it doesn't seem to show everything. That is, it doesn't look like the numbers add up to 14G

```

4.0K	bin
4.0K	Calibre Library
305M	Desktop
640K	Documents
148K	Downloads
104M	kdenlive
16K	keymappings
112K	Music
128K	output
12K	Pictures
4.0K	Public
4.0K	recover.sh~
8.0K	R-TT
4.0K	soundKonverter
50M	swiftweasel
10M	swiftweasel-3.0.10_intel-pgo_x86-ubuntu.tar.gz
4.0K	Templates
8.0K	Videos
4.0K	work

```

---

### Post by blind2314 on 2011-11-08
> **mblack3nd said:**
> OK...I have done that... in /home there is just /mblack3 with the same 14G...

when I do the same for /mblack3, it doesn't seem to show everything. That is, it doesn't look like the numbers add up to 14G

```

4.0K    bin
4.0K    Calibre Library
305M    Desktop
640K    Documents
148K    Downloads
104M    kdenlive
16K    keymappings
112K    Music
128K    output
12K    Pictures
4.0K    Public
4.0K    recover.sh~
8.0K    R-TT
4.0K    soundKonverter
50M    swiftweasel
10M    swiftweasel-3.0.10_intel-pgo_x86-ubuntu.tar.gz
4.0K    Templates
8.0K    Videos
4.0K    work

```

Then it's likely a hidden directory that is taking up the space. As asked/mentioned before, have you cleaned out your user's "trash bin"?

---

### Post by BillyBoa on 2011-11-08
What about the old kernels in the boot directory? Sometimes they are not cleaned by clean.

---

### Post by mblack3nd on 2011-11-08
I think so yes

---

### Post by oldfred on 2011-11-08
When I run this from home, my .wine is the largest hidden folder.

sudo du -hc --max-depth=1

---

### Post by mblack3nd on 2011-11-08
not sure about old kernels in boot directory... but I did find 10G worth of files in .mozilla...deleted them and all is better

thanks!

---

### Post by btindie on 2011-11-11
If you run the following command it'll list the size of all folders sorted numerically including the 'hidden' dot folders.
```
cd $HOME
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
```

---

