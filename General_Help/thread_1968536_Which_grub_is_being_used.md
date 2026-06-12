---
title: "Which grub is being used?"
date: 2012-04-29
forum: General Help
---

### Post by OllieGab on 2012-04-29
I Installed Debian next to my Ubuntu 11.10 (and Mint) so I believe that made the Debian grub "take control" (?).
After updating Ubuntu to 12.04 the grub menu does look different, though it still has all the same entries.
Does this mean that it is now U12.04's grub that is being used again? Does an upgrade of an existing distro "take back control" if it was another grub used previously?

Cheers!

---

### Post by Dngrsone on 2012-04-29
Yes, Ubuntu 12.04 installed Grub 2 to your drive.

Considering Grub is common among all you distribtions, and I *believe* they all use Grub 2 now, the question is largely academic.

However, you could try opening a terminal in Debian and doing 

```

sudo update-grub

```

and see if that straightens things out.

Otherwise, you miight try reinstalling Grub from within Debian.

---

### Post by grahammechanical on 2012-04-29
You will find that the last Linux to be installed will put its Grub in the MBR.

The same applies to the last kernel to be updated as this always causes the command update-grub to be run.

As a OS upgrade often includes upgrades to the kernel, then yes, when you upgraded Ubuntu to 12.04 it installed its Grub into the MBR.

If I remember correctly, 11.10 use the 3.0 kernel and 12.04 uses 3.2 Linux kernel. So, yes, the upgrade to 12.04 changed which Grub was in MBR.

I only use Ubuntu but I have different versions of Ubuntu installed. I have Grub Customizer in what I think of as my main Ubuntu and I use Grub Customizer to put the Grub menu back as I like it.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I have absolutely no idea how well this utility would work if it was run in Debian or Mint.

Regards.

---

