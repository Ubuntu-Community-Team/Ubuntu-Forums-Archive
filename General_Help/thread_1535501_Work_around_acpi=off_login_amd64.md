---
title: "Work around acpi=off login amd64"
date: 2010-07-21
forum: General Help
---

### Post by fearful on 2010-07-21
Is there a way around having to logon acpi=off with ubuntu 10.04 amd64 on Toshiba Satellite L505D-S5983. I also came around when I watch flash videos it says "An error has occurred please try again later" any ideas on these two issues?

---

### Post by dcstar on 2010-07-21
> **fearful said:**
> Is there a way around having to logon acpi=off with ubuntu 10.04 amd64 on Toshiba Satellite L505D-S5983. I also came around when I watch flash videos it says "An error has occurred please try again later" any ideas on these two issues?

Any Boot string can be added to the /etc/default/grub file.

As far as Flash goes, the 32-bit version with the 64-bit wrappers is pretty problematic. If you do a forum search you can probably find the older native 64-bit version and use that.

---

### Post by colinwhipple on 2010-07-21
Yes, look at this message thread:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---

### Post by locosway on 2010-12-05
Actually, turning off ACPI is not useful on a laptop since it disables so many features. Instead you may want to try:

pci=noacpi

This worked for my Dell M5010, which otherwise wouldn't boot unless I did turn off ACPI.

---

