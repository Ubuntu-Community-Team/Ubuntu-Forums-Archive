---
title: "how to rename a nic name ( eth1 to eth0)"
date: 2010-01-29
forum: General Help
---

### Post by ulao on 2010-01-29
So I changed a nic out, and I want the new nic to use the old name "eth0". I looked for the 70-persistent-net.rules files buts its not in rules.d? How do I change it back to eth0?
thx!

,y 25-iftab.rules only has subsystem action and driver. Some sources suggest to delete it and reboot?


I see sys/class/net shows only lo and eth1, surly I cant rename that and reboot?

---

### Post by falconindy on 2010-01-29
/sys is a dynamically generated pseudo-filesystem. Changes made there won't be saved. You'll need to write the udev rule. Rather than reinvent the wheel, I'll just quote someone smarter than me:
> Even though they are referenced by names, network interfaces typically do not have device nodes associated with them. Despite that, the rule writing process is almost identical.

It makes sense to simply match the MAC address of your interface in the rule, as this is unique. However, make sure that you use the exact MAC address as shown as udevinfo, because if you do not match the case exactly, your rule will not work.

```
# udevinfo -a -p /sys/class/net/eth0
  looking at class device '/sys/class/net/eth0':
    KERNEL=="eth0"
    ATTR{address}=="00:52:8b:d5:04:48"
```
Here is my rule:

```
KERNEL=="eth*", ATTR{address}=="00:52:8b:d5:04:48", NAME="lan"
```
You will need to reload the net driver for this rule to take effect. You can either unload and reload the module, or simply reboot the system. You will also need to reconfigure your system to use "lan" rather than "eth0". I had some troubles getting this going (the interface wasn't being renamed) until I had completely dropped all references to eth0. After that, you should be able to use "lan" instead of "eth0" in any calls to ifconfig or similar utilities.
The only thing to watch out for here is that udevinfo is deprecated in favor of udevadm, so the command given should actually be:
```
udevadm info -q all -p /sys/class/net/eth0
```
Then you can alter the rule given with the information obtained from udevadm. You can just create the 70-persistent-net.rules file in /etc/udev/rules.d if it's not there.

---

### Post by ulao on 2010-01-29
sorry dup

---

### Post by ulao on 2010-01-29
Ok so its just a matter of getting that file in there? Figured it was getting eth1 from somewhere?

So I grabbed the info from eth1 and made my file


SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:07:e9:0f:e6:30", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


but eth1 is still showing up after the reboot?

If I delete 25-iftab.rules its recreated on boot, but not so with 70-persistent-net.rules

BTW: I'm using feisty 7.04 and it was still udevinfo

---

### Post by ulao on 2010-01-29
I just found an old referance in /etc/iftab
 
eth0 mac 00:0a:7c:e4:ea:34 arp 1

This is the wrong mac addy, change it to the correct one and rebooted. All back up.

---

