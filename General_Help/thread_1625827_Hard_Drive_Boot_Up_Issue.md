---
title: "Hard Drive Boot Up Issue"
date: 2010-11-19
forum: General Help
---

### Post by TheMixtureMedia on 2010-11-19
Hey there here is what I did when I installed Ubuntu 10.10 I installed it with three hard drives. Then today I took one of the drives out because it was almost done. When I rebooted it said that the drive failed to book and I could skip the boot find or try to trouble shoot it. I am not putting that drive back in and Ubuntu still boots up. The problem is everytime I restart it comes up with that issue. Does anyone know how I can edit Ubuntu 10.10 to forget that the drive was even on there. So when the system boots up it just boots up normally??

---

### Post by oldfred on 2010-11-19
With drive plugged in post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by TheMixtureMedia on 2010-11-19
Hi there the drive does not want to boot up now I think the controller does not work in the drive anymore. Is there anything else I can do??

---

### Post by efflandt on 2010-11-19
Is it your BIOS, grub, or Ubuntu complaining about your missing drive.  You might go into CMOS setup (from the BIOS splash screen) and make sure that it is not trying to boot from the missing drive.  But apparently you have grub on an existing drive if Ubuntu still boots.  So run the bootinfo script without the broken drive connected just to see how things are configured without the missing drive.

Check your /etc/fstab to see if it is still trying to mount something from the missing drive.  Then assuming things look proper from the bootinfo script RESULTS.txt, run **sudo update-grub** to update grub menu in case it listed something to boot on the missing drive.

---

