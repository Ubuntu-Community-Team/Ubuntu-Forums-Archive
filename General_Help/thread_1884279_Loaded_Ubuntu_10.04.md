---
title: "Loaded Ubuntu 10.04"
date: 2011-11-21
forum: General Help
---

### Post by snakehorse on 2011-11-21
Is there Loaded Ubuntu 10.04 with VLC Player, Flash Plugins, and other required software components ?
Reason for asking is if one has to install it on a PC not having internet connection, it becomes difficult to get these softwares.

Regards.

---

### Post by pawanh on 2011-11-21
You could use *APTonCD* ([http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)) or *Sushi, huh?* to make a CD of all the software you'll need on the other computers. You can use this CD as a repository whenever you install again. But this won't work for Adobe flashplugin since the package itself downloads the files from Adobe. An alternative would be to use Gnash. Or you could use Linux Mint. It comes with these software preinstalled.

---

### Post by snakehorse on 2011-11-22
Is CloneZilla for the same purpose ? or it clones the whole disk ?

Can I create ISO for the whole installation, including whole packages ?  Wwould aptoncd take care of that ? Are Softwares from Software center included n the ISO ?

Thanks in advance.

---

### Post by jjex22 on 2011-11-22
If I'm understanding, I think this may help:

[capink's thread]("http://ubuntuforums.org/showthread.php?t=688872")

---

### Post by dandnsmith on 2011-11-22
I've used *partimage* for the purpose of copying a configured Ubuntu 10.04 to another PC.
I believe it does much the same thing as clonezilla, but has no fancy GUI (invoke from a terminal, have primitive graphics interface to operate with) - indeed, it's possible (comment I read somewhere) that clonezilla invokes partimage.

Advantages are:
- you can see what's happening,
- it operates on one partition to create an image (must be unmounted),
- can be restored to a partition (which it overwrites) - but that must be at least as large as the original
- partimage can be installed from the Ubuntu repositories
- partimage is available as part of the SysRescue CD software.

What you do have to consider is how you make the image available for the restore operation (USB stick ...)
HTH

---

### Post by mikewhatever on 2011-11-22
> **snakehorse said:**
> Is there Loaded Ubuntu 10.04 with VLC Player, Flash Plugins, and other required software components ?
Reason for asking is if one has to install it on a PC not having internet connection, it becomes difficult to get these softwares.

Regards.

Hm..., what would you use Flash for on a PC without internet?

---

### Post by snakehorse on 2011-11-22
I want to install image on another PC. It has Windows XP on it. Can I use this Image to install it using Imaging Software within Windows xp, without using USB or DVD ?

Regards.

---

### Post by dandnsmith on 2011-11-22
If you want to install it within XP, rather than alongside, do you want it as a virtual machine install, or as a dual-boot install.
In the former case you'll need to check out the ways and means and use a  configured image (cf capink's link in earlier post), in the latter case then a bootable CD which is configured with wubi would be needed.

Are you sure you know the implications of each method, or, alternatively, exactly what you want to achieve when the install is complete?

---

### Post by snakehorse on 2011-11-30
Apton CD did the trick. Thanks.

---

