---
title: "read only file system"
date: 2010-05-22
forum: General Help
---

### Post by nisargjhaveri on 2010-05-22
Hii all
I can't insert songs in my iPod nano.
There is an error occurs which says that it is a 'read only file system' in ubuntu

thanks

---

### Post by sanderd17 on 2010-05-22
Do you use rhythmbox to send music to your ipod?

---

### Post by OpSecShellshock on 2010-05-22
In my experience with such devices, you'll either need to change the permissions of the ipod, change the fstab to specify how it mounts, or run gtkpod with admin privileges.

---

### Post by bodhi.zazen on 2010-05-22
Moved to general help as this is not a security issue.

Also if the file system is corrupt it may be mounted ro . In that event you can try to check the file system (fsck) or sometimes you need to back up your data and re-format.

I am not as familiar with the ipod and apple often makes products to specifically malfunction with Linux, so I use alternate Linux compatible products.

---

### Post by jamesisin on 2010-05-22
Is your iPod a MacPod or a WinPod (ie, on what system was it initiated)?

---

### Post by nisargjhaveri on 2010-06-09
mine is winpod

---

### Post by jamesisin on 2010-06-15
That's good.  It needs to be WinPod for Ubuntu to write on it I believe.

Are there any other details you can provide which might be helpful?  Can you write to it using sudo/gksudo for instance?  Error messages?

(I'm traveling in France and won't be very good about responding.)

---

### Post by rmronimolic on 2010-06-15
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]I'm trying to get this job where I work from home. I had to download a CD and run it to make sure my computer was compatible with what they needed. When I run the CD, it just repeats "failed - Read only file system"[/FONT][/COLOR][/FONT][/COLOR]

---

