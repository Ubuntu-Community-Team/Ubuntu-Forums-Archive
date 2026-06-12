---
title: "device file and the actual device"
date: 2010-09-23
forum: General Help
---

### Post by asemoon on 2010-09-23
Hi,
after entries are created in /dev folder for devices , when we ask a device for a service what mechanism figures out that which actual device should be used?

for example  I have 2 DVB cards on my system, both have entries in /dev folder like this :
```

$ls /dev/dvb/
adapter0 adapter1

```
when I ask adapter1 for a service how does it know it should use the second DVB card installed on my system? which mechanism is managing this?
and another question:
since every PCI device has an entry in /sys/bus/pci/devices/ , how can I find out that an entry in /dev folder belongs to which PCI device in /sys/bus/pci/devices/ directory , going back to my DVB cards example adapter1 belongs to /sys/bus/pci/devices/0000:03:08.0 but I want to figure it out using a shell command or something like that

---

### Post by sisco311 on 2010-09-23
udev manages the device nodes in /dev. It loads kernel modules by utilizing coding parallelism to provide a potential performance advantage versus loading these modules serially. The modules are therefore loaded asynchronously. So, you can't predict which DVB card will become adapter0 and which one adapter1.

But, udev provides persistent naming for some device types out of the box.

For example, to view the persistent names which have been created for your storage hardware, you can use the following command:
```
ls -alR /dev/disk/
```

If you are lucky, udev provides persistent names for your DVB cards too, to check it out, run something like:
```
find /dev/ -type l -exec ls -alh '{}' \; | grep adapter
```
If the command returns symbolic links which point to /dev/dvb/adapter*, then you could use this links, if not, then you have to write udev rules.

Check out the wikipedia page:
[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)
The Arch & Gentoo wiki pages are usually good:
[http://wiki.archlinux.org/index.php/Udev](http://wiki.archlinux.org/index.php/Udev)
[http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)
and
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

If you have any questions, please feel free to ask.

---

### Post by asemoon on 2010-09-24
thanks for the reply,
back in old days when there was no udev or on systems which device files are created statically (like some embedded systems) suppose we have 3 DVB cards installed on a system and we have manually created the device files for these 3 DVB cards, they work just fine, but there is a question about this:
when we request a service from the second dvb card,how does linux figure out which actual DVB card should be used?

---

