---
title: "no comunication between disk and OS"
date: 2010-11-16
forum: General Help
---

### Post by etejos on 2010-11-16
about 2 months ago, I bought a Samsung laptop (model NP-R430) Inmmediatly I installed Ubuntu. well,the machine worked very well until something unexpected happened. something like this:

Target filesystem doesn't have /sbin/init
run-time:/etc/init: permission denied

I don't know what happend. I could install windows again, but, I don't want return to windows.

could someone help me please?

Ed

---

### Post by WorMzy on 2010-11-16
The first order of business would be to boot a LiveCD/USB and run fsck on your root partition:
[LIST=1]
[*]Open a terminal (Applications -> Accessories -> Terminal)*
[*]Find out what partition is your root partition by running ```
sudo blkid
``` and looking for the one with 'type="ext4"'. Make a note of the /dev/sdXY identifier, that's the bit you need for fsck.
[*]Run fsck. If necessary, replace "[COLOR="Red"]/dev/sda1[/COLOR]" with the information discovered with blkid: ```
e2fsck -fcp [COLOR="Red"]/dev/sda1[/COLOR]
```
[/LIST]

If that fixes your partition, great. If not, and fsck gives you an error, post it here so we can advise you further. If not, and fsck says everything's fine, then the problem isn't with the partition itself, and I suspect you may have inadvertently borked it through the use of a sudo command. In this event, the time it may take to repair would be dependant on what you did, and a reinstall would be the advised solution in many of these cases. Did you run any "sudo rm", "sudo chown", "sudo chmod", etc, commands before the problem started?


*NOTE: If you're using the Netbook Remix or whatever it's called, with the new Unity interface, this may not be the case for you. In this event, browse the menus until you find "Terminal".

---

