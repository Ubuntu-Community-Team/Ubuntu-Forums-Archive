---
title: "I can no longer boot from my hard drive, did GRUB just die?"
date: 2010-09-01
forum: General Help
---

### Post by Frostshock on 2010-09-01
It's an Aspire 5741 but I don't think it's a laptop issue as it was literally working 12 hours ago. I booted into Windows 7 from GRUB, did a bit of stuff I needed Windows for, then shut down.

Ubuntu was installed from the 10.4.1 64-bit LiveCD, so it's GRUB2. Now when I boot from the hard drive I get absolutely nothing. It's just a blinking underscore on a black screen that goes on forever, with no input possible. It doesn't even give any hints that it's even trying to load GRUB or do anything.

I booted from the CD, which DID work, and checked my Windows and Ubuntu partitions, they were intact and I could access files on them so I don't think my hard drive crashed or anything of the sort. The GRUB files were also present, so I'm at a loss.

Should I try this?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

As long as it couldn't cause any harm I'm willing to try it. Failing that, my next plan is to replace GRUB with the Windows bootloader temporarily to see if that will boot.

Thanks in advance.

---

### Post by hangfire on 2010-09-01
> **Frostshock said:**
> It's an Aspire 5741 but I don't think it's a laptop issue as it was literally working 12 hours ago. I booted into Windows 7 from GRUB, did a bit of stuff I needed Windows for, then shut down.

Windows updates feels free to write to the block after the boot sector, destroying grub2's necessary information.

If you can reinstall grub2 from the liveCD you should be OK.

-HF

---

### Post by oldfred on 2010-09-01
The grub team is looking for issues like yours. Since it is windows software doing this they want to see if they can do a work around to avoid the issue but need details.

Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)

---

### Post by Frostshock on 2010-09-01
> **hangfire said:**
> Windows updates feels free to write to the block after the boot sector, destroying grub2's necessary information.

If you can reinstall grub2 from the liveCD you should be OK.

-HF

Cheers, everything is back to normal. Now I know what to do.

> **oldfred said:**
> The grub team is looking for issues like yours. Since it is windows software doing this they want to see if they can do a work around to avoid the issue but need details.

Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)

I'll take a look at those, and if it happens again I'll be sure to grab some logs before fixing the problem. All I did on Windows was install Pidgin to chat while I used some programs I had already installed before that didn't break GRUB.

---

