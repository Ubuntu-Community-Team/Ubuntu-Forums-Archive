---
title: "Windows runs CHKDSK after deleting Ubuntu partition(Dual boot mode)"
date: 2010-09-18
forum: General Help
---

### Post by Stan_1936 on 2010-09-18
I installed Windows XP and then Ubuntu 9.10...so they're being dual booted.  I then upgraded to 10.04 by doing the following:

1. When asked, from Ubuntu Live CD, how I wanted to partition the HDD, I selected Manual.
2. I completely deleted the ext4 / partition and the swap partition, so I had an NTFS partition(XP) and empty space.
3. I created a new ext4 / partition and a new swap partition
4. Ubuntu was installed using the 2 partitions created in step 3.

After restarting the PC and choosing Windows from the bootloader, Windows ran CHKDSK because it said that it had to verify "one of your disks for consistency".

The CHKDSK ran and found no problems.

The CHKDSK message was quite discoforting to me because I didn't think the XP partition would be affected....I never touched it.

QUESTION:
Is this CHKDSK message normal or is it an indication of a problem?

---

### Post by wilee-nilee on 2010-09-18
> **Stan_1936 said:**
> I installed Windows XP and then Ubuntu 9.10...so they're being dual booted.  I then upgraded to 10.04 by doing the following:

1. When asked, from Ubuntu Live CD, how I wanted to partition the HDD, I selected Manual.
2. I completely deleted the ext4 / partition and the swap partition, so I had an NTFS partition(XP) and empty space.
3. I created a new ext4 / partition and a new swap partition
4. Ubuntu was installed using the 2 partitions created in step 3.

After restarting the PC and choosing Windows from the bootloader, Windows ran CHKDSK because it said that it had to verify "one of your disks for consistency".

The CHKDSK ran and found no problems.

The CHKDSK message was quite discoforting to me because I didn't think the XP partition would be affected....I never touched it.

QUESTION:
Is this CHKDSK message normal or is it an indication of a problem?

I suspect XP needed a chkdsk already, a chkdsk of some sort should be run every so often anyway. In Ubuntu every 30 reboots it runs a fdisk the Linux equivalent.

Hard to say what happened, you were the one there and you would know if you had kept XP setup correctly.

The one thing that can happen though with gparted and other partition managers is that you want to run each operation individually, if you delete a partition and then have it create another all in one swoop; I have had this create not quite what I wanted.

---

### Post by Stan_1936 on 2010-09-18
Yeah, XP was working fine and was setup correctly.

You're right though......I deleted and installed everything in one step.  I just remembered having read what you said about not doing this.....

I wonder if this could be the explanation.

---

### Post by wilee-nilee on 2010-09-18
> **Stan_1936 said:**
> Yeah, XP was working fine and was setup correctly.

You're right though......I deleted and installed everything in one step.  I just remembered having read what you said about not doing this.....

I wonder if this could be the explanation.

It is hard to say, even if you have XP defragged no virus...etc it could still need a a chkdsk just to make itself happy, and we all want a happy XP eh.;)

The good thing here is that it seems you knew how to reload the mbr if you needed to, so now get to helping the rest of us.:-\"

---

### Post by Stan_1936 on 2010-09-18
^^^That is EXACTLY what I wanted to/want to avoid.  I had tried it once without success and so never dual booted, out of fear that I would lose the ability to boot into XP.

Anyways, the bootloader appears to have stayed intact OR the magical "install Ubuntu after Windows" seems to have done its thing.

---

### Post by wilee-nilee on 2010-09-18
> **Stan_1936 said:**
> ^^^That is EXACTLY what I wanted to/want to avoid.  I had tried it once without success and so never dual booted, out of fear that I would lose the ability to boot into XP.

Anyways, the bootloader appears to have stayed intact OR the magical "install Ubuntu after Windows" seems to have done its thing.

Sounds like your set. Reloading the mbr is easy once you now how to do it. Just ask if you want any information about this area. Once you know how to do this it is quite, the release, if you have a general understanding of bootloaders, you can remove and install totally in control once again generally.

Generally the OS take over the boot as they are installed consecutively, but this can be tweaked in certain situations, at least with Linux, probably with MS to if you know how.

---

### Post by lisati on 2010-09-18
What I'd be looking for is to see if XP runs CHKDSK *every* time you boot - if it doesn't you'll probably be OK.

---

### Post by Stan_1936 on 2010-09-18
nope, I've restarted XP a numberof times since then and CHKDSK never came up after that.

---

### Post by Jesus_Valdez on 2010-09-18
So, no problems?

A happy Ubuntu costumer.

---

