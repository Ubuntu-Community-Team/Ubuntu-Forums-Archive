---
title: "Old issue, thought 10.10 would correct it, now it's back."
date: 2011-03-29
forum: General Help
---

### Post by GratefulDean on 2011-03-29
When my laptop was solely encumbered by Windows 7 it took to getting stuck on the HP page, with the "Press Esc key for startup menu" in the lower left corner.  It would remain there for upwards of 10 minutes during which time I would often ctrl-alt-del myself into a crippling frenzy.  This was one of the issues that caused me to finally look into Ubuntu in earnest. 

So I now happily dual boot, not really bothering to visit the Windows side at all, and have lived free of this problem until today.

My understanding is that the Grub is the boot loader responsible for giving me the option to boot windows or Linux, if Windows is decided then the windows boot loader takes over and if Ubuntu is chosen then the Grub continues on to boot Ubuntu.  I am very green so I could very well have cobbled together what I've read into a poor conclusion. 

So my thought was that the Grub installation with 10.10 would correct this boot issue but now I'm concerned that something more insidious is at work.  

What are my first steps to figure out what the problem is then what can I do to correct it before I loose the ability to boot altogether?  This is my only machine and I am in no position to replace it anytime soon.

Thanks for any advice you can offer, 
Dean

---

### Post by tredegar on 2011-03-29
> So I now happily dual boot, not really bothering to visit the Windows side at all, and have lived free of this problem until today.

> So my thought was that the Grub installation with 10.10 would correct this boot issue

What is this "problem" or "boot issue"?

Please re-read your post.
You have not told us what your problem is, so we cannot help.

---

### Post by GratefulDean on 2011-03-29
> **GratefulDean said:**
> When my laptop was solely encumbered by Windows 7[COLOR="Red"] it took to getting stuck on the HP page, with the "Press Esc key for startup menu" in the lower left corner.  It would remain there for upwards of 10 minutes[/COLOR] during which time I would often ctrl-alt-del myself into a crippling frenzy.  This was one of the issues that caused me to finally look into Ubuntu in earnest. 
Dean

I should have been clearer. The, what I call, HP page comes up before the OS boots up.  It is getting stuck there again.

Sorry for the confusion,
Dean

---

### Post by lithopsian on 2011-03-29
The "HP page" would be part of your BIOS.  Check the settings to be sure you haven't set something in there.

The BIOS is responsible for deciding which device you are going to boot from.  It will churn through in an order that you can configure until it finds something workable.  Check you don't have a CD or USB stick inserted and configured before your hard drive.

---

