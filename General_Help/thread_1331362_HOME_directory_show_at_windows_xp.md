---
title: "HOME directory show at windows xp"
date: 2009-11-19
forum: General Help
---

### Post by voltage on 2009-11-19
hi,

I would like to doing some like, what ever file or shortcut that i have save at my current windows xp desktop and this desktop we name as [desktop A], then once again i log off or shutting down my current pc [desktop A] (those file or shortcut will completely sync. or copy to my ubuntu server.). After a while i try to logon my account at another pc name as [desktop B] (at the same network), so do I can get back my desktop by the same things as "desktop A" ?

if yes, shell i know what package do i need to install and what can i do ?

Thanks for Advice..good day.;)

---

### Post by Giblet5 on 2009-11-19
Windows desktop shortcuts are useless on Ubuntu.

They use a different file format and Windows shortcuts point to programs and objects that probably won't work under Ubuntu. Syncing the other way (Ubuntu -> Windows) is impossible. Syncing Ubuntu->Ubuntu is easy - use rsync.

---

### Post by voltage on 2009-11-19
> **Giblet5 said:**
> Windows desktop shortcuts are useless on Ubuntu.

They use a different file format and Windows shortcuts point to programs and objects that probably won't work under Ubuntu. Syncing the other way (Ubuntu -> Windows) is impossible. Syncing Ubuntu->Ubuntu is easy - use rsync.

ya, u r right. But what i need is, save windows xp desktop short cut and data into remote ubuntu home folder. then once again i login to diffrent pc which is running windows xp, then i can simply access my destop shoirt cut and data.

---

### Post by voltage on 2009-11-19
hello, do some one can tell me what package that i need to install ? pls .. :-&

---

### Post by dcstar on 2009-11-19
> **voltage said:**
> hi,

I would like to doing some like, what ever file or shortcut that i have save at my current windows xp desktop and this desktop we name as [desktop A], then once again i log off or shutting down my current pc [desktop A] (those file or shortcut will completely sync. or copy to my ubuntu server.). After a while i try to logon my account at another pc name as [desktop B] (at the same network), so do I can get back my desktop by the same things as "desktop A" ?

if yes, shell i know what package do i need to install and what can i do ?

Thanks for Advice..good day.;)

This is called Roaming Profiles:

[http://wiki.samba.org/index.php/Samba_&_Windows_Profiles](http://wiki.samba.org/index.php/Samba_&_Windows_Profiles)

---

