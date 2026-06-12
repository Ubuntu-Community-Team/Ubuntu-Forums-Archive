---
title: "How to restore access to Thinkpad Rescue and Recovery partition?"
date: 2010-01-07
forum: General Help
---

### Post by john_brown_jr on 2010-01-07
Greetings,

I have a brand new Lenovo Thinkpad T400. Lenovo claims that it should boot into recovery mode if the blue 'ThinkVantage' button is pressed during boot. However, this does not happen after I have installed Ubuntu (Koala). First of all, nothing happens when I press the blue button, and no recovery partition is visible in GRUB boot menu. However, the partition itself is still there. The question is how to boot from it?

I found some tips from [http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery), however, they are for GRUB, but my Ubuntu comes with GRUB2. I tried to adapt their instructions to my case. I added this to /etc/grub.d/40_custom:

```
menuentry "Rescue and Recovery" {
        insmod ntfs
        set root=(hd0,3)
        parttool (hd0,3) hidden-
        parttool (hd0,3) boot+
        search --no-floppy --fs-uuid --set A0F7000BF6FFDF88
        chainloader +1
}

```

That, however results in message about bootmgr missing at startup. Does anyone have any ideas?

One option would be to start Windows and reinstall Windows MBR, but this would nuke my GRUB, and things could quickly go downhill from there as I am using full disc encryption for my Ubuntu partitions.

---

### Post by one30nav on 2010-01-25
Try this instead.  Found this awesome guidance from Michael-352 on the Nabble forums:

menuentry "Thinkpad Rescue and Recovery" {
        set root=(hd0,2)
        chainloader +1
}

This accesses the R&R with no further tweaking required.
My fat32 partition is sda2, hence th "2" above.  Hope this helps...

---

