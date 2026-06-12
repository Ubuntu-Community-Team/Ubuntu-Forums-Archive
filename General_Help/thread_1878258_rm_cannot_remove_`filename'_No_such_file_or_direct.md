---
title: "rm: cannot remove `filename': No such file or directory"
date: 2011-11-09
forum: General Help
---

### Post by venetis on 2011-11-09
I'm using rsnapshot and some files in the snapshots folder cannot be deleted...

Here is the strace of rm:
```
execve("/bin/rm", ["rm", "filename"], [/* 44 vars */]) = 0
brk(0)                                  = 0x8876000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7712000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=66555, ...}) = 0
mmap2(NULL, 66555, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7701000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\222\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1544392, ...}) = 0
mmap2(NULL, 1554968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7585000
mmap2(0xb76fb000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x176) = 0xb76fb000
mmap2(0xb76fe000, 10776, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb76fe000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7584000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb75848d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb76fb000, 8192, PROT_READ)   = 0
mprotect(0x8053000, 4096, PROT_READ)    = 0
mprotect(0xb7733000, 4096, PROT_READ)   = 0
munmap(0xb7701000, 66555)               = 0
brk(0)                                  = 0x8876000
brk(0x8897000)                          = 0x8897000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2919792, ...}) = 0
mmap2(NULL, 2097152, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7384000
close(3)                                = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
fstatat64(AT_FDCWD, "filename", 0x8877ab0, AT_SYMLINK_NOFOLLOW) = -1 ENOENT (No such file or directory)
geteuid32()                             = 1000
fstatat64(AT_FDCWD, "filename", 0xbf8f63c0, AT_SYMLINK_NOFOLLOW) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7711000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7711000, 4096)                = 0
open("/usr/share/locale/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=619, ...}) = 0
mmap2(NULL, 619, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7711000
close(3)                                = 0
write(2, "rm: ", 4rm: )                     = 4
write(2, "cannot remove `filename'", 27cannot remove `filename') = 27
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, ": No such file or directory", 27: No such file or directory) = 27
write(2, "\n", 1
)                       = 1
close(0)                                = 0
close(1)                                = 0
close(2)                                = 0
exit_group(1)                           = ?
```

I've run fsck and everything seems fine...

Any suggestions?

---

### Post by carranty on 2011-11-09
I don't know what the strace means but I've compared it to the strace of my rm and its the same, so I'm guessing your system is fine.  This error message usually means your not specifying the file path correctly.

How exactly are you trying to delete the files, from the command line using rm?  Are you sure you're specifying the right directory? Can you use the 'ls -l' command for the file your trying to delete.  Please paste both the command and the output to this thread.

---

### Post by mikaelcrocker on 2011-11-09
I would have to touch on previous reply.  I would look into the 'filename' either being used as a variable, or if you're literally trying to delete a file or directory called 'filename'.  One thing you've probably considered is the difference between rm and rmdir and some of rules with both, but if you haven't, well, look what I did :)

In some of your debug methods, try hardcoding a couple things just to ensure it's working to narrow down causes and symptoms.

---

### Post by carranty on 2011-11-09
I hadn't realised until reading mikael's post but you're trying to delete a file called 'filename'.  This is a little odd, are you by chance copying and pasting from a tutorial on deleting files?  If so, be sure to change the word *filename* to the name of the file you're trying to delete, also, make sure you're in the right directory.

For example say I'd used rsnapshot to back up the file *foo *located in my *Documents* folder.  To delete it I would navigate to the appropriate directory

[I]cd /.snapshots/daily.7/home/carranty/Documents

[/I]and then delete the file using rm

[I]rm foo

[/I]Note the directory will be different for you, but you get the idea.

---

### Post by matt_symes on 2011-11-09
Hi
[FONT=monospace]
[/FONT]> fstatat64(AT_FDCWD, "**filename**", 0x8877ab0, AT_SYMLINK_NOFOLLOW) = -1 ENOENT (No such file or directory)Indeed. If it can't stat it it will never unlink it.

Kind regards

---

### Post by efflandt on 2011-11-09
Are you sure that there are not spaces in the filename (in which cases the filename either needs to be quoted like **"file name"** or each space escaped with backslash like **file\ name**).

Or try bash filename completion by typing **rm**, first few characters of filename, and then **Tab** key.  That should pick up even something like an invisible trailing space.

---

### Post by venetis on 2011-11-09
> **carranty said:**
> I don't know what the strace means but I've compared it to the strace of my rm and its the same, so I'm guessing your system is fine.  This error message usually means your not specifying the file path correctly.

How exactly are you trying to delete the files, from the command line using rm?  Are you sure you're specifying the right directory? Can you use the 'ls -l' command for the file your trying to delete.  Please paste both the command and the output to this thread.

I'm using 'rm -f' to delete it. I'm specifying the right directory. Here is what 'ls -l' give:
```
ls: cannot access 'OI&#65533;: No such file or directory
ls: cannot access 11-visa.pdf: No such file or directory
total 0
-????????? ? ? ? ?                ? filename
-????????? ? ? ? ?                ? ?'OI?
```

For some reason, the file names are corrupted... There are two files I want to delete: filename and the other weird-named one. Cannot delete any of them...

---

### Post by venetis on 2011-11-09
> **mikaelcrocker said:**
> I would have to touch on previous reply.  I would look into the 'filename' either being used as a variable, or if you're literally trying to delete a file or directory called 'filename'.  One thing you've probably considered is the difference between rm and rmdir and some of rules with both, but if you haven't, well, look what I did :)

In some of your debug methods, try hardcoding a couple things just to ensure it's working to narrow down causes and symptoms.

'filename' is the actual name of the file...

---

### Post by venetis on 2011-11-09
> **efflandt said:**
> Are you sure that there are not spaces in the filename (in which cases the filename either needs to be quoted like **"file name"** or each space escaped with backslash like **file\ name**).

Or try bash filename completion by typing **rm**, first few characters of filename, and then **Tab** key.  That should pick up even something like an invisible trailing space.

There is no space. Using the bash file name completion gives me the correct file name: 'filename'.

---

### Post by matt_symes on 2011-11-09
Hi

You do have a problem there. This is an extX file system ? 

Can you get the inodes for the files.

In the same directory and instead of ls -l try

```
ls -i
```Post back results.

Kind regards

---

### Post by venetis on 2011-11-09
> **matt_symes said:**
> Hi

You do have a problem there. Can you get the inodes for the files.

In the same dirctory and instead of ls -l try

```
ls -i
```

Post back results.

Kind regards

Here are the results for 'ls -i'
```
ls: cannot access 'OI&#65533;: No such file or directory
ls: cannot access filename: No such file or directory
? filename  ? ?'OI?
```

---

### Post by matt_symes on 2011-11-09
Hi

> **venetis said:**
> Here are the results for 'ls -i'
```
ls: cannot access 'OI&#65533;: No such file or directory
ls: cannot access filename: No such file or directory
? filename  ? ?'OI?
```

The inodes for those files are corrupted.

What is the name of the directory those files are in ?
Are there any other files in that directory ?
Are they corrupted and do you need them ?

From this directory's parent - ie the parent directory of the files 'filename' and 'OI&#65533;' - type

```
ls -i
```to get the inode of the directory that holds those two files.

Kind regards

---

### Post by venetis on 2011-11-09
> **matt_symes said:**
> What is the name of the directory those files are in ?
Are there any other files in that directory ?
Are they corrupted and do you need them ?

From this directory's parent - ie the parent directory of the files 'filename' and 'OI&#65533;' - type

```
ls -i
```to get the inode of the directory that holds those two files.

I don't need the files. The directory name is 'temp' and it only contains the files 'filename' and 'OI&#65533;'. I don't want to retrieve them -- just to remove them...

I got the inode for the directory. Now what? :)

---

### Post by matt_symes on 2011-11-09
Hi

This is an extX file system ? If not then the information below is irrelevant.

Post the inode number back here. Make sure its the correct number.

As i want to make sure it's correct, please post the output of

```
ls -i
```from the parent directory of the files. Just post the entry for the specific directory if you want.

Also post the results of this command back here

```
df -h
```I think you may have to delete the parent directory.

You can try 
```

rm -rf <directory_name>
```and 

```
rmdir <directory_name>
```but i suspect they will return errors because of the corrupted files inside.

Therefore i think you best bet for success may be to delete the inode of the parent directory using debugfs.

For this you will need the inode number and device node.

Kind regards

---

### Post by venetis on 2011-11-09
> **matt_symes said:**
> Hi

This is an extX file system ? If not then the information below is irrelevant.

Post the inode number back here. Make sure its the correct number.

As i want to make sure it's correct, please post the output of

```
ls -i
```from the parent directory of the files. Just post the entry for the specific directory if you want.

Also post the results of this command back here

```
df -h
```I think you may have to delete the parent directory.

You can try 
```

rm -rf <directory_name>
```and 

```
rmdir <directory_name>
```but i suspect they will return errors because of the corrupted files inside.

Therefore i think you best bet for success may be to delete the inode of the parent directory using debugfs.

For this you will need the inode number and device node.

'rm -rf' and 'rmdir' do not work.

The inode is 1966090.

The device is /dev/sda2.

The output of 'df -h' is:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              33G  3.7G   27G  13% /
udev                  2.0G  4.0K  2.0G   1% /dev
tmpfs                 791M  800K  790M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  996K  2.0G   1% /run/shm
/dev/sda4             145G   26G  112G  19% /home
/home/XXX/.Private
                      145G   26G  112G  19% /home/XXX
```

---

### Post by matt_symes on 2011-11-09
Hi

> 'rm -rf' and 'rmdir' do not work.

I'm beginning to think you may have the same issue with debugfs.

Let me get back to you.

Kind regards

---

### Post by erind on 2011-11-09
> **venetis said:**
> 'rm -rf' and 'rmdir' do not work.

The inode is 1966090.

...

Maybe 'find' command will come in handy in this case. Using the problematic directory inode number, you can try:

```
find . -inum 1966090 -exec rm -rf {} \;
```Make sure the inode number is the *correct *one. The command deletes stuff!

---

### Post by venetis on 2011-11-09
> **erind said:**
> ```
find . -inum 1966090 -exec rm -rf {} \;
```Make sure the inode number is the *correct *one. The command deletes stuff!

Unsuccessful...

Here is what I get:
```
rm: cannot remove `./temp': Directory not empty
find: `./temp/\037\'OI\360': No such file or directory
find: `./temp/filename': No such file or directory
```

---

### Post by erind on 2011-11-09
> **venetis said:**
> Unsuccessful...

Here is what I get:
```
rm: cannot remove `./temp': Directory not empty
find: `./temp/\037\'OI\360': No such file or directory
find: `./temp/filename': No such file or directory
```

It seems like there is a disk error or filesystem problem. I'd reboot and start with a **fsck** check for consistency problems. I'd give more help if I had more experience in disk/filesystem issues.

---

### Post by venetis on 2011-11-09
> **erind said:**
> It seems like there is a disk error or filesystem problem. I'd reboot and start with a **fsck** check for consistency problems. I'd give more help if I had more experience in disk/filesystem issues.

fsck reports no error when run...

Disk is healthy according to the disk utility...

---

### Post by Bobhuber on 2011-11-09
> **venetis said:**
> I'm using 'rm -f' to delete it. I'm specifying the right directory. Here is what 'ls -l' give:
```
ls: cannot access 'OI&#65533;: No such file or directory
ls: cannot access 11-visa.pdf: No such file or directory
total 0
-????????? ? ? ? ?                ? filename
-????????? ? ? ? ?                ? ?'OI?
```For some reason, the file names are corrupted... There are two files I want to delete: filename and the other weird-named one. Cannot delete any of them...
You can find this in the  synaptic package manager . I've never had to use it but it  may help.
nautilus-filename-repairer

---

### Post by stevepburke on 2012-08-30
Try using:

touch <file>

then you should be able to remove it:

rm <file>

---

### Post by dcstar on 2012-08-31
> **venetis said:**
> I don't need the files. The directory name is 'temp' and it only contains the files 'filename' and 'OI&#65533;'. I don't want to retrieve them -- just to remove them...


Then stop wasting your time with the "advice" in this thread and simply do:
```
rm -i *
```
You will be prompted to delete each file one by one, say "No" to the ones you want to keep and "Yes" to these corrupted filenames when they eventually appear.

---

