---
title: "Grub Help"
date: 2011-02-15
forum: General Help
---

### Post by cdslaughter on 2011-02-15
Ubuntu and Grub2

This is probably more of a grub question that a ubuntu but I thought a better community  would provide a  better solution.

I have a default load of 10.04 32 bit and I am trying to create an alternative boot option that allows me to boot dban and run the autonuke option. I have a cd that does this and has proven it's self useful in the past. Although keeping the cd in the optical drive tray is still possible, I really want this as a normal boot option loaded from the local disk.

I have been able to get it to boot into the tool, but unlike the cd where the --autonuke option starts a disk wipe without user assistance, when loading from the local disk it just launches the tool and waits for the user to initiate the wipe.

What appears to be the issue is it fails to pass the arguments to the dban loader. (See Below)

```

menuentry "Recovery Tools" {
        linux16 /boot/dban/dban.bzi nuke="dwipe --autonuke --method zero" silent root=/dev/ram0 init=/rc console=ttyS0,115200n8
}

```Anyone have any ideas?

---

