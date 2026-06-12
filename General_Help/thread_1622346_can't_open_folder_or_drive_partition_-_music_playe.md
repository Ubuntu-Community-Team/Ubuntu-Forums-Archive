---
title: "can't open folder or drive partition - music player loads instead of nautilius"
date: 2010-11-15
forum: General Help
---

### Post by petex on 2010-11-15
As stated in the subject when i click on partition in Places or try to open a folder e.g. by selecting open containing folder in transmission the system will load music player instead of nautlius. Is this some kind of problem with file asociations??

---

### Post by Verbeck on 2010-11-15
> **petex said:**
> Is this some kind of problem with file asociations??
yep. to fix it,

*create a folder on your desktop if you don't have one (right click>create folder)
*right click the folder and select open other other application
*select file browser from the list and make sure the 'remember this application for...' is checked. then click open

---

### Post by petex on 2010-11-15
strange i already did that and it did no good, now that I did it again it seams to work
still have to check if it will work after rebooting, but THX

---

### Post by ibbill on 2010-11-15
Had the same problem thanks for the fix. This just started is there something causing this.

Bill

---

### Post by mc4man on 2010-11-15
> is there something causing this.
There is and has been for some time and likely will continue 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

---

### Post by ibbill on 2010-11-15
> **mc4man said:**
> There is and has been for some time and likely will continue 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)
  Well hope they fix this never even looked at that check box ouch. Thanks for the heads up.

---

### Post by mc4man on 2010-11-15
> Well hope they fix this
There is [a bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833") that's considered upstream' problem, who knows if it will be fixed.
What I linked you to was an attempt to get ubuntu to mitigate the bug by makng the box inactive by default.

Either they don't 'get' that there is a difference, or don't care to address.
(keep in mind that it also affects files, though the affect isn't that bad

---

