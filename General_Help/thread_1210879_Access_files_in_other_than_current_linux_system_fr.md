---
title: "Access files in other than current linux system from terminal"
date: 2009-07-12
forum: General Help
---

### Post by healee on 2009-07-12
How do we access files in CD drive or DVD drive or other partitions in the same computer or networked drives be they Windows or Linux from the terminal using command such as ls, mv, cp and so on?

---

### Post by Finalfantasykid on 2009-07-12
I might be wrong about this, but for me at least you should be able to find it at /media.

so just go

$> cd /media
$> ls 

That should give you a list of cd/dvd and other partitions, maybe usb storage devices.  I don't know about accessing networked computers though...

---

### Post by healee on 2009-07-12
Thanks a lot!  It doesn't seem to show other partitions on the same computer either.  In my case, it shows only the following, "cdrom cdrom0 cdrom1 floppy floppy0".

Apart from accessing the files from the terminal, another reason for me to ask is I want to set up shared areas in other partitions such as Windows on the same computer for access from networked computer using samba.  Hence I need to be able to have the paths in the format recognizable by samba besides "ls" and so forth.

---

### Post by The Question on 2010-05-31
Anybody have an answer to this question?

I am trying to setup grub to load a kernel on another partition.

---

### Post by Serpher on 2010-05-31
If you're talking about GRUB's command line where it says initframs, that's not the same shell Ubuntu or really any Linux distro anybody knows about uses. However if you are using the bash shell (Terminal when you get into Ubuntu), run these commands.

```
sudo -i
mkdir /media/mnt/
mount /dev/sda1 / /media/mnt/
cd /media/mnt/
```

The 1 after sda may be any number, usually 1-4 though. It's your partition number and anything 5 and above is a logical partition. You might want to run 'ls /dev/sda?' to see your partitions.

---

### Post by The Question on 2010-06-01
Well, I was talking about both normal terminal command line and grub command line.  I figured they would be the same.

As far as Bash prompt: I tried what you wrote, or what I assume you meant since what you wrote exactly didn't work:

sudo -i
mkdir /media/mnt
mount /dev/sda1 /media/mnt
cd /media/mnt

After line 3 it says unknown filesystem type ext4.  I am running 8.10 and trying to mount a 10.04 partition btw and I know the file systems are different.

As far as the grub command line goes:

What I was really after was the syntax for the kernel command in GRUB legacy, to point it to the kernel on the 10.04 partition.  The point of all this is that I want to boot up with Ubuntu 10.04.  I'm not sure what you mean by initframs.  Here, I'm talking about the grub command prompt one gets by typing ESC at boot up and then C.  One might normally type for example:

kernel /boot/vmlinuz-2.6.27-21-generic

I'm looking for what to put in front of /boot... to switch to the other partition.  Maybe it's not possible because of the ext4 filesystem, I don't know.

Anyway, here is some results of commands I entered:

nick@gollum:~$ ls /dev/sda?
/dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7
nick@gollum:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="974c36e9-cf8d-411d-9301-891f40d1e4da" TYPE="ext4" 
/dev/sda5: UUID="6d8fb15d-79c6-4c2e-a347-da3c63e8b091" TYPE="swap" 
/dev/sda6: UUID="c10ebddc-d930-4df5-90c1-edf6e8cf6bfb" TYPE="ext3" 
/dev/sda7: UUID="7c44d7fd-55d4-4cee-af93-8bace96424a7" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
nick@gollum:~$ 

Thanks for the help.

---

