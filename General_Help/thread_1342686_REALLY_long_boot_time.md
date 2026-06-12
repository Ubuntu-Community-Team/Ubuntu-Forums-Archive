---
title: "REALLY long boot time"
date: 2009-12-01
forum: General Help
---

### Post by j0zza on 2009-12-01
Hello all,

Just signed up to ubuntuforums to help me with this problem that i can not figure out since i installed ubuntu 9.10 about 3-4 weeks ago.

I have had this problem from the very first time on installing ubnutu.

When i boot up ubunutu i get the CPU start up screen then it just goes straight to a blank screen with the white dash (but i cant type anything)  it sits there for a bout 3-4 minutes then continues to boot like normal ubuntu would...???...

Any help would be great as it is really annoying for ubuntu to startup when i know ubuntu in normally a fast loader!

Thanks guys!

keep in mind im pretty much a n00b to Ubuntu!

j0zza

---

### Post by oldfred on 2009-12-01
Grub can be slow loading if you have multiple drives but worst case I have seen is 30-40 seconds. It is a known bug and the work around for that is to install grub on the same drive as the install and boot that drive.

If you only have one system grub bypasses the menu and directly loads Ubuntu. You can only see the menu if you hold down the shift key from the end of the BIOS boot.

You could try booting the recovery to see if it is also slow, but it will leave you at a command line, not loading the window manager. You can use startx to get gnome going.

You can check you boot log files and see if something is looping or takes a long time to load. A long time between tasks would indicate a problem and where to look. IN system administration is the log file viewer.

---

### Post by j0zza on 2009-12-01
OK thanks for the reply oldfred, but i do only have 1 driver. NO dual boots just straight ubuntu.

How do i boot into recovery?

I have looked at the boot log but theres so much there how am i aspose to find what i'm looking for :S

Thanks again.

j0zza

---

### Post by oldfred on 2009-12-01
In the boot log the first entry is the time. The times should have very small difference but if one is a large jump that would indicate it had a problem loading that line.

Hold down shift key while booting, should bring up the menu.

---

### Post by j0zza on 2009-12-02
i am guessing you are talking about the "bootstrap.log" file because in the "boot" log it says (nothing has been logged yet).


But in the "bootstrap.log" the first 3 lines is the following:
Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5.0.0ubuntu7_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk 		 	   		  

I don't know if this means anything but as i said in the "boot" log there is nothing there...

thanks for your help again!

j0zza

---

