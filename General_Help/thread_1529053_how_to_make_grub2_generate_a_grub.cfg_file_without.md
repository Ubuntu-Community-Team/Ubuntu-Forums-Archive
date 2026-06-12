---
title: "how to make grub2 generate a grub.cfg file without UUIDs?"
date: 2010-07-11
forum: General Help
---

### Post by MountainX on 2010-07-11
I want to do everything with disk labels. My /etc/fstab is already set up for labels.

How can I tell grub2 to use labels? I need it to stop using UUID for root.
Thanks

---

### Post by confused57 on 2010-07-11
I think there's an option in /etc/default/grub to disable using UUID's in the root parameter:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

---

### Post by MountainX on 2010-07-11
> **confused57 said:**
> I think there's an option in /etc/default/grub to disable using UUID's in the root parameter:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

Yes, there is. But I have two issues:
1. this parameter is buggy*
2. I want to enable labels, not just disable UUID.

So I'm looking for a good solution.

> *A bug currently requires true be placed within quotation marks for this option, when uncommented, to take effect. Quotation marks currently are not the default and the user must add them.

Does that mean I have to use single quotes, double quotes, or what? And when the bug is fixed, what will be the result of using quotes? This bug just creates so many questions...

---

### Post by confused57 on 2010-07-11
```
#GRUB_DISABLE_LINUX_UUID="true"

    * Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    *

      A bug currently requires true be placed within quotation marks for this option, when uncommented, to take effect. Quotation marks currently are not the default and the user must add them.
```
It appears to me that the quotes are already added & that you just need to uncomment the above mentioned parameter.  I don't know if it'll automatically use /dev/sdx, instead of UUID's after disabling this option.

Your best option would probably be to create custom entries, then disable os-prober during update grub.  I mainly using Hardy 8.04, so I'm not that fluent with grub2, but there are plenty of other users who can give you more specific instructions for doing this.

---

### Post by oldfred on 2010-07-11
If you want to do custom

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by MountainX on 2010-07-11
> **oldfred said:**
> 
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

oldfred, thanks! those are great links. It will take me a while to read all of that. At first glance, I don't see any tweaks to change grub from using UUID's to using file system labels. However, there is a lot of other good stuff in there.

---

