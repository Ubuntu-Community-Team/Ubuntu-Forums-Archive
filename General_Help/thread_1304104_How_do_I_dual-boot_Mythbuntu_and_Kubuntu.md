---
title: "How do I dual-boot Mythbuntu and Kubuntu?"
date: 2009-10-28
forum: General Help
---

### Post by MountainX on 2009-10-28
I want to install mythbuntu first, then install Kubuntu to another partition and be able to boot both of them. How can I do that?

My current setup is that I'm running sidux in a partition and sidux uses grub to boot. I have lots of free (unpartitioned) disk space for mythbuntu and kubuntu.

Here's the issue. When installing mythbuntu, the installer says no other operating systems are on the computer. In fact, sidux already exists. I want to leave sidux and add mythbuntu and kubuntu. I am concerned that since the mythbuntu installer doesn't see sidux, after this install sidux will no longer be a boot option.

I seem to remember that mythbuntu uses lilo, whereas sidux and kubuntu use grub. I guess that's going to be a problem...

---

### Post by RedSingularity on 2009-10-28
Have you tried using kubuntu to do the reformatting?  

If all else fails why not use the partition editor from a live CD to make some partitions and give them specific names for each OS you put on.

---

### Post by ranch hand on 2009-10-28
I would use gparted on your LiveCD to format your drive before you install.  This way your will know exactly what partitions you want each OS on.

I would install Myth after your sidux and then Kubuntu last.  Kubuntu will then be what you are booting from and it should see all your installs.

I find it strange that Myth would not use grub.  Are you sure about that?  I have seen some distros that give you the choice of grub our lilo.

You should be able to set sidux as your default boot in Kubuntu easily enough or simply reset sidux as your boot/root.

---

### Post by MountainX on 2009-10-28
> **Shadow121 said:**
> Have you tried using kubuntu to do the reformatting?  

If all else fails why not use the partition editor from a live CD to make some partitions and give them specific names for each OS you put on.

partitions and reformatting are not the issues. The issue is the boot loader (grub or lilo). I can't seem to find if mythbuntu uses grub or lilo. That's the first question. The second question is, if it uses lilo, how do I tell mythbuntu to use grub instead?

---

### Post by MountainX on 2009-10-28
> **ranch hand said:**
> 
I find it strange that Myth would not use grub.  Are you sure about that?  I have seen some distros that give you the choice of grub our lilo.


No, I'm not sure. When I installed mythbuntu a couple years ago, it used lilo. That may have changed now. The installer did not give me a choice - so I'm stuck half way through the installer until I find out more. Google has not helped (yet).

---

### Post by MountainX on 2009-10-29
I think I have it solved now. 
There is an advanced option at the end of the Mythbuntu install. In there I chose to install the boot loader to the partition where I put Mythbuntu (sda3) rather than sda.

Then in the existing grub in the MBR, I added this to the menu.lst:

```
Title Mythbuntu partition in sda3
Root (hd0,2)
Chainloader +1
```

I think this will work...

---

