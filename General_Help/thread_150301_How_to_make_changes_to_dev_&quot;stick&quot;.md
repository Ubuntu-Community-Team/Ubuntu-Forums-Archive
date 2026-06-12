---
title: "How to make changes to /dev/ &quot;stick&quot;??"
date: 2006-03-25
forum: General Help
---

### Post by Kadin2048 on 2006-03-25
I need to change a few things in /dev ... specifically I need to add "generic" SCSI devices, like /dev/sg0, and I also want to make a symlink between /dev/tape/ and /dev/nst0.

However every time I make the changes, (the generic devices I get with modprobe sg, the other by making a symlink and changing the permissions), it just gets reset when I reboot. It's like /dev/ is just getting reset to some factory default every time I restart.

How do I stop this from happening?

The only way I've figured out so far is just to add some lines to the bottom of /etc/init.d/bootmisc.sh, but this seems like a really inelegant way to do things -- it just seems unreal that I have to run:
modprobe sg
ln -s /dev/nst0 /dev/tape
chmod 777 /dev/tape

EVERY time I reboot, just to get these changes made ... is that really the case? It seems like a really stupid way to have to do things.

Anybody have any ideas of a better way?

---

### Post by Barrakketh on 2006-03-25
[QUOTE=Kadin2048]However every time I make the changes, (the generic devices I get with modprobe sg, the other by making a symlink and changing the permissions), it just gets reset when I reboot. It's like /dev/ is just getting reset to some factory default every time I restart.[/quote]
Eh...it is.  Read the [url=
http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev-FAQ]FAQ for udev[/url] as well as [links on this page](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html) to learn more about it.  It's filesystem is of type "tmpfs", so I think you can guess why it's reset every boot ^_^
> How do I stop this from happening?
You could create another filesystem to mount it on, but that's probably beyond most of us here :D
> The only way I've figured out so far is just to add some lines to the bottom of /etc/init.d/bootmisc.sh, but this seems like a really inelegant way to do things -- it just seems unreal that I have to run:
modprobe sg
ln -s /dev/nst0 /dev/tape
chmod 777 /dev/tape

EVERY time I reboot, just to get these changes made ... is that really the case? It seems like a really stupid way to have to do things.
More or less, but if you want to try something new you can read [Writing udev rules](http://www.reactivated.net/writing_udev_rules.html).

EDIT:  Here's something else from a comparison of udev and devfs
> Provide a persistent device naming solution:
    Lots of people want to assign a specific name that they can talk to
    a device to, no matter where it is in the system, or what order they
    plugged the device in.  USB printers, SCSI disks, PCI sound cards,
    Firewire disks, USB mice, and lots of other devices all need to be
    assigned a name in a consistent manner (udev doesn't handle network
    devices, naming them is already a solved solution, using nameif).
    udev allows users to create simple rules to describe what device to
    name.  If users want to call a program running a large database
    half-way around the world, asking it what to name this device, it
    can.  We don't put the naming database into the kernel (like other
    Unix variants have), everything is in userspace, and easily
    accessible.  You can even run a perl script to name your device if
    you are that crazy...

    For more information on how to create udev rules to name devices,
    please see the udev man page, and look at the example udev rules
    that ship with the tarball.

---

### Post by Kadin2048 on 2006-03-26
Thanks for the info, Barrakketh. It seems like that is the "right" way to do what I'm looking for ... making the symlinks seem easy enough (from /dev/tape to /dev/nst0 and /dev/changer to /dev/sg0, respectively), but getting it to create the generic SCSI devices like /dev/sg0 in the first place is less clear.

I guess I may just stick with my slovenly hack for now...

---

