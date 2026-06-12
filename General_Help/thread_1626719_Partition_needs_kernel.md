---
title: "Partition needs kernel"
date: 2010-11-20
forum: General Help
---

### Post by haoleboy on 2010-11-20
After installing Ubuntu 10.10, before it boots into the OS, I have options I can boot to:

Ubuntu with Linux 2.6 35.22 Generic
Ubuntu with Linux 2.6 35.22 (Recovery mode)
Memory Test
Memory Test
????D?3??y?3u?c?5zB?h??z8 (on/dev/5db2)

When I boot to the last line, it shows that I have to run a kernel first. 
My question is this..... Can I eliminate this partition safely so it does not show up? Do I use Parted Magic or can I use G4L?  Or do I just say to the heck with it and write zeros to the drive, and reinstall Ubuntu?

Thank you very much.

---

### Post by coffeecat on 2010-11-20
> **haoleboy said:**
> Or do I just say to the heck with it and write zeros to the drive, and reinstall Ubuntu?

Whoa! Slow down! :)

When you select the first option, does it boot into Ubuntu OK? If so, you have a perfectly good Ubuntu installation, just a bizarre fifth choice in the grub menu.

If you can boot OK, do so, and then go to this page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the bootscript and post the RESULTS.txt file in code tags as explained in the link. That will tell us your partition layout and why grub is showing that peculiar option.

By the way - you do not need to zero out a drive before reinstalling. That routine dates back more than 15 years and belongs there.

---

### Post by haoleboy on 2010-11-20
I don't understand where I find these code tags in the forum....

---

### Post by coffeecat on 2010-11-20
Highlight the output of RESULTS.txt and click on the # icon which you'll see in the toolbar just above the message field.

---

### Post by oldfred on 2010-11-20
When you are posting a message the panel above has all the editing icons. On the right side is # or code tags. Hover with mouse over the icons to know what they are.

---

### Post by haoleboy on 2010-11-20
Not ever done this before, but it looks like iu did it under Google.....I hope it comes through

---

### Post by coffeecat on 2010-11-21
> **haoleboy said:**
> Not ever done this before, but it looks like iu did it under Google.....I hope it comes through

I don't know what this means. You need to post the RESULTS.txt in this thread.

---

### Post by haoleboy on 2010-11-22
My problem has been solved. Got it squared away, and thank you very much for your time and efforts.

---

