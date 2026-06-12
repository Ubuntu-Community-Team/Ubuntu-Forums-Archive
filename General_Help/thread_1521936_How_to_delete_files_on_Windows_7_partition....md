---
title: "How to delete files on Windows 7 partition..."
date: 2010-07-01
forum: General Help
---

### Post by r2rX on 2010-07-01
Hey guys,

I have Ubuntu 10.04 x64 installed and i've mounted both NTFS partitions. The first contains my Windows partition (with Windows 7 on it) and the second contains my backup partition. They are two seperate hardisks.

Now, i'm trying to delete files on my Windows partition, but the ability to 'Cut' is greyed out and there's no 'delete' option at all.

This only occurs on my Windows partition, but my Backup partition can execute and option; whether delete, cut etc.

I assume this is either a settings in Ubuntu or something about Windows that prevents alternate O/S's from messing around with it.

So how can I go about enabling the feature to delete from my Windows partition? The idea is to erase all Windows related stuff so I can reinstall Windows.

All the help is appreciated.

r2rX  :D

---

### Post by TeoBigusGeekus on 2010-07-01
Just use gparted and format your windows partition.

---

### Post by r_s on 2010-07-01
mount your partition using sudo.. and then run *sudo nautilus*.

---

### Post by TeoBigusGeekus on 2010-07-01
> **r_s said:**
> mount your partition using sudo.. and then run *sudo nautilus*.

It should be gksudo nautilus.

---

### Post by r_s on 2010-07-01
both work :)

---

### Post by TeoBigusGeekus on 2010-07-01
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Morbius1 on 2010-07-01
This is as good an explanation as any:

From the Ubuntu Documentation site: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> Graphical sudo

You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 

[COLOR=Blue]EDIT: Simultaneous posts, sorry.[/COLOR]
Now if someone can explain the difference between gksu ( which I've always used ) and gksudo .......

---

### Post by r2rX on 2010-07-01
I don't wish to format the drive. I would've done so through the Windows Installer. There are files which I want to save but won't fit on my Backup drive....so i'm manually placing all my content in one folder and erasing EVERYTHING else.

The feedback is appreciated. I'll let you know how it goes. :)

r2rX  :D

---

### Post by r2rX on 2010-07-02
I don't mean to cause trouble double-posting, but i'm using PySDM to mount my partitions. I'm not sure if this makes a difference.

r2rX  :)

---

### Post by Morbius1 on 2010-07-02
Why not post the output of the following commands so we can see what Pysdm has done to you:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

And identify the partition that is causing the problem.

---

### Post by r2rX on 2010-07-02
```
sudo blkid -c /dev/null

/dev/sda1: LABEL="Windows" UUID="F486FFA386FF6510" TYPE="ntfs" 
/dev/sda2: UUID="09f7dddf-2427-4fd1-849d-04b71ba8f66f" TYPE="ext4" 
/dev/sda3: TYPE="swap" 
/dev/sdb1: LABEL="Storage" UUID="C23A773E3A772E93" TYPE="ntfs" 
```


```
cat /etc/fstab

proc                                       /proc           proc  nodev,noexec,nosuid                                     0  0  
UUID=09f7dddf-2427-4fd1-849d-04b71ba8f66f  /               ext4  errors=remount-ro                                       0  1  
UUID=C23A773E3A772E93                      /media/Storage  ntfs  nls=iso8859-1,nosuid,umask=000,nodev,gid=1000,uid=1000  0  0  
UUID=F486FFA386FF6510                      /media/Windows  ntfs  nls=utf8,ro,umask=0222                                  0  0  
/dev/sda3    
```

I'm learning slowly-slowly....but I love linux...a beautiful operating system.

r2rX  :)

---

### Post by sidzen on 2010-07-02
To _r2rX_ --
Be Pane-Free and [PHP]dd if=/dev/zero of=/dev/sdx bs=4096 conv=notrunc,sync[/PHP] *x *being the designation for the drive in question
Thanks, _[TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094")_!
I'm learning more and more from the forums to which I belong -- never used gksudo before.  Aptitude is another I'm tryin gout and find useful.  
BTW, do you know of antiX?  Being from Greece, I thought you may.

---

### Post by Morbius1 on 2010-07-02
Open gedit as root:
```
gksu gedit /etc/fstab
```Replace this:
> UUID=C23A773E3A772E93                      /media/Storage  ntfs  nls=iso8859-1,nosuid,umask=000,nodev,gid=1000,uid=1000  0  0    With this:
```
UUID=C23A773E3A772E93   /media/Storage  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000 0 0
```Save the file, exit gedit, and back in the terminal type:
```
sudo umount /media/Storage
```Then:
```
sudo mount -a
```There's no need to reboot. Now see if you can read / write to that partition.

Note: the umask=000 is overkill since it's in the default, but I like to have it there anyway just in case somebody redefines what's in the default.

---

### Post by Morbius1 on 2010-07-02
Sorry about that I must be on some kind of drug flashback. It's the wrong partition:

Should be from this:
> UUID=F486FFA386FF6510                      /media/Windows  ntfs  nls=utf8,ro,umask=0222                                  0  0  To this:
```
 UUID=F486FFA386FF6510 /media/Windows ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000 0 0
```

Making the change to the storage partition wouldn't hurt either .

---

### Post by r2rX on 2010-07-02
The partition i'm actually trying to get access to is the 'Windows drive' (sda1).

But I applied the following to Windows (sda1) in fstab:

```
ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000 0 0
```

And it works! Hoorah!

I appreciate all the help guys.

Although, could someone explain to me what the problem was, in particular? I'm not familiar with the syntax and what they do/mean....

Sidzen, I'm not familiar of antiX....and i'm not in Greece :p

r2rX  :D

---

### Post by Morbius1 on 2010-07-02
>                               UUID=F486FFA386FF6510                      /media/Windows  ntfs   nls=utf8,[COLOR=Blue]ro[/COLOR],[COLOR=DarkGreen]umask=0222[/COLOR]                                  0  0                      [COLOR=Blue]ro - stands for read only

[/COLOR][COLOR=DarkGreen]umask=0222[/COLOR] - each one of those "2"'s turns off write to owner, group, and everyone else. 

Pysdm really really didn't want  you to write ( A write in the case of the partition itself means add or delete ) to that partition.

---

### Post by r2rX on 2010-07-02
I figured the 'ro' referred to read-only....funny enough, that was the first thing I tried changing in PySDM. But, even after disabling it (and the PySDM interface registered it) it was still on. Running PySDM with 'gksu' or 'gksudo' didn't do it either.

I think i'm gonna do some more research into the fstab syntax. :)

Thanks Morbius1 and everyone else. You've helped me one step closer to my knwoledge and comfort with Linux. :)

r2rX  :D

---

