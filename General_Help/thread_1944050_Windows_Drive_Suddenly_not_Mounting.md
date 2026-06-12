---
title: "Windows Drive Suddenly not Mounting"
date: 2012-03-20
forum: General Help
---

### Post by HenryL on 2012-03-20
Hello,

I am running Ubuntu 11.10 and also Windows Vista. I only use Windows occasionally, although I find it handy to be able to access the Windows drive from Ubuntu.

This morning however the Windows drive is not visible while I am in Ubuntu. I opened GParted and it showed an error exclamation for the Windows drive. I selected Information from the right click and it presented a pop up with an endless stream of code that ran off the screen and was not scrollable. It was also not selectable so I cannot copy and paste it here. I have attached a screen shot.

I then logged into Windows which worked fine. However when copying a few files from the windows drive onto an external drive I found that it seemed to be limited in how much data it could copy at once. I don't know if this is related or not.

To my knowledge nothing unusual has happened that could cause this. But I am not anything like technical enough to be willing to try to excavate into the problem. 

Any assistance as to the possible cause - and even better, solution - would be appreciated.

Thanks

Henry

---

### Post by TeoBigusGeekus on 2012-03-20
Run a "Check Disk (and fix errors)" from Vista on the partition and see if the problem persists.

EDIT: Getting too old lisati?

---

### Post by lisati on 2012-03-20
The first thing I'd suggest is to run CHKDSK from within Windows.

---

### Post by Mark Phelps on 2012-03-21
CHKDSK can be hard to find in Vista ...

To run it, you can do the following:
1) Click in the Start area
2) Select My Computer -- should bring up a list of "drives" (what MS calls partitions)
3) Right-click on the "drive" and select properties
4) Once there, select the option to scan for errors

I think you might be able to enter "check disk" in the start area and get there as well ...

---

