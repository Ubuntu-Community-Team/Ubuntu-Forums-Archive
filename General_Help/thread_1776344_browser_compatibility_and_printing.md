---
title: "browser compatibility and printing"
date: 2011-06-06
forum: General Help
---

### Post by Ditchdoc7893 on 2011-06-06
I'm sure this may sound dumb, but I have a question regarding browser compatibility and printing.  I like to print coupons and when I tried to do this through either Firefox 4.0 or Chromium, it says I have to be running either a MS Windows 2K or newer or Mac OS X.  The site I print from is coupons.com.  Does anyone have any advice for getting these to print using either Firefox or Chromium, or any other browser for that matter?

---

### Post by linuxinstalledfromhdd on 2011-06-06
Install PlayOnLinux. And install Internet Explorer.  Then you can use screen capture to take a snapshot of whatever coupon you have up, and then print that instead. You may need to add more browser components (like support for ActiveX scripts etc) in PlayOnLinux. That might work. It would easy to test out too.

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

---

### Post by lovinglinux on 2011-06-06
I wouldn't bother with Internet Explorer. I tried to install it via PlayOnLinux and it didn't even install properly. 

I also tried to install Firefox for Windows via Wine, which is supported by the coupon site. It install properly, however when you click to print the coupons, it asks to download their coupon printer executable. When you execute it, it adds two plugins to Firefox. However, it didn't work when  actually trying to print.

I also tried to use the native Firefox with User Agent Switcher, but the problem is the printer executable that you need to install, so it doesn't work this way.

You might be able to use Firefox for Windows via Wine, if you manage to install the printer executable properly, but unfortunately, I don't have a simple guide to do that.

Perhaps, would be easier to install Windows on a virtual machine to print your coupons.

---

### Post by wildmanne39 on 2011-06-06
Hi, the idea of a virtual machine like in virtualbox that lovinglinux suggested is probably the only way. I was going to say one of the other methods but he already said that will not work, I personally use windows inside of virtualbox for any windows programs that I have to run, but it is not very often.

---

### Post by Ditchdoc7893 on 2011-06-06
So I think I have it figured out.  Virtualbox works really well for this particular type of thing.  In doing the install of XP to Virtualbox, I think I truly realized how much I despise Microsoft.  I had to call just to activate it (and believe me, I let them have it about that) because I've had to reinstall their piece of sh!7 OS so many times.  They got an ear full let me tell you.  Anyway, this works really well for anyone else who wishes to coupon and run Ubuntu.

---

### Post by wildmanne39 on 2011-06-06
> **Ditchdoc7893 said:**
> So I think I have it figured out.  Virtualbox works really well for this particular type of thing.  In doing the install of XP to Virtualbox, I think I truly realized how much I despise Microsoft.  I had to call just to activate it (and believe me, I let them have it about that) because I've had to reinstall their piece of sh!7 OS so many times.  They got an ear full let me tell you.  Anyway, this works really well for anyone else who wishes to coupon and run Ubuntu.
Hi, that's good, I am glad you are happy. Read up on the things that you can do with virtualbox, that way if you need to redo xp you will know how to simply use a saved backup of xp to restore it only takes a few seconds, they are called snapshots. would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

