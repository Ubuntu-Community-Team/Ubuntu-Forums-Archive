---
title: "Boot freezes after update to new kernel"
date: 2010-07-01
forum: General Help
---

### Post by Bobulous on 2010-07-01
I've just updated (through Update Manager) to the latest Linux kernel, (2.6.32-23, I believe) and now Ubuntu will not boot to the desktop.

It gets as far as finishing fsck on all of the drives, and successfully completes checks if necessary, but after that it just comes to a halt and won't proceed any further.

The last messages on screen when it freezes are (ignoring the fsck success reports):

init: ureadahead-other main process (954) terminated with status 4
init: ureadahead-other main process (959) terminated with status 4
init: ureadahead-other main process (970) terminated with status 4

These messages were appearing before, though.

The only way I seem to be able to boot now is by selecting the previous kernel (2.6.32-22) in GRUB.

Is anyone else seeing this, and does anyone know how to fix this Ubuntu update problem?

---

### Post by Bobulous on 2010-07-01
No one else is seeing this problem after the kernel update?

---

### Post by koushik.ms on 2010-07-02
I faced (what I think is a) similar issue to this. I upgraded to 2.6.32-23 on a (DELL D620) laptop yesterday and have been working with it for 24h+.

Once after bootup I logged in and out and before I could login again the GDM login screen just froze. No response to keys/ mouse (Caps Lock etc dead, Ctrl+Alt+F1-6 won't work) - only way out was to "long-press" the power off button.

Doing the same steps again didn't recreate the problem.

HTH

---

### Post by Bobulous on 2010-07-02
If I try to boot from the 23 kernel, it comes to a pause every time.

So I'm stuck with booting the 22 kernel from now on. Hopefully the 24 kernel will fix the problem, though I won't be shocked if it doesn't. Since the 10.04 release of Ubuntu, unshakeable problems have become common.

---

### Post by mike55 on 2010-07-05
Just wanted to say, I'm having the same problem here. After applying latest updates, the system rebooted and went through fsck to completion, but then hung. Reboot with hard power off results in hang at same place. Not seeing an error message on mine though. Will boot previous kernel as well until I have some more time to look at it.

---

### Post by Bobulous on 2010-07-05
I'm not sure the error I posted is directly related to the failure to boot. (I see the same messages even when successfully booting using the 22 kernel.)

Note that if you install "StartUp-Manager" you can specify which kernel to default to in the GRUB menu. That will at least make the problem less of a pain in the ***, but it's still a problem, and seemingly there aren't many people experiencing it. So I'm guessing that a fix is not going to arrive anytime soon.

Ubuntu 10.04 has proved such a mess (for me, at least) that I'm wondering whether Fedora handles updates more smoothly. (Probably a case of "grass is always greener on the other side", but I might give Fedora a chance if anything else goes wrong with 10.04.)

---

### Post by Bobulous on 2010-07-26
I've just applied the latest kernel (.24) and the problem remains.

Still no idea why boot comes to a dead stop since the .23 kernel. Answers on a postcard.

---

### Post by Bobulous on 2010-08-14
Think I've fixed it.

After finding this page:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I realised that new users of Ubuntu 9.10 and later are being setup with GRUB 2, while users who have upgraded from 9.04 and earlier are left with GRUB. Thinking this might shed light on the boot problem with newer kernels, I upgraded to GRUB 2 using the helpful instructions on the page linked above.

Once using GRUB 2, the Ubuntu splash screen miraculously started to display properly again, and the boot halted in its usual place. But this time I could read a garbled message that said something like "Wait for mounting, or press S to skip, or R for recovery." I pressed S to skip and then found that I couldn't login to GNOME because my /home directory was not mounted.

So it turned out to be a problem with mdadm (which sets up the RAID volume on which my home directory relies). I found that /dev/md0 was mounted, but /dev/md1 was not.

To fix this, I simply added a DEVICE and ARRAY lines to my mdadm.conf file, explicitly defining the partitions that make up my /dev/md1 RAID volume.

Now it seems I can boot successfully using the latest kernel (...24). I don't know why the newest kernels have stopped mdadm successfully detecting RAID partitions automatically, but I do wish that this sort of scenario was detected by Canonical when they were testing the 10.x version of Ubuntu.

---

### Post by mortenr on 2010-08-15
I'm experiencing this right now but none of the fixes so far have made any headway. Seems like mdadm is a POS software that should be avoided like the plague. This is the third time mdadm bricks my machine this year. Next time I'm off back to Windows-land. So far I've wasted so much time trying to get FOSS to work for me that I might as well have bought gold-plated Windows and Office licenses. Not even ME was this fickle...

---

