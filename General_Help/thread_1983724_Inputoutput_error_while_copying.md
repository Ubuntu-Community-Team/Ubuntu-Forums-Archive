---
title: "Input/output error while copying"
date: 2012-05-20
forum: General Help
---

### Post by aflyingturtle on 2012-05-20
So I'm trying to copy from a HFS+ formatted internal hard drive into an external HFS+ hard drive while running of an ubuntu livecd 12.04. I installed the hfsprogs using ```
sudo apt-get install hfsprogs
``` but if I try and copy or write anything to the external drive I get the error: ```
 Error creating directory: Input/output error 
``` Is there a way to stop getting this error?

---

### Post by dcstar on 2012-05-21
> **aflyingturtle said:**
> So I'm trying to copy from a HFS+ formatted internal hard drive into an external HFS+ hard drive while running of an ubuntu livecd 12.04. I installed the hfsprogs using ```
sudo apt-get install hfsprogs
``` but if I try and copy or write anything to the external drive I get the error: ```
 Error creating directory: Input/output error 
``` Is there a way to stop getting this error?

Did you remount the drive **after **you installed this other stuff?

---

