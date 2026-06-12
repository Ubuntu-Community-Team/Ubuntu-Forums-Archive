---
title: "fsck option"
date: 2012-05-15
forum: General Help
---

### Post by ahso4271 on 2012-05-15
Hi
often, I suspect one app, 12.04 64bit doesn't boot anymore. Running fsck from 10.04 helps but I wonder how to set it automatically "if disc dirty run fsck" Any option somewhere?
Thanks

---

### Post by carl4926 on 2012-05-15
```
sudo touch /forcefsck
```

---

### Post by codemaniac on 2012-05-15
You can always run fsck manually .
```
fsck -F file_system_type partition
```

```
 fsck -F ufs -y /dev/sdb1 
```

---

### Post by dcstar on 2012-05-15
> **ahso4271 said:**
> Hi
often, I suspect one app, 12.04 64bit doesn't boot anymore. Running fsck from 10.04 helps but I wonder how to set it automatically "if disc dirty run fsck" Any option somewhere?
Thanks

[LIST=1]
[*]There are threads about a 12.04 bug that does not unmount filesystems cleanly when shutting down - you may be affected by this.
[*]fsck always runs on boot, that is set in the /etc/fstab file for each mount line.
[*]To have fsck automatically fix things during the boot scan, edit the /etc/default/rcS file.
[/LIST]

---

### Post by ahso4271 on 2012-05-15
> **dcstar said:**
> To have fsck automatically fix things during the boot scan, edit the /etc/default/rcS file.


Doesn't work, still hangs. fsck from 10.04 fixed it, so it's not hardware related?
Maybe in background waiting for input? setting verbose in that file has no effect as well. 
How to show boot messages alike in suse with escape key?

Sigh...I'll try this now:
sudo touch /forcefsck

---

### Post by ahso4271 on 2012-05-16
sudo touch /forcefsck

Thanks, that seems to work. But it takes long and I wonder what's going on. Can I see boot messages, alike in Suse with Esc key?

Thanks

---

### Post by codemaniac on 2012-05-16
> **ahso4271 said:**
> sudo touch /forcefsck

Thanks, that seems to work. But it takes long and I wonder what's going on. Can I see boot messages, alike in Suse with Esc key?

Thanks

You can see BOOT messages by pressing the esc key , only if grub is not quiet, i.e.: GRUB_CMDLINE_LINUX_DEFAULT="splash" .

Edit the file /etc/default/grub and set ```
GRUB_CMDLINE_LINUX_DEFAULT="splash"
``` 
After editing the file, you need to run update-grub.
```
sudo update-grub
```

---

### Post by ahso4271 on 2012-05-18
Thanks but ~ every 5 reboot it hangs. fsck from 10.04 helps but I wonder what's going on? Is my system 12.04 broken (not again :-()? Or how to find out if my disc is going nuts?

PS: now it mounts 12.04 read only! Is 12.04 that ugly? I've reinstalled all several times but still end up with new bugs....sigh  :frown:

What would I do without 10.04....I'd be fuc*

---

### Post by ahso4271 on 2012-05-18
makes it unusable...try mint tomorrow sigh and see if it's my disc.

---

### Post by carl4926 on 2012-05-18
> **ahso4271 said:**
> makes it unusable...try mint tomorrow sigh and see if it's my disc.
Give the RC a go it's great
[http://mint.mirror.root.lu/isos/testing/](http://mint.mirror.root.lu/isos/testing/)

---

