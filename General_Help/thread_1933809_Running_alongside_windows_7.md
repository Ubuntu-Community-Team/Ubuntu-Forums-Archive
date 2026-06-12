---
title: "Running alongside windows 7"
date: 2012-03-01
forum: General Help
---

### Post by abminto63 on 2012-03-01
I'm sure this has been posted before but I am a new member of Forum.    I have a laptop with windows 7 and tried Ubuntu running alongside.   It worked Ok to start but now on booting my laptop, I ger Error - no partition - Grub Rescue.
I thought I was reasonably PC literate but this found me out.   I have read posts with instructions I do not understand.   Can anyone tell me in beginners language h againow and where I insert info in Linux to allow me to access widows 7
abminto63

---

### Post by HeroOfCanton on 2012-03-01
You would need to edit your grub file, although it should have done that on install.

To clarify, are you only getting this error when trying to boot to windows, or is this all you get when you boot up?

---

### Post by Mark Phelps on 2012-03-01
We need to first confirm that you do NOT have a wubi installation.  So, did you install from inside Windows using Wubi, or did you create a new partition and install booting from the Ubuntu CD?

Also, do both OSs not start, or does only Ubuntu not start?

---

