---
title: "Grub2 Editing - editing directly to /boot/grub/grub.cfg"
date: 2010-06-06
forum: General Help
---

### Post by bobnutfield on 2010-06-06
Hello Everyone,

I have an old laptop that I installed EasyPeasy Lucid on.  I have never used Grub2 as my other Ubuntu installs still use Grub Legacy.  I have studied all the tutorials which instruct that the grub.cfg file should not be edited directly.

This old laptop has one of the dreaded Intel graphics chips for which the kernel automatically loads the i915 module.  Of course (like a multitude of others with Intel graphics and Lucid) I booted into a black screen but knew the workaround was to enable mode setting through grub. I used the

```
i915.modeset=1
```

and added it to /etc/default/grub line GRUB_CMDLINE_LINUX, just after "quite splash", just as the workaround suggests.  I kept getting the "not found" when I ran update-grub and it would never work.  So, I thought, what the heck, I'll just add it directly to /boot/grub/grub.cfg kernel line, just like the old days in Grub Legacy.  In this way, it WORKED.  I could now boot the machine (though it still crashes on rare occassions).

My question is:  Why did the editing of the GRUB_CMDLINE_LINUX NOT work, and editing the grub.cfg directly DID work?  What is the reason for not being allowed to edit the grub.cfg directly?

---

### Post by Leppie on 2010-06-06
not sure how you edited the grub defaults file, but the line should look something like this:
```
GRUB_CMDLINE_LINUX="quiet splash i915.modeset=1"
```this seems to cause some confusion at times.

> **bobnutfield said:**
> What is the reason for not being allowed to  edit the grub.cfg directly?
the same message shows in grub legacy's menu.lst.
in grub2 it's more that it doesn't make any sense to directly edit the grub.cfg, as whenever update-grub is run those amendments will be lost (as the configuration scripts are not aware of manual amendments made to grub.cfg).

---

### Post by bobnutfield on 2010-06-06
Thank you, that may be why my original try netted "not found".  I used two separate entries "quiet splash" and "i915.modeset=1".  But, in any case, if it had worked it would have simply added the entry to end of the kernel line in grub.cfg just like I did anyway.  What is wrong with by-passing /default/grub and editing the .cfg file directly.  Updating grub is not necessary with direct editing, either.  It sort of acted like grub legacy used to.

---

### Post by bildr on 2010-06-06
he means whenever a kernel update is install, grub will regenerate its configs automatically.  the way you did it, every time a kernel update is installed, you config will bork and you'll have to edit again.  change it as recommended or deal with updates breaking your stuff.

---

### Post by bobnutfield on 2010-06-06
That explains it.  Thank you.

---

### Post by Leppie on 2010-06-06
another way is using the GRUB_CMDLINE_LINUX_DEFAULT parameter:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
```

---

### Post by bobnutfield on 2010-06-06
> **Leppie said:**
> another way is using the GRUB_CMDLINE_LINUX_DEFAULT parameter:
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
```

Thank you, that is good to know.  I went back and deleted my edit of grub.cfg, used your suggested entry in etc/default/grub and all is good.  Got to the same end and will now not have to re-edit on kernel updates.

On a side note, I will be glad when they sort this Intel graphics thing.  Many of my old laptops have Intel graphics, and many of the friends I assist with Linux also have it.  It is really putting them off of Linux and one has already gone back to Windows after using Ubuntu for a year...

---

### Post by Leppie on 2010-06-06
i didn't have any issues with intel graphics under karmic. this is actually the reason why i still have karmic on my lappy.
you may want to try that on your friends' machines?

---

### Post by bobnutfield on 2010-06-06
Yes, he had Karmic and asked me to help him update to Lucid. I did so unaware of the regressions in Intel module.  Well, you know the rest.  He got frustrated with the time it took for me to study and find the work around.  His point was that there should not have to be any "workarounds".  He had grown to dislike Windows intensely so he tried Linux, at first with Jaunty a year ago.  All was well.  Then this.  But I have to say that Ubuntu is certainly not the only distro to suffer with this.  It actually goes all the back to the 2.6.29 kernel for really old graphics chips (like his).  As of the latest kernels only the workaround or the vesa driver will work.

---

### Post by Leppie on 2010-06-06
yes i know it's a pain. i like lucid as it really does boot up fast, however as stated before the issue with intel graphics keeps me from upgrading from karmic for the moment.

---

