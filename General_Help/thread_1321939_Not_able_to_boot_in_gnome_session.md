---
title: "Not able to boot in gnome session"
date: 2009-11-10
forum: General Help
---

### Post by Erazer on 2009-11-10
Hi friends,

I tried something new this time and got into a bit of a trouble. What I did is as follows :

I converted my ext2 file system to ext3 using "tune2fs" command after booting from the live CD. Now the problem is that after system restart My gnome session is gone from the sessions menu in login window. 

Kindly tell me how I can get my gnome session back. 

I don't want to reinstall the whole thing as I have downloaded my mails in Thunderbird and I don't want to loose them.

---

### Post by MichealH on 2009-11-10
can you at the login window CTRL-ALT-F1 and type 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by Erazer on 2009-11-11
Hi Micheal, 
 
Sorry bro your solution didn't work.

---

