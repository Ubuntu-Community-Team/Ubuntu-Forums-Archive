---
title: "USB HDD: Can unmount but not safely remove?"
date: 2011-04-15
forum: General Help
---

### Post by csh on 2011-04-15
If my question does not suit in this section, forum administrator / moderator please move it.

I purchased a new USB 3.0 HDD. It only consist of 1 partition which is FAT32. I can unmount the drive by using command "sudo umount /dev/sdb1" command. But, when I try to safety remove it by right clicking on the drive in "Computer" and then click "Safely remove drive", an error was occurred. Kindly please refer to the attached screenshot.


For more info:
HDD USB version: USB 3.0
Laptop USB version supported: only up to USB 2.0
Ubuntu version: 10.10 32 bit

---

### Post by sanderj on 2011-04-15
Did you Google it?

http://www.google.com/q="synchronize+cache%3A+failed"+"stop+unit%3A+failed"

Seems like a known bug:

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194)
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575)

I see no solution, but two work arounds ...

---

### Post by csh on 2011-04-15
> **sanderj said:**
> Did you Google it?

http://www.google.com/q="synchronize+cache%3A+failed"+"stop+unit%3A+failed"

Seems like a known bug:

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194)
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575)

I see no solution, but two work arounds ...

Yes. I did google, but found no solution. That's why this thread has been created.

---

### Post by sanderj on 2011-04-15
> **csh said:**
> Yes. I did google, but found no solution. That's why this thread has been created.

IMHO it's then better to mention what you've done and found. That avoids that others do the same.

---

### Post by csh on 2011-04-15
> **sanderj said:**
> IMHO it's then better to mention what you've done and found. That avoids that others do the same.

I didn't do anything. It is a new HDD that purchased yesterday. I did copy some files but only when using Windows. I never copy any files into it when using Ubuntu. In Windows, "Safely remove hardware" works very well on the drive.

---

### Post by sanderj on 2011-04-15
> **csh said:**
> I didn't do anything.
<snip>


What I meant is this: I googled it for you, which gave two bug reports and at least two workarounds, and after that you said "Yes. I did google, but found no solution.". It's more useful so say in your first post what you've done and tried yourself, and pointing to the things (like bug reports + workarounds) you've already found yourself.

Anyway: how about the workarounds? Or how about joining the bug reports?

---

