---
title: "Change Grub2 boot option names?"
date: 2009-12-06
forum: General Help
---

### Post by Altay_H on 2009-12-06
Ever since installing grub2 my boot loader seems more more limited. I'm setting up my mother's computer to dual-boot XP and Ubuntu and I want to clean up the boot loader so that it won't be confusing to her. I've been able to clean it up somewhat by removing the memory test options, but I'd like to rename the boot options because one of the non-Ubuntu OS options is very poorly named.

The HP recovery option that restores the computer to factory default settings is named "Windows NT/2000/XP (on /dev/sda2)" which tells absolutely nothing about what it does. I'd like to rename it to something significantly more descriptive like "Restore to factory default (erase all data)" to make sure she doesn't get it confused with the XP boot option. What's the proper way to do this in Grub2?

I looked over the [Grub2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275") and it tells how to add new options, how to remove existing options, and how to create the menu manually, but it doesn't cover how to rename existing options. Is the best way to go about this to create a totally customized menu? Thanks for the help with getting used to the new version of grub!

---

### Post by ranch hand on 2009-12-06
You need to look at a custom menu in /etc/grub.d/40_custom.

Build your menu, with the labels you want between the "  ".  When you save the file save it as 06_custom and it will be at the top of your generated menu screen.

See link in my sig or drs305's great how to that you already have been to.

---

### Post by Altay_H on 2009-12-07
Thanks for the suggestion, but I actually [surprisingly] found a better solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1287602").

For my specific problem, it involved making the following change to /etc/grub.d/30_os-prober.
```

# Original
# if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
# fi

  if [ "${LONGNAME}" = "**[COLOR=Red]Windows NT/2000/XP (on /dev/sda2)[/COLOR]**" ] ; then
    LONGNAME="**[COLOR=DarkBlue]Restore to factory default (erase all data)[/COLOR]**"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

```

For anyone else having trouble modifying boot options in Grub2, I'd suggest checking out the [aforementioned thread]("http://ubuntuforums.org/showthread.php?t=1287602").

---

### Post by ranch hand on 2009-12-07
I misunderstood what it was you wanting to do.

I shuld have pointed you to drs305s thread.  It is a neat one anyway.

---

