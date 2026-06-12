---
title: "Can't run executable file marked 777 on ext4 partition"
date: 2012-04-11
forum: General Help
---

### Post by JohnSuperDoe on 2012-04-11
Hi,

I know this may sound like a total n00b question, but I screen the forum for this problem and no solution is working.

**I can't run an executable file on my Ubuntu 11.10 setup.**  This file is NOT a Windows file but a Linux executable. The file is marked as 777 and is located in my Home directory which is on an ext4 partition.

When trying a double-click in Nautilus, I get "There is no application installed for executable files" and when I manually try to execute the file by typing "./filename" I get "bash: ./filename: Permission denied"

My user has admin right and is the owner of the file. 

This very same file work perfectly when run by a different admin user or on my Mint 12 computer.

My fstab look like this : 

```
proc                                        /proc        proc  nodev,noexec,nosuid  0  0  
UUID=087ed226-70aa-40c9-b861-5be4e4e7dc99   /            ext4  errors=remount-ro    0  1  
/dev/mapper/cryptswap1                      none         swap  sw                   0  0  
/dev/sda6                                   /media/sda6  ext4  users,user,user_xattr           0  0  
```Any ideas?

Thanks a lot in advance!

---

### Post by kiirokurisu on 2012-04-11
Can you show the output of an ls -l in the directory containing the executable?

---

### Post by dcstar on 2012-04-12
> **JohnSuperDoe said:**
> 
.........
This very same file work perfectly when run by a different admin user or on my Mint 12 computer.


Is the Mint computer 32 or 64-bit, and is the Ubuntu system the same?

---

### Post by JohnSuperDoe on 2012-04-12
> **kiirokurisu said:**
> Can you show the output of an ls -l in the directory containing the executable?

Hi kiirokurisu,

Sure! Here it is: 

```
-rwxrwxrwx 1 john john     4205 2012-04-11 13:58 com.living-e.timeEdition.plist
-rwxrwxrwx 1 john john     2785 2012-01-06 10:14 com.living-e.timeEdition (UbuntuJob's conflicted copy 2012-04-11).plist
-rwxrwxrwx 1 john john      992 2009-03-17 08:48 COPYING.txt
-rwxrwxrwx 1 john john    35146 2008-09-25 06:23 LICENSE.txt
drwxrwxrwx 4 john john     4096 2012-04-11 14:19 Resources
-rwxrwxrwx 1 john john  7138124 2011-11-28 11:26 timeEdition1.1.6-linux.tgz
-rwxrwxrwx 1 john john    19456 2012-04-10 15:55 timeEditionData.edb
-rwxrwxrwx 1 john john    13312 2012-02-01 16:56 timeEditionData (UbuntuJob's conflicted copy 2012-04-11).edb
-rwxrwxrwx 1 john john 11544655 2011-11-10 15:47 timeEditionLinux
-rwxrwxrwx 1 john john  2306924 2009-05-01 09:40 timeEdition_Manual.pdf 
```

The executable is "timeEditionLinux"

Thanks!

---

### Post by JohnSuperDoe on 2012-04-12
Hi dcstar,

> **dcstar said:**
> Is the Mint computer 32 or 64-bit, and is the Ubuntu system the same?

The Mint 12 computer is based on Ubuntu 11.10 64bit. 

The Ubuntu 11.10 which have the problem is 32 bit.

Thanks!

---

### Post by JohnSuperDoe on 2012-04-17
I'm still clueless on how to fix this.

Anybody saw a similar issue ?

---

### Post by The Cog on 2012-04-17
What's the output of these two commands?
The first tells us your machine architeture, the second tells us the file type.
```
uname -a
file timeEditionLinux
```

---

### Post by Bobhuber on 2012-04-17
> **JohnSuperDoe said:**
> Hi,

I know this may sound like a total n00b question, but I screen the forum for this problem and no solution is working.

**I can't run an executable file on my Ubuntu 11.10 setup.**  This file is NOT a Windows file but a Linux executable. The file is marked as 777 and is located in my Home directory which is on an ext4 partition.

When trying a double-click in Nautilus, I get "There is no application installed for executable files" and when I manually try to execute the file by typing "./filename" I get "bash: ./filename: Permission denied"

My user has admin right and is the owner of the file. 

This very same file work perfectly when run by a different admin user or on my Mint 12 computer.

My fstab look like this : 

```
proc                                        /proc        proc  nodev,noexec,nosuid  0  0  
UUID=087ed226-70aa-40c9-b861-5be4e4e7dc99   /            ext4  errors=remount-ro    0  1  
/dev/mapper/cryptswap1                      none         swap  sw                   0  0  
/dev/sda6                                   /media/sda6  ext4  users,user,user_xattr           0  0  
```Any ideas?

Thanks a lot in advance!
To make a long story short try adding the exec flag to your external partition in fstab
 /media/sda6  ext4  users,user,user_xattr ,exec

---

### Post by dcstar on 2012-04-18
> **JohnSuperDoe said:**
> Hi dcstar,



The Mint 12 computer is based on Ubuntu 11.10 64bit. 

The Ubuntu 11.10 which have the problem is 32 bit.

Thanks!

You **cannot** run 64-bit binaries on 32-bit systems.

---

### Post by JohnSuperDoe on 2012-04-19
> **The Cog said:**
> What's the output of these two commands?
The first tells us your machine architeture, the second tells us the file type.
```
uname -a
file timeEditionLinux
```

Sure!

**uname -a: **
```
Linux Ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
```

**file timeEditionLinux: **
```
timeEditionLinux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
```

Thanks for your help!

---

### Post by jwbrase on 2012-04-19
So much for the "trying to run a 64-bit executable on a 32-bit system" theory. The executable is 32-bit, so that's not your problem.

---

### Post by The Cog on 2012-04-19
Maybe the home partition is mounted noexec. What's the output of this command? ```
mount
```
Also, I wonder if there are any extended attributes. What's the output of ```
lsattr timeEditionLinux
```

---

### Post by JohnSuperDoe on 2012-04-19
> **Bobhuber said:**
> To make a long story short try adding the exec flag to your external partition in fstab
 /media/sda6  ext4  users,user,user_xattr ,exec

I tried this and it doe not work.

Thanks anyways

---

### Post by JohnSuperDoe on 2012-04-19
> **The Cog said:**
> Maybe the home partition is mounted noexec. What's the output of this command? ```
mount
```Also, I wonder if there are any extended attributes. What's the output of ```
lsattr timeEditionLinux
```

Here's the output ofthose commands:

**mount: **
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /media/sda6 type ext4 (rw,noexec,nosuid,nodev,user_xattr,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /media/sda6/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sdb on /media/ED7C-C40B type vfat (rw,nosuid,nodev,uid=1002,gid=1002,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

```
[B]
lsattr timeEditionLinux[/B] **:**
```
-----------------e- timeEditionLinux
```

Thanks!

---

### Post by matt_symes on 2012-04-19
Hi

Library problems can cause this as well so....

..as well as the Cog's suggestion to check the extended attributes, from a terminal, navigate to the directory containing timeEditionLinux and type

```
ldd timeEditionLinux
```

Copy and paste the entire results  back here.

Kind regards

---

### Post by gandalf3 on 2012-04-19
if you right click on the .exe in nautilus, and go to properties>permissions is the check box "allow executing file as executable?" checked? if it's not check it and try double clicking on the .exe again
hope this helps!

---

### Post by JohnSuperDoe on 2012-04-19
> **matt_symes said:**
> Hi

Library problems can cause this as well so....

..as well as the Cog's suggestion to check the extended attributes, from a terminal, navigate to the directory containing timeEditionLinux and type

```
ldd timeEditionLinux
```Copy and paste the entire results  back here.

Kind regards

Hi Matt,Here's my result.[B]

ldd timeEditionLinux: [/B]

```
    not a dynamic executable
```

thank you

---

### Post by JohnSuperDoe on 2012-04-19
> **gandalf3 said:**
> if you right click on the .exe in nautilus, and go to properties>permissions is the check box "allow executing file as executable?" checked? if it's not check it and try double clicking on the .exe again
hope this helps!

Hi Gandalf,

Of course, that was one of the first thing I looked for when troubleshooting. 

I don't even have the "allow executing file as executable?" checkbox like I do on the Mint machine. I only have a kind of grid of read, write and execute checkboxes for the owner, group and Others.

They are all checked.

---

### Post by matt_symes on 2012-04-19
Hi

Where did you download the file from ? I would like to take a look.

Kind regards

---

### Post by JohnSuperDoe on 2012-04-19
> **matt_symes said:**
> Hi

Where did you download the file from ? I would like to take a look.

Kind regards

I've got this time tracker from here: [URL="http://www.timeedition.com/en/downloads/index.html"]http://www.timeedition.com/en/downloads/index.html
[/URL] 

Note that, I renamed the executable from "timeEdition" to "timeEditionLinux" to avoid confusion with the Windows version. This is because I often switch from machine to machine and continue to track my time.

---

### Post by matt_symes on 2012-04-19
Hi

I just downloaded it and extracted it with no problems. It will not work on my machine as it is looking for the gtk2.0 libraries. (I am using precise)

```
matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ ./timeEdition 
./timeEdition: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$
```I am not sure why ldd is saying it is non executable as the file is executable. ldd should be showing output similar to this.```


matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ ldd timeEdition 
        linux-gate.so.1 =>  (0xf7796000)
        libgtk-x11-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libgmodule-2.0.so.0 => not found
        libglib-2.0.so.0 => not found
        libgthread-2.0.so.0 => not found
        libgobject-2.0.so.0 => not found
        libgdk_pixbuf-2.0.so.0 => not found
        libpango-1.0.so.0 => not found
        libpangocairo-1.0.so.0 => not found
        libpangoft2-1.0.so.0 => not found
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf775f000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf775a000)
        libXi.so.6 => not found
        libXext.so.6 => not found
        libX11.so.6 => not found
        libstdc++.so.6 => not found
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf772d000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf770e000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7569000)
        /lib/ld-linux.so.2 (0xf7797000)
        libcairo.so.2 => not found
matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$
```I am also interested in why it works under another admin user as you stated in your first post. This may point to problems with your current user.

I just wanted to check something first though.

Open a terminal and copy and paste this into the terminal. Don't type it as it's too easy to make a mistake.

```
mkdir ~/temptimeEdition && cd $_ && wget http://sourceforge.net/projects/timeedition/files/timeEdition/1.1.6/timeEdition1.1.6-linux.tgz  && tar xvf time* && cd timeEdition* && ./timeEdition
```It will create a new directory and change to it, download the tar file, untar it, move to the untarred directory and attempt to run it.

Post back on what it says. Do you still get the permission denied error ?

I just wanted to clarify that you are currently running these tests in Ubuntu and not Lnux mint ?

Also when you post output back here please also _post the commands you typed_, as well as the output, between code tags like this.
```

matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ ls -l
total 11324
-rw-r--r-- 1 matthew matthew      992 Mar 17  2009 COPYING.txt
-rw-r--r-- 1 matthew matthew    35146 Sep 25  2008 LICENSE.txt
drwxr-xr-x 6 matthew matthew     4096 Apr  1  2009 Resources
-rwxrwxr-x 1 matthew matthew 11544655 Apr  1  2009 timeEdition
matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ 
```That way we get the entire context of what is happening on your PC.

> Hi Matt,Here's my result.[B]

ldd timeEditionLinux: [/B]

     ```
not a dynamic executable
```thank youThat is not so good and i would have preferred to see the entire context of what you typed.

Kind regards

---

### Post by JohnSuperDoe on 2012-04-20
[SIZE=4][SIZE=1]wait... [/SIZE]

It works!!! [/SIZE]

The only thing I've done to make this work is to add "exec" in my fstab as suggested by [Bobhuber]("http://ubuntuforums.org/member.php?u=945841") here: 

[I]"To make a long story short try adding the exec flag to your external partition in fstab
 /media/sda6  ext4  users,user,user_xattr ,exec"[/I]

I previously said that it was not working because after modifying the fstab, I did a "sudo mount -a" and the problem was still there.

Now, I just rebooted my machine and it's working now!  I don't get it. I thought that "mount -a" was supposed to "reload" the fstab. But apparently I was wrong. What I should have done instead  ?

I'd like to thank all of you for your help. 

[SIZE=2]You guys rock![/SIZE] :guitar:

---

### Post by JohnSuperDoe on 2012-04-20
> **matt_symes said:**
> I am also interested in why it works under another admin user as you stated in your first post. This may point to problems with your current user.

The admin user's home directory was not on the same sda6 drive as my user's directory. That might explain the exec issue that I had.

> **matt_symes said:**
> I just wanted to clarify that you are currently running these tests in Ubuntu and not Lnux mint ?

YES. Every tests in this thread was done on the Ubuntu machine.

> **matt_symes said:**
> Also when you post output back here please also _post the commands you typed_, as well as the output, between code tags like this.
```

matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ ls -l
total 11324
-rw-r--r-- 1 matthew matthew      992 Mar 17  2009 COPYING.txt
-rw-r--r-- 1 matthew matthew    35146 Sep 25  2008 LICENSE.txt
drwxr-xr-x 6 matthew matthew     4096 Apr  1  2009 Resources
-rwxrwxr-x 1 matthew matthew 11544655 Apr  1  2009 timeEdition
matthew@matthew-Aspire-7540:~/temptimeEdition/timeEdition 1.1.6$ 
```That way we get the entire context of what is happening on your PC.

That is not so good and i would have preferred to see the entire context of what you typed.

OK. I'll do that next time.

Thanks a LOT for your help!

---

