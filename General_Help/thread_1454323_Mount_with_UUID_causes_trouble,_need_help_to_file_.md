---
title: "Mount with UUID causes trouble, need help to file bug report"
date: 2010-04-14
forum: General Help
---

### Post by vintermann on 2010-04-14
Today I had a problem with Ubuntu that grandma would not have managed to fix. I hate when that happens. It scared *me* too, for a moment I thought my disk was dead. I want to file a bug report, and I want your help in finding things to include.

I just booted up, and by the time I came to mounting filesystem, it reported a failure and hung at "starting crypto disks". Tried a reboot, same thing happened. Reading a bit carefully, I see that it's my home partition that's failed to mount, and I can go into an emergency shell with esc. OK, I do that, try to mount it with mountall, it just reports "can't find device with UUID= ... ". I fear the worst. Run fsck on it, disk clean, try remount again, no effect. But wait, haven't I had trouble with these UUID things before? (yes, I have!) On a hunch, I mount it without going through fstab ("mount -t ext4 /dev/sda5 /home") - it works. Whew. ctrl-d, rest of boot process goes fine. 

Presumably the UUID got erased for some reason. blkid lists an id for my root partition, but none for my home partition, either without arguments or the device name as argument. I have no idea what could have caused it. According to my logs I turned it on around 8:00, off around 10:00, and then when I turned it on again at 17:00 it wouldn't boot. No packages were installed in this time frame according to the logs, and as far as I can remember I did nothing whatsoever as root this morning.

It's bad, bad, that crippling errors that grandma can't recover from can suddenly pop up for no apparent reason. But I think they still prioritize sysadmins over grandmothers at Canonical, so I'm probably not going to be able to convince them to switch back to device-based mounting... they'll probably just close this bug unless I manage to find out just *how* that UUID got erased. That's what I need your help in finding out - I'm all out of ideas :(

---

