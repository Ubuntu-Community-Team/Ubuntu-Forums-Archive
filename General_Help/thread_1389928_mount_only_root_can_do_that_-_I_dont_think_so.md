---
title: "mount: only root can do that - I dont think so"
date: 2010-01-25
forum: General Help
---

### Post by kaveraj on 2010-01-25
I have an external usb hard disk with 2 partitions. They are defined in fstab as follows:
```
UUID=...   /media/ext-music    ext3    user,auto,rw    0   0
UUID=...   /media/ext-videos    xfs    user,auto,rw    0   0
```

I dont know why the system doesnt automount when the usb hdd is switched on. But what is really strange is:

```
mohanr@hp:~$ mount /media/ext-*
mount: only root can do that

mohanr@hp:~$ mount /media/ext-music
mohanr@hp:~$ mount /media/ext-videos
```

Those are the only 2 partitions under /media and I dont understand why placing a * while mounting have to automatically require root privileges, when I can mount all individual relevant partitions  without any problems.

---

### Post by sgosnell on 2010-01-25
From the mount man pages:
```

The non-superuser mounts.
              Normally,  only  the superuser can mount file systems.  However,
              when fstab contains the user option on a line, anybody can mount
              the corresponding system.

              Thus, given a line

                     /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any  user  can  mount the iso9660 file system found on his CDROM
              using the command

                     mount /dev/cdrom

              or

                     mount /cd

              For more details, see fstab(5).  Only the user  that  mounted  a
              filesystem  can unmount it again.  If any user should be able to
              unmount, then use users instead of user in the fstab line.   The
              owner option is similar to the user option, with the restriction
              that the user must be the owner of the special file. This may be
              useful e.g. for /dev/fd if a login script makes the console user
              owner of this device.  The group option  is  similar,  with  the
              restriction  that  the  user  must be member of the group of the
              special file.


```
COMMAND LINE OPTIONS
       The full set of mount options used by an invocation of mount is  deter&#8208;
       mined  by  first  extracting the mount options for the file system from
       the fstab table, then applying any options specified by  the  -o  argu&#8208;
       ment, and finally applying a -r or -w option, when present.

       Command line options available for the mount command:
       -V     Output version.

       -h     Print a help message.

       -v     Verbose mode.

       -a     Mount all filesystems (of the given types) mentioned in fstab.


Probably the way to mount both the partitions with one command would be ```

mount -a 
```

---

### Post by kaveraj on 2010-01-29
mount -a still requires root privileges 

What I am trying to get at is that there might be something wrong in the basic design of the program itself when it is functionally inconsistent ..

---

### Post by sgosnell on 2010-01-29
It's not inconsistent.  By design, anyone can mount a drive listed in fstab with the user option.  Other drives require superuser privileges.  Your drives clearly have the user option, and can be mounted by anyone.  /media/ext-* is not listed in fstab, so mounting that (those) requires sudo.  Wildcards don't work here.

---

### Post by kaveraj on 2010-01-30
But isnt the wildcard supposed to be preprocessed and expanded before being passed on to the programs. I guess that is how things worked. 

Even otherwise, dont you see the logical dissonance here. Wildcards are a basic feature - saying that it doesnt work because it is not listed in fstab - is not strong reasoning

---

### Post by sgosnell on 2010-01-30
Wildcards don't work during the boot sequence.  Everything is interpreted literally, AFAIK.  GRUB doesn't pass anything to programs, it just boots.  BASH knows about wildcards, but I don't think GRUB does.

---

### Post by falconindy on 2010-01-30
Mount isn't behaving inconsistently. You're trying to insist upon functionality that isn't implemented. Globbing is done by Bash, and doesn't have this level of awareness that you want. Even if it did work, you aren't able to specify multiple mounts in a single command.

You **can** do something like this...

```
mounts=('mounts' 'videos')
for mount in ${mounts[@]}; do mount /media/ext-$mount; done
```

So that you only need to maintain the mounts array.

---

