---
title: "Copy and Paste does not work much of the time"
date: 2010-03-07
forum: General Help
---

### Post by jereece on 2010-03-07
In Ubuntu, why does copy and past not work for most applications.  I can't tell you how many times I have copied some text and went to a new application and Past is greyed out.  For example, in Firefox I can highlight some text like "Belmont Diner", then right click and choose "Copy".  Then go up to the Google search bar and right click and Paste is not an option.  I have tried doing this using Crtl C to copy and Ctrl V to paste.  It does not work...most of the time.  Every once in a while it will but most of the time it does not.  I can repeat the action to make sure I really copied the data and still no luck. Sometimes it works but many times it does not.

Any suggestions?

Thanks,
Jim

---

### Post by 2hot6ft2 on 2010-03-07
I've had a similar problem the last couple days. One suggestion is to install glipper. I'm going to reinstall it to see if it will fix the issue. Edit: Seems to be working again.
In a terminal
Applications > Accessories > Terminal
```
sudo apt-get install glipper
```
Or search for it in Synaptic.

It will let you copy something to the clipboard and even if you close the place you copied it from (like a text file) you can still paste it where you want it.

---

### Post by asmoore82 on 2010-03-07
[SIZE="5"]+1[/SIZE] for glipper

I don't know how I lived without it for so many years.

---

### Post by JEREMIAHBARLOW on 2010-05-19
You are my hero!  

Why, OH WHY did they write the clipboard to forget when closing an application?

This is a must have for a Clipboard fix.  Cut, Copy, Paste the way it should be.

Thank You for glipper

---

### Post by jereece on 2010-05-20
Installed glipper.  Much better but I wish when you press Print Screen the popup box would not appear and you have to press copy to clipboard.

Thanks,
Jim

---

