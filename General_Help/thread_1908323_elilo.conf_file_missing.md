---
title: "elilo.conf file missing"
date: 2012-01-13
forum: General Help
---

### Post by marcellux on 2012-01-13
Hello,

I decided to remove the GRUB bootloader on KUBUNTU 11.10 and replace it with ELILO.

I was searching this first in google!

I want to modify the ELILO's configuration file. Every forum I was visiting says I should be able to find it under /etc/elilo.conf and it should look something like this:

boot=/dev/hda
map=/boot/map
install=/boot/boot.b
compact
prompt
timeout=50
image=/boot/vmlinuz-2.0.36
    label=linux
    root=/dev/hda2
    read-only
other=/dev/hda1
    label=win

whenever I search for the file on my system, I cannot find it!

When I go to usr/sbin/elilo file,, this is what I found:

## define default config file
CONF=/etc/elilo.conf
bootconf=$CONF
ERR=" Error in $CONF:"

## define default configuration
boot=unconfigured

How can I modify this and why I do not have a elilo.conf file?

Thanks in advance

---

