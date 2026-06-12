---
title: "cannot execute in 12.04"
date: 2012-05-18
forum: General Help
---

### Post by goncalo.justino on 2012-05-18
Dear all,

I've just come across that apparently simple error that gets under my skin... Don't even know where to post this...

I've been using ubuntu daily at work, both server and desktop, but essentially via cli, since... 2007? Really not an expert but just a "used" user.

Now, i've just made a clean 12.04 install on a machine, and I can't execute one file that always worked well, it's actually mopac (from openmopac.net). So today, whenever I try to run
/opt/mopac/MOPAC2009.exe <file.dat>
I get
bash: /opt/mopac/MOPAC2009.exe: No such file or directory

My walkings so far: environment variables, location, folder and file permissions, aliases, csh instead of bash, updates, new packages, removing and resinstalling packages... 2 days doing nothing but this, to no avail.

the one difference: i've always had one single partition, now i have /, /home and /opt partitions. they're all ext4, but another 11.10 pc here is ext4 (1 partition only) and it's running ok.

could this disk setting explain this ? why ?

anyway I can fix this without reinstalling again ?

really, ANY comments are welcome

all the best,
justin

[if curious, mopac it's a small executable that has allways run well up to yesterday on all machines and distros and configurations, no pre-requisites required other than being at a /opt/mopac folder, it reads in a text file, makes a bunch of computations and writes some text files.]

---

### Post by Cheesemill on 2012-05-18
What are the outputs of the following please:
```
ls -l /opt/mopac
```
```
mount
```

---

### Post by goncalo.justino on 2012-05-18
```
ls -l /opt/mopac/
total 5820
-rwxrwxr-x 1 goncalo goncalo  327180 May 18 10:48 1HHO.pqr.initial.dat
-rwxrwxr-x 1 goncalo goncalo     409 Feb  3  2007 Example data set.mop
-rwxrwxr-x 1 goncalo goncalo      80 Feb 15  2007 gmolden
-rwxrwxr-x 1 goncalo goncalo    2637 May 19  2010 Installation instructions.txt
-rwxrwxr-x 1 goncalo goncalo     335 Feb 15  2007 Molden.txt
-rwxrwxrwx 1 goncalo goncalo 5603232 Feb  6 11:21 MOPAC2009.exe
-rwxrwxr-x 1 goncalo goncalo      84 Feb 15  2007 mopac.csh
drwxrwxrwx 2 goncalo goncalo    4096 May 18 10:51 older
-rwx--x--x 1 goncalo goncalo      16 May 18 10:48 password_for_mopac2009

```

```
 mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb6 on /home type ext4 (rw)
/dev/sdb5 on /opt type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/goncalo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=goncalo)

```

---

### Post by Gyokuro on 2012-05-18
You have downloaded a Windows executable  - mobac2009 for linux is the file you should download :-)

---

### Post by Cheesemill on 2012-05-18
> **Gyokuro said:**
> You have downloaded a Windows executable  - mobac2009 for linux is the file you should download :-)
The linux executable ***is*** called MOPAC2009.exe

---

### Post by goncalo.justino on 2012-05-18
> **Gyokuro said:**
> You have downloaded a Windows executable  - mobac2009 for linux is the file you should download :-)

not the case, really. it's called MOPAC2009.exe but it works on linux :D
[though i've  just redownloaded and tested to make sure i hadn't had some windows mental relapse]

---

### Post by haresear on 2012-05-18
The bash message suggests the argument <file.dat> does not exist. Are you sure that file exists? Could it have a non-visible character in the name (like a space at the end)?

---

### Post by goncalo.justino on 2012-05-18
> **haresear said:**
> The bash message suggests the argument <file.dat> does not exist. Are you sure that file exists? Could it have a non-visible character in the name (like a space at the end)?

Hi haresear,


The <file.dat> was just my writing in the post.

If I put a example.dat file and run /opt/mopac/MOPAC2009.exe I get the same "complain", whether I run it from the dat file folder, from the mopac folder, or when i put the dat file in the mopac folder.

Anyway, thanks !

---

### Post by btindie on 2012-05-18
That's a 32bit binary, what arch are you running on? - "uname -i" if it's x86_64 then you may need some 32bit compatibility libraries.

Also, make sure the file has the executable bit set, that's the problem with zip. -  "chmod a+x /opt/mopac/MOPAC2009.exe".

Then try running it again.

---

### Post by haresear on 2012-05-18
@btindie: I'm looking at post #3, and the ls output says to me that MOPAC2009.exe is executable:

-rwxrwxrwx 1 goncalo goncalo 5603232 Feb  6 11:21 MOPAC2009.exe

Am I missing something?
(if the file wasn't executable, the error message would be "permission denied")

@goncalo.justino: Yes, I realize what you meant by <file.dat>, but it still seems like it can't find the dat file with the name you are providing to MOPAC2009.exe. If you are not using a path, then the dat file needs to be in the folder where you are issuing the command. I would suggest using 'ls <file.dat>' to be sure that the file exists in the folder you are using, or include the full path name to the dat file.

---

### Post by mineral2511 on 2012-05-23
> **btindie said:**
> That's a 32bit binary, what arch are you running on? - "uname -i" if it's x86_64 then you may need some 32bit compatibility libraries.


Thank you, I had the exact same problem as the original poster and installing ia32-libs solved it for me.

---

