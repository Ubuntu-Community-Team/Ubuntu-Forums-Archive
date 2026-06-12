---
title: "Strange problem in Xubuntu with Opera browser"
date: 2011-12-10
forum: General Help
---

### Post by M_Mynaardt on 2011-12-10
Hi!

I have had a strange problem with Opera lately.  I've been trying one Linux distro or another for a while and have settled on Xubuntu; largely because I'm partial to the Xfce DE.  But the strangest thing happened recently with two sites I've never had problems with before.  In both cases, when I selected these sites, they caused some, even all, of the menus in Opera to become rectangles, as if they're unrecognizable fonts.  I've never seen that before.  And if I opened the same sites in another browser (Firefox or Chromium), there was no such problem.

Does anyone know what would cause this?  And how to fix it?

The two websites this happend to me are:
     [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
     [http://elementaryos.org/](http://elementaryos.org/)

I've accessed these sites without incident in other distros other than Xubuntu; so I'm not sure if there's a 'hiccup' in Opera, Xubuntu, or the combination thereof.  Any suggestions would be appreciated.

Thanks in advance!

---

### Post by bluexrider on 2011-12-10
> **M_Mynaardt said:**
> Hi!

I have had a strange problem with Opera lately.  I've been trying one Linux distro or another for a while and have settled on Xubuntu; largely because I'm partial to the Xfce DE.  But the strangest thing happened recently with two sites I've never had problems with before.  In both cases, when I selected these sites, they caused some, even all, of the menus in Opera to become rectangles, as if they're unrecognizable fonts.  I've never seen that before.  And if I opened the same sites in another browser (Firefox or Chromium), there was no such problem.

Does anyone know what would cause this?  And how to fix it?

The two websites this happend to me are:
     [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
     [http://elementaryos.org/](http://elementaryos.org/)

I've accessed these sites without incident in other distros other than Xubuntu; so I'm not sure if there's a 'hiccup' in Opera, Xubuntu, or the combination thereof.  Any suggestions would be appreciated.

Thanks in advance!

I tried both sites using Opera 11.6 and no issues

---

### Post by Ms. Daisy on 2011-12-10
Do you have some kind of script blocker, like NotScript, running in Opera?

---

### Post by M_Mynaardt on 2011-12-11
> **bluexrider said:**
> I tried both sites using Opera 11.6 and no issues

I've never had problems like that with any site before.  It was so bad in Opera 11.52 that it messed up _all_ of Opera's menus and I had to reinstall it (to version 11.6).  Now, when I look at either site, it makes anything the mouse cursor moves over act strange until I close the tab opened with either of those sites.

I'm figuring there must be a setting *somewhere* that's causing this odd-ball behavior.  Something that's easily overlooked, I'm sure...

Thanks.

---

### Post by M_Mynaardt on 2011-12-11
> **Ms. Daisy said:**
> Do you have some kind of script blocker, like NotScript, running in Opera?

Not that I'm aware of.  Where would I look to see if there is anything like that running in Opera?  I looked through Preferences and couldn't figure out where that might be…

Thanks…

---

### Post by procdump on 2012-01-25
Hi there,

Here's how I solved this issue. For some reason in my Xubuntu the opera browser has chosen 'Droid Sans' for a font that is to be used for menus/toolbars etc. Go to Settings/Preferences/Advanced/Fonts into your opera browser and change the occurrence of 'Droid Sans' to 'DejaVu Sans' and this problem will be solved.

---

### Post by M_Mynaardt on 2012-01-25
> **procdump said:**
> Hi there,

Here's how I solved this issue. For some reason in my Xubuntu the opera browser has chosen 'Droid Sans' for a font that is to be used for menus/toolbars etc. Go to Settings/Preferences/Advanced/Fonts into your opera browser and change the occurrence of 'Droid Sans' to 'DejaVu Sans' and this problem will be solved.

That's something that never occurred to me!

And it works too!  I went into Settings/Preferences/Advanced/Fonts and changed every occurrence of a "Droid" font with its equivalent "Deja Vu" font.  And, voilà!  It worked! I checked out the two sites that first caused *Opera* to go wonky on me and no problems now.

Thanks for that!

---

