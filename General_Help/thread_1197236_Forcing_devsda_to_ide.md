---
title: "Forcing /dev/sda to ide"
date: 2009-06-25
forum: General Help
---

### Post by SandmanCL on 2009-06-25
I recently installed 9.04 on a system with a Asus P5Q-EM motherboard that has one IDE connector and 6 SATA connectors.

On the IDE connector I have an old 250GB drive for a master that I use as my system drive, and a DVD-rom as slave.

I currently have 4 sata drives hooked up, and they are mounted as /dev/sda through /dev/sdd, while my IDE drive is currently /dev/sde.

If I add a 5th drive, the IDE drives become /dev/sdf. With the way drives are mounted it doesn't seem to make a difference, but I have a slight OCD when it comes to these things and would feel much more comfortable with /dev/sda always being my system disk.

Is there a way to force this, through grub.conf or other ways ?

The AMI bios on the motherboard lets me configure which drive is the "1st drive" and I have set this to be my IDE drive. But this doesn't seem to have any effect in Linux.


Any pointers appreciated !

Thank you

---

### Post by evilmonk on 2009-10-26
I would like to know how to do that as well. I have a small file/print server with one 80GB IDE HDD with the system, four internal SATA drives in RAID-5 and one 1TB removable SATA drive for backup purposes. Everything works well until I have to leave the system without the backup drive for a few days. The IDE gets shifted from sdf to sde, and I have to connect a monitor+keyboard to get the system running, because GRUB cannot find root.

Is there a working solution to make the IDE drive the first one?

---

### Post by capscrew on 2009-10-26
[QUOTE=SandmanCL]...I have a slight OCD when it comes to these things and would feel much more comfortable with /dev/sda always being my system disk.
[/QUOTE]
...
[QUOTE=evilmonk]I would like to know how to do that as well. I have a small file/print server with one 80GB IDE HDD with the system, four internal SATA drives in RAID-5 and one 1TB removable SATA drive for backup purposes. Everything works well until I have to leave the system without the backup drive for a few days. The IDE gets shifted from sdf to sde, and I have to connect a monitor+keyboard to get the system running, because GRUB cannot find root.

Is there a working solution to make the IDE drive the first one?[/QUOTE]

With Linux the drive ID is by the order of discovery. This means that they can (and as you experienced) change the drive ID.

You should use the UUID of the partition. This never changes. To see the UUID try this

```
sudo blkid
```

You should see the UUID for the device. The Drive ID will change but the UUID never does.

See the usage in /etc/fstab file.

---

### Post by evilmonk on 2009-10-27
OK, so I have to use UUIDs in GRUB then... But won't I have to rewrite the grub.cfg file every time a new kernel update appears? It's automatically generated, if I'm not mistaken.

It's a bit sad, that the Ubuntu kernel maps both PATA and SATA drives starting with "s", if there was an option for the old hdX/sdX naming, there would be no such problems.

---

### Post by QLee on 2009-10-27
[QUOTE=evilmonk]OK, so I have to use UUIDs in GRUB then... But won't I have to rewrite the grub.cfg file every time a new kernel update appears? It's automatically generated, if I'm not mistaken.[/QUOTE]

The UUIDs remain the same through a kernel upgrade. UUID is set when you format the partition.

---

### Post by alphaniner on 2009-10-27
> **evilmonk said:**
> It's a bit sad, that the Ubuntu kernel maps both PATA and SATA drives starting with "s", if there was an option for the old hdX/sdX naming, there would be no such problems.

It's not Ubuntu's doing.  Every Linux kernel uses this method now.

I just noticed that my menu.list is using UUIDs, that was a surprise!  Here's one entry:

```
title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		559ec8f0-3361-429d-8da8-092c238cef51
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=559ec8f0-3361-429d-8da8-092c238cef51 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet
```

I'll post the rest if you would like.  What does your menu.list look like?

---

### Post by mcduck on 2009-10-27
> **evilmonk said:**
> OK, so I have to use UUIDs in GRUB then... But won't I have to rewrite the grub.cfg file every time a new kernel update appears? It's automatically generated, if I'm not mistaken.

It's a bit sad, that the Ubuntu kernel maps both PATA and SATA drives starting with "s", if there was an option for the old hdX/sdX naming, there would be no such problems.

Like said, the UUID will stay the same unless you format the drive/partition.

Besides, you shouldn't even be touching the grub.cfg in the first place (it even says so in the beginning of that file). Grub2 is configured in /etc/grub.d/ and /etc/default/grub

(and it's not only Ubuntu kernel that maps the drives this way. Any recent Linux kernel does this, since ll PATA, SATA and SCSI drives are now handled by the same driver.)

---

### Post by evilmonk on 2009-10-27
> **alphaniner said:**
> I'll post the rest if you would like.  What does your menu.list look like?
Do you mean the /boot/grub/menu.lst? I think I don't have one or it's not there. I use GRUB2, since it is the default for Karmic.

> **mcduck said:**
> Like said, the UUID will stay the same unless you format the drive/partition.

Besides, you shouldn't even be touching the grub.cfg in the first place (it even says so in the beginning of that file). Grub2 is configured in /etc/grub.d/ and /etc/default/grub

In that case I don't know why isn't it using UUIDs in the first place. Here's what a part of my grub.cfg looks like:

```
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        linux   /boot/vmlinuz-2.6.31-14-generic-pae root=/dev/sdf1 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-14-generic-pae
}
```but /etc/default/grub is configured to use UUIDs from the very beginning, i.e. I haven't modified it since installation:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Must I change something somewhere else?

---

### Post by alphaniner on 2009-10-27
You're right about the menu.list.  You won't have one.  Didn't think about the GRUB2 issue, sorry about that.

---

### Post by mcduck on 2009-10-27
That should work, beats me why it's not using the UUID. Have you tried simply running "sudo update-grub" to see if the UUID's are used correctly after that?

---

### Post by dcstar on 2009-10-27
9.10 users can simply install the old **grub** package and then:
```
sudo update-grub
```
to generate a menu.lst file that you can then use with UUIDs as outlined above.

---

### Post by evilmonk on 2009-10-28
> **mcduck said:**
> Have you tried simply running "sudo update-grub" to see if the UUID's are used correctly after that?
It told me:
```
grub-probe: error: Cannot find a GRUB drive for /dev/sdf1.  Check your device.map.
```So I checked the device.map and saw
```
(hd0)   /dev/sda
```So I changed "sda" to "sdf", ran update-grub again and it successfully changed grub.cfg to use UUIDs. So now the system reboots fine either with the backup drive or without it. Problem solved, I guess. Now I hope that  device.map stays that way even after a kernel upgrade.

---

### Post by CharlesA on 2009-10-28
> **alphaniner said:**
> It's not Ubuntu's doing.  Every Linux kernel uses this method now.

Does the same apply to other distros? I know that Clonezilla uses "hd*" for IDE drives and "sd*" for SATA drives. The files can be renamed for restoration on IDE or SATA drives, so it's not a huge deal, but I'm curious as to when they changed everything over to using sd*.

---

### Post by mcduck on 2009-10-28
> **CharlesA said:**
> Does the same apply to other distros? I know that Clonezilla uses "hd*" for IDE drives and "sd*" for SATA drives. The files can be renamed for restoration on IDE or SATA drives, so it's not a huge deal, but I'm curious as to when they changed everything over to using sd*.

Yes, it applies to all distros that use recent kernel versions.

The change was made because the developers found out that the SATA/SCSI driver handles PATA drives better than the original PATA driver did. So they simply started using that driver for all PATA/SATA/SCSI drives, which resulted in all these drives using the same naming scheme as well.

---

### Post by alphaniner on 2009-10-28
When you put it that way it sounds like pure laziness.

---

### Post by mcduck on 2009-10-28
> **alphaniner said:**
> When you put it that way it sounds like pure laziness.

Laziness? Why?

They have a driver that handles the job very well, why should they do anything else than use that driver? Use inferior driver instead, or do twice the work for no benefits, just because some people might not like all their hard drives using a common naming scheme?

---

### Post by alphaniner on 2009-10-28
Lazy because as a consequence (as opposed to by design), the established means of naming drives got thrown out the window.  I wasn't criticizing the choice though.

---

### Post by CharlesA on 2009-10-29
> **mcduck said:**
> Yes, it applies to all distros that use recent kernel versions.

The change was made because the developers found out that the SATA/SCSI driver handles PATA drives better than the original PATA driver did. So they simply started using that driver for all PATA/SATA/SCSI drives, which resulted in all these drives using the same naming scheme as well.

Gotcha. That's quite nifty. ;)

Thanks for the info.

---

