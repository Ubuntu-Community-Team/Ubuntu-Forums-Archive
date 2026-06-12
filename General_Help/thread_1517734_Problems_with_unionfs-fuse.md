---
title: "Problems with unionfs-fuse"
date: 2010-06-25
forum: General Help
---

### Post by cheshirekow on 2010-06-25
I've been looking at tons of information on the web on unioning file systems. Right now I'm trying to get something setup with unionfs-fuse (I guess aufs2 is the preferred and there's also mddhfs but I can't find any documentation on the latter and the former is not in the repositories). 

Anyway, I set up the following test scenario

```

user@host:~$ cd Desktop
user@host:~/Desktop$ mkdir test
user@host:~/Desktop$ cd test
user@host:~/Desktop/test$ mkdir test1
user@host:~/Desktop/test$ mkdir test2
user@host:~/Desktop/test$ mkdir test3
user@host:~/Desktop/test$ echo "this is file A" > test1/fileA.txt
user@host:~/Desktop/test$ echo "this is file B" > test2/fileB.txt

```

Then I merge the test1 and test2 directories as such

```

unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test3

```

And I get the expected result

```

user@host:~/Desktop/test$ unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test3
user@host:~/Desktop/test$ ls -l test3
-rw-r--r-- 1 user user 14 2010-06-25 11:34 fileA.txt
-rw-r--r-- 1 user user 14 2010-06-25 11:34 fileB.txt

```

I then unmount the new directory

```

user@host:~/Desktop/test$ sudo umount test3

```

And then try this

```

user@host:~/Desktop/test$ unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test1
fuse: mountpoint not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```

Which I was definately not expecting. So I figured "what the heck, lets try it"

```

user@host:~/Desktop/test$ unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test1 -o nonempty
user@host:~/Desktop/test$ ls -l test1

```

The first command executes, but the second freezes... Any one care to explain why? I thought unionfs allowed merging of two directories into one of the two as the mount point. At least, that's what a number of the unionfs tutorials have indicated. Is there a way to do what I want? Some other options?

---

### Post by gzarkadas on 2010-06-25
It maybe the case that test1 contains two files, which gave you this issue; see if having an empty test1 makes things work.

In any case, mounting a path to itself -even if it can be made to work- looks somewhat strange. What is this that you want to achieve after performing your tests?

---

### Post by cheshirekow on 2010-06-26
I'm trying to accomplish a solution to this:

[http://ubuntuforums.org/showthread.php?t=1515506](http://ubuntuforums.org/showthread.php?t=1515506)

---

### Post by gzarkadas on 2010-06-26
You don't have to go that way. I have a rather big system with about 5500 packages installed and my disk usage (I used `sudo baobab' and requested an analysis of the entire filesystem) is approx. this:

```

all except /home , /usr and /var: 1.3 GB
/var: 2.7 GB of which 1.1 GB is due to aide , so 1.6 GB
/usr: 16.6 GB of which:
    /usr/share/doc: 4.4 GB
    /usr/src: 1.2 GB
    /usr/include: 0.4 GB
so, "necessary" space on /usr: 10.6 GB

```Thus the "necessary" space except /home in your system will be more or less: 1.3 + 1.6 + 10.6 = 13.5 GB
Since you have 4 + 16 GB in two disks, you can:

**Warning: This procedure will most probably require you to work some parts of it from the liveCD, since the system will be unusable in its intermediate states. Step 0 is crucial for the integrity of your data.**

0. Make a complete backup of your system, since you will be repartitioning. If you don't know how to do it, there are guides both in the tutorials section of the forum and in the ubuntu community documentation.

1. Put everything except /usr and /home in the 4GB disk, in one partition. You 'll have aprox. 1GB free for temp files, your /root files, etc. which is more than plenty.

2. Make three partitions in your second, 16 GB, disk:
One for /usr with size 11 GB
One for /home with size 3 GB (or 4 GB if you can afford smaller swap)
one for swap with size 2GB (or 1 GB if you can afford it, to give more space to your docs).

3. Now make directories in your external usb drive for all parts of the filesystem tree that will be mounted:
```
    /usr/share/doc
    /usr/src
    /usr/include

```and of course
```
    /home/<account>/Collections
    /home/<account>/<whatever-else>

```4. Copy the parts of the filesystem that belong to these directories there. Then empty the corresponding directories in your internal disks.

5. Edit your /etc/fstab to place bind mounts for the directories in the usb drive. You 'll use lines of that form:
```

/olddir  /newdir  none  bind

```For example:
```

/media/two/usr/share/doc    /usr/share/doc  none  bind
/media/two/usr/src    /usr/src    none  bind
/media/two/usr/include    /usr/include    none  bind

```
In addition you need already have put lines for mounting the / , /home , /usr and swap partitions above.

6. If the /etc/fstab info does not automatically work when the usb drive is inserted, you 'll have to force a `mount -a'. See this [guide]("http://ubuntuforums.org/showthread.php?t=168221") and maybe [this also]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto").

Now this may look more involved from the chroot+unionfs solution that you seek, but IMO is a more "clean" design and it does keep all your executables in place. Essentially only when you need documentation or headers to compile from source you'll have to plug the usb drive (oh, and to listen to your music, which probably means the usb drive will be frequently connected :)).

---

### Post by cheshirekow on 2010-06-26
Thanks for the reply! You're findings are encouraging, maybe I should just do this with static mounts. However, I'm not sure what your packages are, but I filled up the 16 GB drive very easily. You quoted a total of 20Gb, but I get the feeling I can easily exceed that. I work with a number of different peices of code right now, and (obviously) this is not my primary build system... but it is nice to work on documentation or squash little bugs when I'm traveling so I tend to carry around the repositories for those projects, as well as the library dependancies (a lot of which are official packages) so I'm pretty sure the shared libraries are going to be taking most of the space. In any case, I'm in deep with trying to figure out this unionfs thing so I think I'll try to push through and figure it out, and if I can get a proof of concept going then I'll decide which of the two I want to use finally.

---

### Post by gzarkadas on 2010-06-26
To gain space, you could in a slightly more involved setup make the entire /usr partition (minus the parts that you 'd have to the usb drive) a squashfs filesystem. Then, to be able to install new software, use unionfs to join the squashed read-only filesystem with a read-write one under /usr. All of this should be made through /etc/fstab, since /usr need always be available.

You can either have this read-write space in your internal disks to have the ability to install software anytime, or in your external usb drive to have the maximum free space for your projects. I think option #2 makes more sense in your case; it will just make necessary to mount the drive during installs - but this will be required to rebuild the squashfs (see below).

This setup has the minor drawback that after modifying the software in your system you will have to rebuild the squashfs filesystem. But it is not necessary to do it often, since the changes will be available through the unionfs. If you select option #2 though, newly installed software will only be available when the usb drive is mounted.

If you go that way then you only need two partitions in the second disk: one for /home (14-15 GB) and one for swap (1-2 GB). Put the squashfs filesystem archive inside /home (say /home/usr.squashfs). This will give you the maximum flexibility of managing your limited space; no loss of trailing space in a partition and easy to make room for a bigger one squashfs in the future.

---

### Post by aakef on 2010-06-27
> **cheshirekow said:**
> 

Then I merge the test1 and test2 directories as such


And then try this

```

user@host:~/Desktop/test$ unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test1
fuse: mountpoint not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

```

Which I was definately not expecting. So I figured "what the heck, lets try it"

```

user@host:~/Desktop/test$ unionfs-fuse /home/user/Desktop/test/test1=RW:/home/user/Desktop/test/test2=RO /home/user/Desktop/test/test1 -o nonempty
user@host:~/Desktop/test$ ls -l test1

```

The first command executes, but the second freezes... Any one care to explain why? I thought unionfs allowed merging of two directories into one of the two as the mount point. At least, that's what a number of the unionfs tutorials have indicated. Is there a way to do what I want? Some other options?

Sorry no, that is presently not supported, probably it will be supported in 0.26 (alpha is currently 0.25, release is 0.24). In order to do that, you will first need to bind mount test1 to another directory and then to use that bind mounted directory as argument for unionfs-fuse.

Cheers,
Bernd

---

### Post by aakef on 2010-06-27
Btw, you should use our mailing list for unionfs-fuse questions. Hmm, I probably should add a 'contact' field to the man page.

[email]unionfs-fuse@googlegroups.com[/email]

---

### Post by cheshirekow on 2010-06-27
> **gzarkadas said:**
> You don't have to go that way. I have a rather big system with about 5500 packages installed and my disk usage (I used `sudo baobab' and requested an analysis of the entire filesystem) is approx. this:

...

Now this may look more involved from the chroot+unionfs solution that you seek, but IMO is a more "clean" design and it does keep all your executables in place. Essentially only when you need documentation or headers to compile from source you'll have to plug the usb drive (oh, and to listen to your music, which probably means the usb drive will be frequently connected :)).

Ok. So I can't yet do exactly what I want to with just unionfs-fuse. Thanks for the info about the current versions. Also, I can't quite figure out how to get gdm/xfce to start in the chroot so I can't exactly do what I want to in that manner either. I will continue to research how to do that and play around with the idea, but for now I'm going ot take gzarkadas's suggestion and mount everything in this manner. I do have one question though, is there any reason to partition up the second hard drive the way you suggested? Wouldn't it be just as easy to leave it as a single partition and bind mount the directories in the right place? Like this (etc/fstab):

```

UUID=...        /mnt/slow       ext4    defaults        0       2

/mnt/slow/usr/share/doc    /usr/share/doc    none   bind    0   0
/mnt/slow/usr/share/doc    /usr/src          none   bind    0   0
/mnt/slow/usr/include      /usr/include      none   bind    0   0

/mnt/slow/home/<account>/Collections        /home/<account>/Collections  none    bind    0   0
/mnt/slow/home/<account>/<whatever>         /home/<account>/<whatever>   none    bind    0   0

```

---

### Post by gzarkadas on 2010-06-27
It can be done that way too. The reason I suggested separate partitions is for safety: if one goes for any reason, the other stays intact, which means less things to repair. But in your case you can trade safety with some more space, since you are low on this.

So, if I understand well your intentions, the setup will be as follows:

**Disks:**

[LIST]
[*]4GB disk: hosts the / (root) mount (and possibly the swap partition, if you have one).
[*]16GB disk: hosts the /home mount.
[/LIST]
[B]The /usr tree:
[/B] 
[LIST]
[*]The entire /usr tree (except the dirs moved to external usb drive) is moved to /home/usr and after mounting /home in /etc/fstab, it is bind mounted as /usr.
[/LIST]
[INDENT]**OR** (if the squashfs option is selected):[/INDENT]
[LIST]
[*]The entire /usr tree (except the dirs moved to external usb drive) is converted to a squashfs archive inside /home (say /home/usr.squashfs).
[*]Directories /home/usr-ro and /home/usr-rw are created.
[*]After mounting /home in /etc/fstab, the squashfs archive is mounted at /home/usr-ro.
[*]A unionfs filesystem containing /home/usr-ro as read-only and /home/usr-rw as read-write is mounted as /usr. I believe this can be achieved with the current version of unionfs.
[/LIST]
[B]The /usr/share/doc /usr/src and /usr/include subtrees:
[/B] 
[LIST]
[*]They are moved to external usb drive, as described previously, and are bind mounted to the appropriate places either statically through /etc/fstab, or if this cannot be made to work, dynamically when the disk is plugged in.
[/LIST]

---

### Post by cheshirekow on 2010-06-28
> **gzarkadas said:**
> So, if I understand well your intentions, the setup will be as follows:


Actually it's more like this:
**Disks**
[LIST]
[*]4GB - / (root)
[*]16GB - /usr, /var, /home
[*]External - /usr/share/doc, /usr/src, /usr/include, /home/user/Collections
[/LIST]

My FSTAB looks like this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2541ced6-0bb3-472f-b290-0e6cadb07609 /               ext4    errors=remount-ro 0       1
# /mnt/slowpoke was on /dev/sdb1 during installation
UUID=ef77bd7d-8377-4b95-ba7d-989a32670a4d /mnt/slowpoke   ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=34a6ec76-1d0b-4710-bec0-eae60196f4e0 none            swap    sw              0       0
# /mnt/Ellis was on /dev/sdc1 during installation
UUID=72e01fc3-9153-4894-ae20-957beef787fc /mnt/Ellis      ext4    defaults        0       4

/mnt/slowpoke/usr       /usr    none    bind 0 3
/mnt/slowpoke/home      /home   none    bind 0 3
/mnt/slowpoke/var       /var    none    bind 0 3

/mnt/Ellis/shiftroot/usr/share/doc    /usr/share/doc  none    bind 0 5
/mnt/Ellis/shiftroot/usr/src          /usr/src        none    bind 0 5
/mnt/Ellis/shiftroot/usr/include      /usr/include    none    bind 0 5

/mnt/Ellis/home/user/Collections      /home/user/Collections    none    bind 0 5
/mnt/Ellis/home/user/Ellis            /home/user/Ellis          none    bind 0 5

```

(Ellis is the volume label for the external hard drive). So this seems to almost work except for a few kinks. I installed xubuntu onto the small drive first (I call it speedy), and then copied the /usr and /var directories to the larger drive (I call it slowpoke). Then I copied the relavent subdirectories to Ellis. I did this all from a live-USB stick (actually the installation image). Now when I try to boot up I get 

```

Error: File Not Found

```

While booting up. It's drawn in a "terminal" appearance before the xubuntu screen pops up. It doesn't seem to prevent anything, though I would like to know what file is being looked for...

Then, I get a screen with the Xubuntu logo and the following (approximate from memory, I should write this down next time... will edit later)

```

keys: S Skip Mounting, M Manually Fix Problems

```

If Ellis is plugged in it goes away and gdm loads up with my user login. If Ellis is not plugged in it hangs here. Pressing M takes me to a root terminal, and pressing S a couple of times leads to gdm loading. I'm guessing this is because of the last few lines of the FSTAB pointing to bad locations if Ellis is not plugged in, so I guess I should make this a script and mount it dynamically instead of with FSTAB. 

The other kink is that at first sudo didn't work. The permissions for everything in usr seems to have changed when  I coped it from speedy to slowpoke. For instance the permissions on sudo where 755, so I changed them to 4111 and now sudo works again. There are still some slightly wonky things. In particular, the icon for the wireless status in the xfc4 panal is a big red circle with a white bar (looks like "do not enter")... even though the wireless is working and I am posting this from the computer.

Maybe I shouldn't have copied all of usr to slowpoke. Maybe I should have left usr/bin on speedy? It'll be a pain to reinstall again but I'd rather get this right now that I'm in a "playing" state, as opposed to later when I have all kinds of important data on here.

Oh, and I read some more about the squashfs solution for compressing data. I think it's an incredibly slick idea, though I think I will save that for later. I'm getting tired of this project so I'd rather find something that "just works" well enough to move on.

---

### Post by gzarkadas on 2010-06-28
I believe you copied /usr without preserving permissions (did a simple `cp' while you should have done a `cp -a'). If you still have the original /usr, copy it again over the new one preserving permissions. 

There are quite a few setuid/setgid executables inside /usr/bin and /usr/sbin. There are also some with different group than root and perhaps some with different permissions than 755. All of these issues need to be fixed.

If you don't have your original /usr tree anymore, don't despair; I am preparing a list of them as are in my system and you could also use the (squashed) filesystem contained in the livecd to read the original permissions, ownership info.

---

### Post by cheshirekow on 2010-06-28
Doh! You're right. I did a simple cp. Not a cp -a. I don't have the original /usr anymore. So to use the fs on the installer image, I need to mount the squashed fs, and then just copy everything from /usr? Actually, can I just boot the usb drive, and then copy everything from /usr? Or is the file system that's loaded by the installer's live image different then the one that is installed?

---

### Post by gzarkadas on 2010-06-28
This is the /usr permissions list for a Karmic Desktop Installation. As you can see there is lots of stuff. Installing additional packages will add to this list.  So, if you have a backup of /usr made such that permissions are preserved, use it to restore; it is the fastest way to go. If not, read on.
 
```

./bin/arping                             4755   root     root
./bin/at                                 6755   daemon   daemon
./bin/bsd-write                          2755   root     tty
./bin/chage                              2755   root     shadow
./bin/chfn                               4755   root     root
./bin/chsh                               4755   root     root
./bin/crontab                            2755   root     crontab
./bin/dotlockfile                        2755   root     mail
./bin/expiry                             2755   root     shadow
./bin/gpasswd                            4755   root     root
./bin/lppasswd                           4755   root     fuse
./bin/mail-lock                          2755   root     mail
./bin/mail-touchlock                     2755   root     mail
./bin/mail-unlock                        2755   root     mail
./bin/mlocate                            2755   root     mlocate
./bin/mtr                                4755   root     root
./bin/newgrp                             4755   root     root
./bin/passwd                             4755   root     root
./bin/pkexec                             4755   root     root
./bin/screen                             2755   root     utmp
./bin/ssh-agent                          2755   root     ssh
./bin/sudo                               4755   root     root
./bin/sudoedit                           4755   root     root
./bin/traceroute6.iputils                4755   root     root
./bin/wall                               2755   root     tty
./bin/X                                  6755   root     root
./bin/xterm                              2755   root     utmp
./games/glines                           2555   root     games
./games/gnibbles                         2555   root     games
./games/gnobots2                         2555   root     games
./games/gnometris                        2555   root     games
./games/gnomine                          2555   root     games
./games/gnotravex                        2555   root     games
./games/gnotski                          2555   root     games
./games/gtali                            2555   root     games
./games/mahjongg                         2555   root     games
./games/same-gnome                       2555   root     games
./lib/cups/backend-available/parallel    555    root     root
./lib/cups/backend-available/scsi        555    root     root
./lib/cups/backend-available/serial      544    root     root
./lib/cups/backend-available/snmp        555    root     root
./lib/cups/backend-available/socket      555    root     root
./lib/cups/backend-available/usb         544    root     root
./lib/cups/backend/parallel              555    root     root
./lib/cups/backend/scsi                  555    root     root
./lib/cups/backend/serial                544    root     root
./lib/cups/backend/snmp                  555    root     root
./lib/cups/backend/socket                555    root     root
./lib/cups/backend/usb                   544    root     root
./lib/eject/dmcrypt-get-device           4755   root     root
./lib/evolution/camel-lock-helper-1.2    2755   root     mail
./lib/libvte9/gnome-pty-helper           2755   root     utmp
./lib/openssh/ssh-keysign                4755   root     root
./lib/policykit-1/polkit-agent-helper-1  4755   root     root
./lib/pt_chown                           4755   root     root
./local/lib/python2.6                    2775   root     staff
./local/lib/python2.6/dist-packages      2775   root     staff
./local/lib/python2.6/site-packages      2775   root     staff
./local/share/ca-certificates            2775   root     staff
./local/share/fonts                      2775   root     staff
./local/share/ppd                        2775   root     staff
./local/share/sgml                       2775   root     staff
./local/share/sgml/declaration           2775   root     staff
./local/share/sgml/dtd                   2775   root     staff
./local/share/sgml/entities              2775   root     staff
./local/share/sgml/misc                  2775   root     staff
./local/share/sgml/stylesheet            2775   root     staff
./local/share/xml                        2775   root     staff
./local/share/xml/declaration            2775   root     staff
./local/share/xml/entities               2775   root     staff
./local/share/xml/misc                   2775   root     staff
./local/share/xml/schema                 2775   root     staff
./sbin/pppd                              4754   root     dip
./sbin/uuidd                             6755   libuuid  libuuid
./src                                    2775   root     src

```[U]If not having /usr backup
[/U]
All of these files must be reset to default owner, group and permissions with `chown' and `chmod' commands. After that the best strategy is to reinstall all additional packages; this will fix permissions I guess.

Since this is a lot of typing and in addition you may not have this specific distro, I include a recipy to find them for your case.

Step 1: Make an .iso image of your distro's liveCD somewhere in your filesystem.

Step 2: Open a terminal and type the full set of commands below. The sequence of events performed are the following:

[LIST]
[*]An interactive root shell is created (you have a lot to type).
[*]Two directories are created in /mnt and first the livecd .iso image, second the installation's squashfs contained there are mounted.
[*]Set current directory the /usr subtree of the installation's squashfs tree.
[*]Use find to locate all files inside the above subtree that have extended permissions (setuid, setgid, etc), owner or group <> root, standard permissions <> user=rw,group=r,all=r. Store the results in files inside /root.
[*]Then merge the three files to one and discard duplicates.
[*]Set current directory the /usr subtree of your filesystem.
[*]Read all lines of the merged file and change ownership and permissions of the target files inside /usr
[*]Remove the mounts and close the root shell.
[/LIST]
```

sudo -i
cd /mnt
mkdir mode=755 dist-cd dist-fs
mount -o loop <path-to-the-licevd-image-iso> /mnt/dist-cd
mount -o loop -t squashfs /mnt/dist-cd/casper/filesystem.squashfs /mnt/dist-fs

cd /mnt/dist-fs/usr
find -O2 -perm /7000 -printf '%-40p %-6m %-8u %g\n' | sort > ~/dist-usr-suid
find -O2 ! -user root -o ! -group root -printf '%-40p %-6m %-8u %g\n' | sort > ~/dist-usr-owner
find -O2 '(' -type d -a ! -perm -755 ')' -o '(' -type f -a ! -perm -644 ')' -printf '%-40p %-6m %-8u %g\n' | sort > ~/dist-usr-perm
cat ~/dist-usr-* | sort -s -u > ~/dist-usr-unique

cd /usr
while read name perm user group ; do chown ${user}:${group} ${name} ; chmod ${perm} ${name} ; done < ~/dist-usr-unique

umount -l /mnt/dist-fs
umount -l /mnt/dist-cd
exit

```Now you can proceed to re-install all packages that you have installed afterwards. Either use the Synaptic Package Manager, or open a terminal and type:
```

cd /var/lib/dpkg
cat status | awk 'BEGIN{RS="";FS="\n";OFS="\n"} { pkg=substr($1,10,length($1)); prio=""; for (i=2;i<NF;++i){ if ($i~/Priority: /){ prio=substr($i,11,length($i)); break }}; if (prio == "optional" || prio == "extra") print pkg }' > ~/additional-packages
cd ~
sudo aptitude reinstall $(cat additional-packages)

```

I see my post came at the right time :).

---

### Post by cheshirekow on 2010-06-28
Awesome. Thanks. I will follow your instructions and report back.

---

### Post by cheshirekow on 2010-06-28
Ok, it seems to have worked. I managed to reboot without a problem. When I did so I did not get the "File not found" error so that seems to have been a problem with wrong permissions. 

At this point everything seems functional except for my xfce panel wifi widget, which still displays red circle icons instead of signal strength icons. If you happen to know what that is please share, but I'll google around and ask in other places as well since I'm guessing that issues is (somewhat) unrelated. I'm sure it was caused by my not using cp -a, but I'm hoping there's a simple fix. Possibly the panel program isn't able to query the network driver for signal strength or something.

---

### Post by gzarkadas on 2010-06-28
I haven' t ever used xfce, so I doubt if I can help here. As a general rule, have a look at your syslog (click the log viewer app at System|Administration menu and scroll the list at the left to the line reading `syslog'), to identify messages that relate with the problem observed.

---

