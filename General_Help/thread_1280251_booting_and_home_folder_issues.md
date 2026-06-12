---
title: "booting and home folder issues"
date: 2009-10-01
forum: General Help
---

### Post by Sennacherib on 2009-10-01
Hi all

After running a system mandated fsck I restarted as normal but this time I got a window on restart saying that ubuntu couldn't find my home folder and when the desktop came up I found that it was as if I had a new installation with a basic desktop and nothing in my folders.

I restarted with the liveCD and using the disk partition tool I saw that all my files are somewhere there as it showed a lot of used hard drive space.  When I re-ran fsck through the terminal it said it had superblock issues. 

How can I get ubuntu to boot up as before?

Thanks in advance.

---

### Post by undecim on 2009-10-01
Did you, by chance, have you home folder installed on a separate partition?

---

### Post by cranecreek on 2009-10-01
Since you have no files to lose , why not start over and you didn't mention what version of Ubuntu you want to use. For a complete how to follow these links:
[Ubuntu Studio]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-9.04") 9.04
[Jaunty jackalope]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04") 9.04
[Intrepid ibex]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10") 8.10<<<<this is what I use

Linux is about choice, Good luck and if any questions this is the best forum that is available, ask questions

Let me know how things work out.

---

### Post by kayvortex on 2009-10-02
Could you post exactly what the fsck error message was. You can boot off the LiveCD and then fsck your root partition (**don't** mount it!). Of course, you need to remember what partition your installation was on: you can try mounting all the partitions at /dev/[s,h]da* in turn to find the right one, and:
```
sudo fdisk -l
```
to help eliminate any possibilities. Let me know if you need any help with this.

It seems like the disk superblock is corrupted. Linux maintains backups, so don't panic just yet.

---

### Post by Sennacherib on 2009-10-02
Cranecreek: I was thinking about going that as none of my files are in any folders, but when I looked at the disk usage, it still said 90Gb was in use: exactly how much I was using before this whole kafuffle; so I'm trying to fix it to not lose the files that appear to be under there...somewhere.

Also, thanks for the heads up: I'm using Jaunty.



Undecim: I do have another partition running vista, but the home folder was on the linux partition. Is that somewhat what you mean?



Kayvortex: Here is the output from the fsck

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fsck /dev/sda1/ -y
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Not a directory while trying to open /dev/sda1/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>




and here is the fdisk -l output

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eea2c43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       22692   182273458+  83  Linux
/dev/sda2   *       22693       29164    51986340    7  HPFS/NTFS
/dev/sda3           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris


when I put that message generated from the failed fsck into google, I couldn't find anything specific to ubuntu, though I did come across [this advice]("http://blog.edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/") on restoring a bad superblock; though I'm not sure understand what it is suggesting.

What would you recommend?

---

### Post by kayvortex on 2009-10-02
It's basically telling you to use a backup of your disk's superblock. First, you need to find a backup: run the command
```
sudo dumpe2fs /dev/sda1 | grep superblock
```

I get the output:
dumpe2fs 1.41.4 (27-Jan-2009)
  Primary superblock at 0, Group descriptors at 1-1
  Backup superblock at **32768**, Group descriptors at 32769-32769
  Backup superblock at **98304**, Group descriptors at 98305-98305
  Backup superblock at **163840**, Group descriptors at 163841-163841
  Backup superblock at **229376**, Group descriptors at 229377-229377
  Backup superblock at **294912**, Group descriptors at 294913-294913
  Backup superblock at **819200**, Group descriptors at 819201-819201
  Backup superblock at **884736**, Group descriptors at 884737-884737
  Backup superblock at **1605632**, Group descriptors at 1605633-1605633

From that, I would first use the backup at **32768**. Run fsck again as:
```
sudo fsck -f -y -b 32768 /dev/sda1
```
where the number "32768" matches one of the numbers that are in bold above, but correspond to whatever output *you* get (it will probably be the same). This command will just run fsck as before, but now using one of the backups of your partition superblock. Again, don't mount /dev/sda1 and let me know if there are any error messages; also, try some more of the backups if it doesn't immediately work for the first few.

---

### Post by Sennacherib on 2009-10-03
Ran all that and got no error messages in the fsck.

Problem one: sorted!  Thanks heaps!


How do you think I should choose the backed up superblock to be able to access all my old files again?  How often is the superblock backed up?

---

### Post by kayvortex on 2009-10-03
Right, I think the way that fsck does things is that it fixes the primary superblock if there are any discrepancies between it and the backup that you specified; so, you *should* be able to boot your system up fine now. I'm not sure how often the superblock is backed-up, but I'd imagine that it's done fairly regularly; so you probably don't need to worry about that. Did your system crash at any time before this issue came up and a previous system fsck? If so, that was probably the cause of the problem; otherwise it *might* be a portent of impending disk failure. It sounds a bit ominous, but it's better to know beforehand that the disk might fail so that you can backup your data regularly. Besides, disks are fairly cheap and not so hard to put in (unless it's a laptop!).

Anyway, let's play it slowly, though, and try to mount your partition using the LiveCD: put the LiveCD in and run the command:
```
sudo mkdir -v /mnt/mydata && sudo mount -v -t ext3 -o ro /dev/sda1 /mnt/mydata
```
This will mount your partition (read-only) at /mnt/mydata, and all your files and data from the root directory down *should* be accessible in /mnt/mydata. Note that I put "-t ext3": if you have formatted your partition as anything else then replace "ext3" with that (you could, of course, just leave it out altogether and let mount guess what it should be, but it would probably be better in this case to tell mount that you know what it should be).

If all your data is accessible, I would use that opportunity to backup all the data that is important to you before doing anything else (just to be on the safe side). Then, try booting your system up as normal and let me know what happens.

---

### Post by Sennacherib on 2009-10-05
Righto

Through /mnt/mydata I've backed up everything: thanks very much for that.

But when I restarted Ubuntu I still couldn't access my files.  I even went back and ran fsck using the oldest superblock (from the dumpe2fs) with the same result: everything looks like a new installation but my files are under there somewhere when I do the disk partition thing on the LiveCD.

When you say "remount" all I'm doing is restarting the computer, taking out the LiveCD and letting Ubuntu start up as normal.

Is that right?

---

### Post by kayvortex on 2009-10-05
No need for the thanks: I'm glad to help.

To "mount" something just means to make its contents available to the OS. For example, when you put a CD in a CD-drive the OS has to "mount" it in order to access the files on it (this is true for *nix *and* Windows) -- it's just that the OS does this automatically for you and so you never see it. But you can do this for hard-disk partitions as well as CDs: in fact, when your system boots up (again, for Windows as well as for *nix) one of the things it does is mount your partitions where all the files on your computer are stored.
However, when you boot off the LiveCD, it doesn't know where your data is so you have to mount your partitions manually if you want to access it, which is what the command I gave you before did. This is why booting off the LiveCD doesn't affect your system: the LiveCD never mounts your hard-disks and so never touches the files and data on your computer.

> When you say "remount" all I'm doing is restarting the computer, taking out the LiveCD and letting Ubuntu start up as normal.

Is that right?
Yeah, that's what I mean when I say mount the disks as normal -- i.e., just letting your computer do its normal boot-up procedure and "mount" the disks as it always does when it boots up.

Right then, you still can't access your files. Does doing a fsck without the "-b" flag run without errors now? I.e., does booting off the LiveCD and running:
```
sudo fsck -f -y /dev/sda1
```
now complete without errors. Because if it *does* then it means that we can rule out disk errors.

In any case, could you also boot your computer up as normal and then post the output of:
```
mount
```
and
```
cat /etc/fstab
```

---

### Post by Sennacherib on 2009-10-07
Righto

I ran 

sudo fsck -f -y /dev/sda1
and it ran with no problem.  How does this mean there are no disk areas compared to when we run it with a specific superblock back up referenced. 

I ran "mount" after rebooting windows (still no sign of files, of course) and here's the output.

nick@plodder-mcgee:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)




cat /etc/fstab


nick@plodder-mcgee:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=424051b5-2f46-4f6b-9f57-6e3f0a15b3d3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1ea78751-3a0a-47a3-9dc1-3ecaac743715 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0





So, what are we looking at here?

---

### Post by kayvortex on 2009-10-07
> How does this mean there are no disk areas compared to when we run it with a specific superblock back up referenced.

If I think I've understood your question properly, it's because there is no "-b *some_number*" there anymore: the "-b" flag tells fsck to use a backed-up suberblock at the number that you give with the "-b" flag. If there is no "-b" flag, then fsck just runs as normal.

Your partitions seem to be mounting fine, so that's not it. I'm thinking that the problem could be with GNOME, and thinking (and hoping!) that the problem is with file permissions. How are you browsing your system -- is it through "Places" on the panel? Are you looking for your files simply by opening windows and looking for your files (as opposed to via the command line)?
Could you post the output of:
```
ls -lh / /home
```
and
```
df -h
```
Also, do you remember the error that GNOME gave? If you can, then could you post that up too, and I'll see if there are any clues there.

---

### Post by Sennacherib on 2009-10-14
Hey, sorry I've been away; works been hell the last five or so days.

here is the output from the 
ls -lh / /home
/:
total 108K
drwxr-xr-x   2 root root 4.0K 2009-08-06 14:40 bin
drwxr-xr-x   3 root root 4.0K 2009-09-30 19:24 boot
lrwxrwxrwx   1 root root   11 2009-08-02 23:26 cdrom -> media/cdrom
drwxr-xr-x  17 root root 4.2K 2009-10-14 21:41 dev
drwxr-xr-x 145 root root  12K 2009-10-14 21:42 etc
drwxr-xr-x  68 nick nick 4.0K 2009-10-02 00:35 home
lrwxrwxrwx   1 root root   33 2009-08-20 22:22 initrd.img -> boot/initrd.img-2.6.28-15-generic
lrwxrwxrwx   1 root root   33 2009-08-06 14:31 initrd.img.old -> boot/initrd.img-2.6.28-14-generic
drwxr-xr-x  15 root root  12K 2009-09-16 12:39 lib
drwxr-xr-x   7 root root  12K 2009-09-16 12:39 lib32
lrwxrwxrwx   1 root root    4 2009-08-02 23:26 lib64 -> /lib
drwx------  46 root root  20K 2009-08-26 19:30 lost+found
drwxr-xr-x   3 root root 4.0K 2009-10-14 21:41 media
drwxr-xr-x   2 root root 4.0K 2009-04-13 10:33 mnt
drwxr-xr-x   2 root root 4.0K 2009-04-20 14:59 opt
dr-xr-xr-x 147 root root    0 2009-10-14 21:41 proc
drwx------  16 root root 4.0K 2009-09-12 22:26 root
drwxr-xr-x   2 root root 4.0K 2009-09-16 12:39 sbin
drwxr-xr-x   2 root root 4.0K 2009-03-06 17:16 selinux
drwxr-xr-x   2 root root 4.0K 2009-04-20 14:59 srv
drwxr-xr-x  12 root root    0 2009-10-14 21:41 sys
drwxrwxrwt  12 root root 4.0K 2009-10-14 21:43 tmp
drwxr-xr-x  12 root root 4.0K 2009-08-06 16:55 usr
drwxr-xr-x  15 root root 4.0K 2009-04-20 15:13 var
lrwxrwxrwx   1 root root   30 2009-08-20 22:22 vmlinuz -> boot/vmlinuz-2.6.28-15-generic
lrwxrwxrwx   1 root root   30 2009-08-06 14:31 vmlinuz.old -> boot/vmlinuz-2.6.28-14-generic

/home:
total 19M
drwxr-xr-x  2 nick nick 4.0K 2009-06-09 22:47 Adobe Photoshop 7.0
-rw-------  2 nick nick 7.2K 2009-08-12 19:08 Bookmarks 2009-08-12.json
drwxr-xr-x 10 nick nick 4.0K 2009-10-01 22:40 Desktop
drwxr-xr-x  4 nick nick 4.0K 2009-09-22 14:25 Documents
-rw-r--r--  2 nick nick 1.5M 2007-04-25 17:33 DosBootimage.IMA
-rw-r--r--  2 nick nick  357 2009-08-02 23:36 examples.desktop
drwxr-xr-x  2 nick nick 4.0K 2009-08-25 19:34 FEBE 2009 25.08 19.33.52
drwxr-xr-x  2 nick nick 4.0K 2009-08-25 19:47 FEBE 2009 25.08 19.46.46
-rw-r--r--  2 nick nick  12M 2009-08-06 16:16 Firefox_wallpaper.png
drwxr-xr-x  6 nick nick 4.0K 2009-09-20 19:10 Mac_files
drwxr-xr-x  7 nick nick 372K 2009-09-17 20:25 Music
drwxr-xr-x  7 nick nick 4.0K 2009-08-07 19:18 music-applet-2.5.1
drwxr-xr-x 28 nick nick 4.0K 2009-10-14 21:41 nick
drwxr-xr-x  8 nick nick 4.0K 2009-09-27 17:04 Photos
drwxr-xr-x 17 nick nick 4.0K 2009-09-27 16:11 Pictures
drwxr-xr-x  2 nick nick 4.0K 2009-08-03 00:42 Public
-rw-r--r--  2 root root   24 2009-09-12 19:24 replay_arp-0912-192459.cap
drwxr-xr-x  2 nick nick 4.0K 2009-08-03 00:42 Templates
drwxr-xr-x 14 nick nick 4.0K 2009-09-04 21:39 Videos
-rw-r--r--  2 root root 4.9M 2009-09-12 19:55 wifi-01.cap
-rw-r--r--  2 root root  381 2009-09-12 19:55 wifi-01.csv
-rw-r--r--  2 root root  584 2009-09-12 19:55 wifi-01.kismet.csv
-rw-r--r--  2 root root 1.6K 2009-09-12 19:55 wifi-01.kismet.netxml

and here is the output from 
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             172G   79G   85G  49% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  292K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  152K  1.9G   1% /dev
tmpfs                 1.9G  468K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-15-generic/volatile


So, from what I see (whatever those inputs you gave me meant) that, as I thought, my files are still there and I can see the various permissions, sizes etc.  In regards to your question; I've been browsing to the various folders by Places, not by the terminal.  I tried to look at my desktop (which should have all the files up there) through the terminal, my feeble attempts only generated the following:

nick@plodder-mcgee:~$ cd Desktop
nick@plodder-mcgee:~/Desktop$ ls
nick@plodder-mcgee:~/Desktop$ 

Yeah, I probably did that wrong!

---

### Post by yknivag on 2009-10-14
> **Sennacherib said:**
> nick@plodder-mcgee:~$ cd Desktop
nick@plodder-mcgee:~/Desktop$ ls
nick@plodder-mcgee:~/Desktop$ 

Yeah, I probably did that wrong!

It certainly seems like your files are still there.

Try the following command in a terminal and see whether you can see them all:

```
cd ~ && ls -alR
```

If it rolls past the top of the terminal or you want to check it more slowly, then you can page the output with:

```
cd ~ && ls -alR | less
```
or send it to a file with
```
cd ~ && ls -alR > myfiles.txt
```

---

### Post by kayvortex on 2009-10-15
> 
nick@plodder-mcgee:~$ cd Desktop
nick@plodder-mcgee:~/Desktop$ ls
nick@plodder-mcgee:~/Desktop$

Yeah, I probably did that wrong!


No, that's OK.

Could you just definitely make sure (within a *terminal*) that all your files are not being displayed. Get a location where you know a file of yours should exist and enter:
```
ls -l -a *directory_where_file_exists*
```
I won't ask you to post any of your personal files, but could you just make sure that they definitely don't exist. Make sure to include the "-a" when you use the *ls* command: it simply tells *ls* to list all hidden files too (hidden files begin with a period in Linux; so, ".myfile.txt", for example, would be a hidden file). The "-l" simply tells *ls* to print more detailed information (it's useful, but not really necessary). Basically, I just want to you to check that your files *haven't* been prefixed with a period for some reason, thereby making them hidden.

Following up on what *yknivag* said,
> ```
cd ~ && ls -alR
```
will print out EVERY file in your home folder (and this includes every file within every directory in your home folder), so this is a useful (but confusing -- just run it and see for yourself!) way to check whether files are no longer being displayed. Almost certainly, this command will print out a lot of info, so enter the command:
```
ls -alR --color=no ~ 2>&1 | less
```
This is a slightly modified command that *yknivag* gave, but essentially does the same thing.
When you run this command, every file will be listed in your terminal and you can press the up and down keys (or just scroll) to look through it. If you look at the bottom, you should see a colon. Press the '/' key on your keyboard and the ':' should change to a '/'. Then, type in something and press enter and you can search for that phrase in that printout. So, if you type '/' and then enter "myfile" and then press the enter key, all instances of "myfile" will be searched for (you can press the 'n' key to go to the next occurrence of "myfile", 'g' to go to the start of the printout and 'G' to go to the end). Use this to look for files that you know should exist, and also for any errors that *ls* has flagged up (press '/' and then type "ls:" and enter to search for errors). Press 'q' to exit. 

If your files are definitely not showing up, then I'm at a bit of a loss I'm afraid. If you're able to see all your files when you put the LiveCD in, then I'd probably just recommend copying all your personal data, waiting however many days it is until Karmic is released, download that and do a clean install. It's not really a "solution", but it might be the simplest thing to do.

Let me know if there's anything you're not sure about.

---

### Post by Sennacherib on 2009-10-18
kayavortex and yknivag

I went through those instructions and it looks like my files are there but, obviously I still can't access them.  Ho hum!

Thanks for your help, but I think, since I've backed everything up, I'll do a clean install.

Thanks very much guys.

---

### Post by kayvortex on 2009-10-19
Don't mention it. I'm just sorry I wasn't able to find a proper solution. Regardless, don't forget to backup important stuff every so often.

---

