---
title: "How to rebuild NTFS-3G with integrated FUSE support and make it setuid root?"
date: 2011-01-07
forum: General Help
---

### Post by New00Folder on 2011-01-07
I'm using Ubuntu 10.04 and I want to mount my ntfs partitions using ntfs-3g, but there's an error message saying that

1> I must remove setuid/setgid bit from ntfs-3g binary
Or
2> Rebuild NTFS-3G with integrated FUSE support and make it setuid root.

Earlier 1st option was to mount as root and I did as suggested on tuxera.com.
```

sudo chown root $(which ntfs-3g)
sudo chmod 4755 $(which ntfs-3g)

```Then I started getting the above mentioned error.
So I figured 2nd option should be a better solution. But honestly speaking I don't know what it even means. Please explain me how and what is to be done.

---

### Post by GhodMode on 2011-01-24
Hi New00Folder.
I'm sorry you went two weeks without an answer to this question.  I know that this has been a problem for a long time and I'm surprised no one has fixed it.  I've looked for the solution to this before, but I always gave up and just mounted my external NTFS drive with sudo.

My solution:
[LIST]
[*]Download the source for the latest NTFS-3G from tuxera: [http://www.tuxera.com/community/ntfs-3g-download/](http://www.tuxera.com/community/ntfs-3g-download/)
[*]Extract it anywhere, then switch to the new directory:
```
tar xvzf ntfs-3g-2011.1.15.tgz
```
```
cd ntfs-3g-2011.1.15/
```
[*] Run the configure command with the argument [font=monospace]--with-fuse=internal[/font]
```
./configure --with-fuse=internal
```
[*] Execute [font=monospace]make[/font]
[*] When make completes, execute [font=monospace]make install[/font] with sudo
```
sudo make install
```
[/list]
If everything worked as expected, you should have a new ntfs-3g binary in /bin.  The one installed by the package manager was in /usr/bin.  This new one is the one you have to setuid root for.  Note that there's no need to setgid root.
```
sudo chmod 4755 `which ntfs-3g`
```

The final step is to ensure that your normal user has access to the device.  By default, disk devices are owned by the root user, associated with the "disk" group, and allow read/write access to the owner and the group.  So, you'll need to append your username to the line defining the disk group in /etc/group.  The line looks like this:
```
disk:x:6:ghodmode
```
That part after the last colon is a comma-separated list of usernames that are in the disk group.  Naturally, you have to use sudo to modify this file.

Finally, log out and back in so that your user's new group will be acknowledged and you'll be able to mount your partition as a normal user.

I have an entry in [font=monospace]/etc/fstab[/font] to make mounting easier.  It's usually /dev/sde1 on my system, but since my device is an external USB drive, it could get a different device file name.  So, I got the UUID from /dev/disk/by-uuid and used that in my fstab.
```
UUID=12C23AD8C23AC031 /mnt/My\040Book ntfs defaults,users,noauto 0 0
```


It would be so much easier if someone would just create an Ubuntu / Debian package for NTFS-3G with integrated support for FUSE.

--
-- Ghodmode
[http://www.ghodmode.com](http://www.ghodmode.com)

---

### Post by New00Folder on 2011-01-25
Hi GhodMode

First of all thanks a lot for your time. I did as you suggested and the partitions are being mounted in directories I want but there are two entries for each partition under the places menu; one is named like "54GB filesystem" and it works properly while the other entry is named as the mount directory and clicking on it give this error
```

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

```I tried ```

fuser -M /media/Music

```but I got no results.

The line I add in fstab is
```

UUID=08189ED7189EC35C    /media/Music/    ntfs-3g    auto,user,rw,exec 0 0

```

---

### Post by GhodMode on 2011-01-25
Make sure that your user ID owns the mount point.  I think I forgot to tell you that part.
```
sudo chown *youruserid* /media/Music
```

unmount it from the command line.  Use [FONT="Fixedsys"]sudo[/FONT] if you need to.
```
sudo umount /media/54GB\ filesystem
```
Then see what it says in Places.  You *might* be able to just click it there and Gnome will use the settings from the fstab file.

When it's not mounted, you should be able to use the following command to mount it as a normal user.
```
mount /media/Music
```

... and unmount it with the following command, still as a normal user.
```
umount /media/Music
```

If those both work, your permissions and fstab settings are all correct and you need to troubleshoot gnome-volume-manager.

I think gnome-volume-manager might have mounted your disk before you were able to make the necessary changes to the fstab and install NTFS-3G.  That would explain why you have two entries in your Places menu.

The "54GB filesystem" entry sounds like an entry that would have been automatically generated based on the volume label of the disc.

What does the other entry (the one that doesn't work) in the Places menu say?

Confirm where the disk is mounted.  From the console, just type [FONT="Fixedsys"]mount[/FONT] and it'll give you a list of device names and mount points.  I think that yours will say something like this:
```
/dev/sde1 on /media/54GB filesystem type fuseblk
```
If that's what it says, it's not using your fstab entry.
If it says [FONT="Fixedsys"]/media/Music[/FONT] after "on", then it is using your fstab entry.

Based on what I've read, gnome-volume-manager *should* check the fstab for settings before mounting a drive.

-- Ghodmode

---

### Post by New00Folder on 2011-01-25
Hi again!
Mount point is owned by the user. (By the way, do you really think it's a good idea?)

Partition doesn't get mounted in /media/54GB\ Filesystem but in the directory I want it to i.e. /media/Music.

I unmounted the partition and clicked on "Music" under places. There was the same error message about the volume being already mounted but instead (and at the same time) the partition got mounted at /dev/Music (as specified in fstab) which was acessible when I clicked on "54 GB Filesystem".

One thing I'd like to make clear at this point is that "54 GB Filesystem" is not a directory where the partition is mounted. Even when I had
```

/dev/sda6    /media/Music    ntfs    defaults,umask=007,gid=46,noatime

```in my fstab (before I decided to try this UUID stuff) I used to get one menu entry for the partition- "54 GB Filesystem". But now in addition to that I get an extra entry "Music" (it's the name of the mounting point) which doesn't work while the "54 GB Filesystem" still works.

mount isn't working without root privilege.

I suppose there's nothing wrong with fstab either because the partition is being mounted in the directory as specified in fstab and I don't use
```

sudo mount /dev/sda6 /media/Music

```to mount, but
```

sudo mount -a

```which mounts according to fstab.

---

### Post by Morbius1 on 2011-01-25
I couldn't quite follow your post but I'll take a crack at the first question:
>  Mount point is owned by the user. (By the way, do you really think it's a good idea?)You may have created the mountpoint and then changed ownership to userX but if this is your line in fstab:
> /dev/sda6    /media/Music    ntfs    defaults,umask=007,gid=46,noatimeIt's owned by root now.

To be exact it's owner:group = root-plugdev and permissions of 770. Even though it's owned by root all local login users have the ability to read/write/execute it's contents.

---

### Post by New00Folder on 2011-01-25
Hi Morbius

You are right about permissions. I changed the mounting point's owner to user only to make ntfs-3g work as suggested by GhodMode.

(I don't like this idea because there's a tiny arrow shaped button in my browser right beside the "54 GB Filesystem" button which unmounts the partition as user is the owner and has permissions to do so. This arrow button is too close and can be mistakenly pressed.)

In that case, I put the line
```

UUID=08189ED7189EC35C    /media/Music/    ntfs-3g    auto,user,rw,exec 0 0

```
in fstab.

The fstab entry you've quoted is what I had before I decided to use ntfs-3g.

---

### Post by GhodMode on 2011-01-26
> **New00Folder said:**
> 
You are right about permissions. I changed the mounting point's owner to user only to make ntfs-3g work as suggested by GhodMode.


NTFS-3G won't let a normal user mount the disk if the user doesn't have access to both the mount point and the device.  This is specified at the Tuxera FAQ.

The permissions shouldn't really be a problem.  The mount point is just an empty directory.  Even if it wasn't empty, it's only accessible to one user.  Also, as Morbius1 pointed out, the ownership changes when you mount it

You might want to check out the "Access Handling and Security" and "USER MAPPING" sections of the [COLOR="Blue"]_[ntfs-3g man page]("http://linux.die.net/man/8/ntfs-3g")_[/COLOR] for more detailed information.

[QUOTE=New00Folder]
(I don't like this idea because there's a tiny arrow shaped button in my browser right beside the "54 GB Filesystem" button which unmounts the partition as user is the owner and has permissions to do so. This arrow button is too close and can be mistakenly pressed.)
[/quote]

The placement of the unmount button (the tiny arrow) is a Gnome design thing.

If you don't want a normal user to have the right to mount/unmount the volume at all, there's no reason to rebuild NTFS-3G with integrated FUSE support.

If you want a normal user to be able to mount the volume, but not be able to unmount it, I don't think that's possible.  The two capabilities kind of go together.

[QUOTE=New00Folder]In that case, I put the line
```

UUID=08189ED7189EC35C    /media/Music/    ntfs-3g    auto,user,rw,exec 0 0

```
in fstab.

The fstab entry you've quoted is what I had before I decided to use ntfs-3g.[/QUOTE]

---

### Post by New00Folder on 2011-01-29
Looks like I did rebuild NTFS-3G with blah, blah, blah and make it work correctly but due some problem with nautilus there remains a confusion of menu entries.

---

### Post by crono141 on 2012-10-28
I hate to revive an old thread, but I'm recently having this problem as well.  After folowing the directions in the OP, when I try and mount my device by clicking in nautalus I get this error:

Error opening '/dev/sdc1': Permission denied
Failed to mount '/dev/sdc1': Permission denied
Please check '/dev/sdc1' and the ntfs-3g binary permissions,
and the mounting user ID.

My user ID is part of the disk group in the group file.  Clearly there's a permission issue here, but I don't know how to solve it.

Relevant line of fstab is as follows

> /dev/sdc1	/media/Media	ntfs-3g	rw,user,auto,exec,utf8 0	0

---

