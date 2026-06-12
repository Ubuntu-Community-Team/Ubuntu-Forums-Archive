---
title: "pdf file won't go away."
date: 2011-12-05
forum: General Help
---

### Post by alextockey on 2011-12-05
I have two pdf. files in my downloads folder that won't open, which I am having trouble deleting. 

First, I tried using the GUI by dragging them to the trash. I did not receive a prompt, the files simply would not move there.

Then I used terminal to remove them with:$  [FONT=Courier New]rm -rv file.pdf
[/FONT]terminal would say:[FONT=Courier New] removed 'file.pdf' [/FONT]
but when I use ls, it shows that the file is still there. I've also tried this under superuser, with no results.

Does anyone know how to override this unfortunate problem?
[FONT=Courier New]
[/FONT]

---

### Post by killermist on 2011-12-05
Try "rm -fv file.pdf" instead.
That way even if the permissions on the file were somehow write-protected, it should still work (-f option is "force")

Another possibility is that the filesystem has been mounted in read-only mode, but let's shelve that until you try the -f option first.

---

### Post by alextockey on 2011-12-05
That doesn't seem to work either.

I noticed that when I remove the file, it does move it to the trash, but another copy remains in the folder I deleted it from.

---

### Post by killermist on 2011-12-05
"rm" should not be interacting with the "trash" in any way.

Try this sequence of commands

```
pwd
df -hT .
mount
```
these
display the present working directory
display free space (human readable with filesystem type) of the filesystem you're on
and displays what is mounted where

[edit]
These won't attempt to do anything to the file.  They're just information collection to try to figure out why the file cannot be deleted.

---

### Post by aeiah on 2011-12-05
is this a failed download? is your browser repeatedly re-creating the file as it tries to download it?

---

### Post by alextockey on 2011-12-05
Okay, this is what I recieved:

In the Downloads directory containing the two directories which contain the files:
[FONT=Courier New]home/alextockey/Downloads

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    455G   11G  422G   3% /
udev      devtmpfs    1.9G  4.0K  1.9G   1% /dev
tmpfs        tmpfs    764M  992K  763M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.9G  1.7M  1.9G   1% /run/shm
df: `/root/.gvfs': Permission denied

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)[/FONT]
[FONT=Courier New]udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alextockey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alextockey)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)


[FONT=Verdana]In the directories containing the files themselves:
1st File:
[/FONT]/home/alextockey/Downloads/Cengage-Beginning.DirectX.11.Game.Programming.2011.RETAiL.EBook-DiGiBook

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    455G   11G  422G   3% /
udev      devtmpfs    1.9G  4.0K  1.9G   1% /dev
tmpfs        tmpfs    764M  992K  763M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.9G  1.2M  1.9G   1% /run/shm
df: `/root/.gvfs': Permission denied

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alextockey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alextockey)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)


[FONT=Verdana]2nd File:[/FONT]
/home/alextockey/Downloads/Wiley.Ubuntu.Linux.Toolbox.1000.plus.Commands.for.Ubuntu.and.Debian.Power.Users.Nov.2007.eBook-BBL

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    455G   11G  422G   3% /
udev      devtmpfs    1.9G  4.0K  1.9G   1% /dev
tmpfs        tmpfs    764M  992K  763M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.9G  1.2M  1.9G   1% /run/shm
df: `/root/.gvfs': Permission denied

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alextockey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alextockey)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)


[/FONT]

---

### Post by carranty on 2011-12-05
Could you open a terminal and type

```
ls -l ~/Downloads/file.pdf
```

where by *file.pdf* I mean the actual name of the file we're talking about (I know there are 2, but lets just focus on one right now). 

Please paste both the command, and the output to this thread.

Note, you don't need the -r option when using rm unless you want to delete a folder.

---

### Post by killermist on 2011-12-05
Am I seeing that right that the directories have a space in them?  If so, that makes it a bit harder to directly target them for deletion.

Let's get a little more broad.  Are you trying to delete directories and the files they contain?  If so, then commands to delete regular files won't work without additional parameters.

If you're looking to delete a directory and files, then the command "rm -fr targetdirectory" is your command.  If the directory has spaces in it, then I recommend letting the shell help you with auto-completion.  When you get to typing the directory name, punch in the first few characters and use [tab] to ask the shell to fill in the rest.

---

### Post by alextockey on 2011-12-05
> **aeiah said:**
> is this a failed download? is your browser repeatedly re-creating the file as it tries to download it?

I deleted the files successfully, by deleting them first in KGet. That was totally the issue. Thanks guys.

---

