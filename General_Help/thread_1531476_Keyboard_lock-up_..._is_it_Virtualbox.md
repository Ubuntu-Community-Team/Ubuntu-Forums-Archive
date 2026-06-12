---
title: "Keyboard lock-up ... is it Virtualbox ?"
date: 2010-07-15
forum: General Help
---

### Post by asearle on 2010-07-15
Hi everyone,

I am running Ubuntu 10.4 and using Virtualbox very intensively to develop under windows.  This is the perfect combination:  Virtualbox is excellent and gives great speed, functionality and connectability.

However, I keep getting a keyboard and mouse 'lock-up' and find that I have to power-down my PC in order to get things working again.  The strange thing here is that Ubuntu seems to continue working fine:  for example audio keeps playing and the system once successfully finished burning a CD even though keyboard and mouse were frozen.

This happens only very sporadically but is a serious problem because I can't have things freezing when I am in the middle of development or am demoing functionality to a client.

At first I thought it was Ubuntu but it only seems to happen when VirtualBox is running so I am wondering whether there is a problem with the keyboard and mouse capture for Virtualbox and that this is causing the problem.

I have de-installed and re-installed Virtualbox but this didn't help.

So does anyone have a idea how I could either fix this problem or how I could get the system to free the keyboard and mouse when I get a lock-up.

That would be a great help.

Many thanks,
Alan Searle

---

### Post by robsoles on 2010-07-15
I haven't experienced that, I find that if the Ubuntu screensaver runs and the VM had focus last then I have to click away from the VM and click back into it to get the keyboard to go in it again but otherwise I haven't had the problem you mention.

Have you installed the 'Guest Additions'?

---

### Post by jbrice on 2010-07-15
Are you seeing the result of a normal "as designed" feature of VirtualBox? By default, clicking on a V.Box session running in a window captures input, and if that guest session is busy/frozen, the whole PC seems to freeze. 

Just try hitting the right-hand "Ctrl" key as this releases the keyboard and mouse input back to the host session.

Once you have overcome this problem, the following may be of interest to you - an [online article on moving the big V.Box files off onto their own disk or partition]("http://www.jamesbrice.com/articles/35-pcs-and-software/48-move-vbox-working-folders").

---

### Post by robsoles on 2010-07-15
> **jbrice said:**
> ...

Once you have overcome this problem, the following may be of interest to you - an [ online article on moving the big V.Box files off onto their own disk or partition]("http://www.jamesbrice.com/articles/35-pcs-and-software/48-move-vbox-working-folders").

I read some of it - it isn't that big a value add if you are for instance using a raid mirror setup rather than backing up over the wire or other TCP/IP method. Your joomla theme looks awfully familiar!

---

### Post by asearle on 2010-07-15
Hi everyone,

Thanks for the feedback.

I have switched off 'auto-capture' in Virtualbox and will now check whether the right-hand crtl button will free a freeze-up.

Anyway, I'll give feedback on this in a few days.

Many thanks,
Alan

PS:  I do have Virtualbox extras installed.

---

### Post by robsoles on 2010-07-15
I've a feeling it probably won't. (ie, turning off auto-capture!)

Are you using virtualbox ose from the repository?

If so, go and have a poke around at [www.virtualbox.org]("http://www.virtualbox.org") and let me know if you need help transferring over to the closed source version you can get from that site.

If already using Oracle closed source version then please say so.

---

### Post by reiki on 2010-07-15
I have this issue when using VirtualBox to program my universal remote. Lately it is only the keyboard, but the mouse keeps working fine so I minimize the virtual machine, maximize it, and the keyboard is active again. I had assumed this was because of my wireless keyboard and mouse, both of which are using the same transceiver plugged into USB. 

I hadn't given it a lot of thought as I figured it was something quirky with my hardware setup.

---

### Post by asearle on 2010-07-16
Hi again,

My VirtualBox is OSE installed from the Ubuntu repository.

But things are confusing me even more:  I got a lock-up again when VirtualBox was running but no virtual machine was open.  I clicked right-Ctrl (the release key) but that didn't help.

So maybe it isn't VirtualBox at all?

This is really frustrating because I get a keyboard and mouse freeze-up one or two times a day at (as far as I can see) random times.  Is is Ubuntu?  Is it software?  Or maybe it's hardware*?

I wish I could find a way to diagnose this.

Any tips would be gratefully received.

Many thanks,
Alan

*:  I'll run a full memory scan tonight

---

### Post by robsoles on 2010-07-16
have you googled much over the problem? like

[http://www.google.com/search?q=virtualbox+ose+freezes+on+my+pc](http://www.google.com/search?q=virtualbox+ose+freezes+on+my+pc)

and search terms I'll leave to your imagination to come up with - although adding your motherboard's (short) ID string and other bits like video card and any other bits that seem prominent in your PC can be a help to finding more relevant results.

Did you look at [http://forums.virtualbox.org/](http://forums.virtualbox.org/) for people having similar problems? Did you check if it's a bug listed on launchpad for your hardware.


I would go and find where they explain how to get the Oracle closed source copy of virtualbox on [www.virtualbox.org](www.virtualbox.org) using apt-get method as opposed to download package method (because then you get automatic updates) - they may have fixed your issue since the version that Canonical are holding in their repository. You just uninstall OSE version and use apt-get to get the new one and your old VMs run just fine (don't have them 'saved' n stuff though!)

---

### Post by asearle on 2010-07-16
Many thanks for this tip and, yes, I have installed the official Oracle version.  It looks very good!

Anyway, I will monitor the situation and will give you feedback regarding freezing up ... or (hopefully) not freezing up  :-)

Many, many thanks for your help.

Regards,
Alan

---

### Post by robsoles on 2010-07-17
How's it going Alan? Can you mark this thread as solved or are you still getting freezes?

---

### Post by asearle on 2010-07-20
Yes, your recommendation worked:  I installed the official version of VirtualBox and now all of my keyboard-freezes have stopped (or at least I haven't had one for 3 days).

I am extremely relieved.  Many, many thanks for the tips!

This thread can certainly be marked as solved  :-)

Regards,
Alan

PS:  Maybe Ubuntu should update the version of VirtualBox OSE that they have on their server?

---

### Post by asearle on 2010-07-20
PS:  How do I mark a thread as solved?  Can I do that or is it done by admin?  I've been looking for a flagging option but can't see one.

---

### Post by robsoles on 2010-07-20
Look at the choices under 'thread tools' in red above.

---

### Post by asearle on 2010-09-08
Everything is fine now.  Yes, it was Virtualbox and installing the official Oracle version (with regular patching) solved the problem.

Many thanks for your help.

Rgds,
Alan

---

### Post by frogotronic on 2011-09-20
Can one play DukeNukemForever in VB?

---

### Post by robsoles on 2011-09-21
> **cement_head said:**
> Can one play DukeNukemForever in VB?

Not that worked for me previously but they have released a couple of (semi reasonable) patches since then.

---

