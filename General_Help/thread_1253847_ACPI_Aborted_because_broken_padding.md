---
title: "ACPI: Aborted because broken padding"
date: 2009-08-30
forum: General Help
---

### Post by Zilioum on 2009-08-30
When I started my pc today (Kernel 2.2.28-15) I got the following messages after: *Starting up*
[FONT="Courier New"]
0.093369 *(No idea if you need the numbers)* ACPI: Aborted because broken padding

1.625288 invalid compressed format (err=1)

1.634046 Kernel panic - not syncing: VFS: unable to mount root fs on unknown wp-block (0,0)[/FONT]

I don't remember doing anything special before I shutting it down yesterday, and this kernel worked perfectly for the last few days.

Lucky for me my older kernel (2.2.27-14) still works, but I get the 8.10 splash screen and not the 9.04 one. I also get quite a lot of freezes (Firefox and Amarok mainly) without any apparent reason and I've never had freezes before anyway.

Help would be very appreciated or at least somebody who could tell me what is happening here.:confused:

---

### Post by Kasperla on 2009-09-01
I had the same problem this morning. Older kernel is still working. Has anybody an idea?

---

### Post by Zilioum on 2009-09-03
Anybody?
> 
Older kernel is still working

Do you also have more system freezes, or does it work properly?

---

### Post by Zilioum on 2009-09-04
The new Kernel update fixed my problem, everything works again. 
But its weird, I had the same problem with 8.10.
First Kernel works, 2nd works for a bit and then suddenly doesn't work at all anymore. 3rd Kernel fixes the problem.

---

### Post by swiiney on 2009-09-10
Hi,

   I have just done a kernel upgrade yesterday and now I am stuck with the same error message!!! Unfortunately I don't have any other kernel available.

   I am going to try to restore using the install CD. Does any documentation exist somewhere to restore initramfs and kernel ?

Thanks

Regards
Stephane

---

### Post by swiiney on 2009-09-11
Solved my problem too.

My Ubuntu is installed in a virtual machine (virtualbox). To restore the installation:

[LIST]
[*]I re-installed ubuntu in another virtual machine
[*]Installed all the patches, particularly the kernel
[*]mount the virtual disk of the broken Linux onto the fresh one
[*]copied the files from the fresh /boot/ to the broken /boot/ (the one concerning the installed kernel System* init*, etc...)
[*]restarted the broken Linux : it works !!!
[*]re-installed the kernel packages to be sure all is correct into the initramfs.
[/LIST]

And it works now !

Regards
Stephane

---

