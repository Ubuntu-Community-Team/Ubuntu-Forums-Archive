---
title: "Dueling Distros: Ubuntu's mangled /home/home"
date: 2006-01-29
forum: General Help
---

### Post by Ambidistastrous on 2006-01-29
After a clumsy installation of Demudi that was meant to share hda with Ubuntu, the home directory on Ubuntu's partition got jacked and it's only possible to log in using rescue mode or the safe terminal emulator.

Background:

I made a clean install of Breezy Badger 5.10 onto its own 80GB hard drive in a fairly old personal computer. All good, so I put some files in the home folder, and then started an installation of DeMuDi on a smaller partition on the same hard drive.

Partitioning hda was the problem: Given hda1 and a swap hda5, I resized hda1 and created a ~15GB hda3. Then I mistakenly put hda1 as the partition to be used for the root filesystem, and hda3 as home. Wrote to the partition table and continued. When the partition editor complained that an existing operating system would be erased, I went back and set hda1 as unused and hda3 as the root filesystem, which I think is correct... then I finished installing DeMuDi, which loaded correctly.

On logging into Ubuntu as a user, an alert says that the home directory was not found, and so GNOME can't load. 

Investigating by terminal, Ubuntu shows that I now have nested home directories: 
[FONT="Fixedsys"]/home/home/thisuser[/FONT]
instead of 
[FONT="Fixedsys"]/home/thisuser[/FONT]

The permissions look correct. However, this rogue home directory actually contains DeMuDi's default Desktop/README.TXT instead of the files I had on Ubuntu.

Finally, the Knoppix Live CD mounts all partitions correctly and shows the file systems as they should be: 
[FONT="Fixedsys"]hda1[/FONT] is the Ubuntu structure with my home directory and files in place, **not** the nested mess shown from within Ubuntu.
[FONT="Fixedsys"]hda3[/FONT] is DeMuDi, with just the readme file on the Desktop.
[FONT="Fixedsys"]hdb1[/FONT] is a Windows morass in need of forensics, which I won't get into here.

Corrective action:

Can I restore hda1 to the way Knoppix sees it? Or do I have to use Knoppix to copy my files to someplace safe and re-install Ubuntu? And how do I do that?

---

### Post by mcmillan on 2006-01-29
My guess is something weird happened with your fstab. Maybe you could post the fstab from ubuntu and we can try to sort it out.

---

### Post by Ambidistastrous on 2006-01-29
OK, here's the fstab information from both sides.

From Ubuntu:
```

# /etc/fstab: static file system information.
#
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc		/proc		proc	defaults	0	0
/dev/hda1	/		ext3	defaults,errors=remount-ro 0	1
/dev/hda3	/home		ext3	defaults	0	2
/dev/hda5	none		swap	sw		0	0
/dev/hdc	/media/cdrom	iso9660	ro,user,noauto	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	0

```

From DeMuDi:
```

# /etc/fstab: static file system information.
#
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc		/proc		proc	defaults	0	0
/dev/hda3	/		ext3	defaults,errors=remount-ro 0	1
/dev/hda5	none		swap	sw		0	0
/dev/hdc	/media/cdrom	iso9660	ro,user,noauto	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	0

```

Thanks for your help.

---

### Post by mcmillan on 2006-01-29
Ok I think I see what happened. When you said:

> Then I mistakenly put hda1 as the partition to be used for the root filesystem, and hda3 as home
It looks like the fstab got written with this setup. I'm guessing you have just have one partition for ubuntu and one for DeMudi. If this is the case you can delete the line for hda3 in your ubuntu fstab. I think that should make ubuntu work. 

Alternatively you can keep the line, but just edit it so instead of mounting at /home it mounts something like /mnt/demudi (you would have to make this directory). This will make it easy if you ever want to mount that partition while in ubuntu, sometimes useful for troubleshooting. If you do that I would recommend changing defaults to noauto so it will only mount when you want to use it instead of at startup. You can also do a similar thing in demudi to create a mount point for ubuntu.

---

### Post by Ambidistastrous on 2006-01-29
Brilliant! Worked like a charm.

Thank you very much.

---

