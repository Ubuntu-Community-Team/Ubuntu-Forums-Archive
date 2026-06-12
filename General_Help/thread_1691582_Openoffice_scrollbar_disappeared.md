---
title: "Openoffice scrollbar disappeared"
date: 2011-02-20
forum: General Help
---

### Post by tushantin on 2011-02-20
It was there about a month ago, but some updates came up and there was this glitch I noticed; the scrollbar vanished, and in its place is some kind of a glitch. I thought it would go away after a bit more updates, but it hasn't and I don't know what to do.

EDIT: Funny thing. No need to reinstall your Office suite, just change your GTK theme. It works!

---

### Post by rvchari on 2011-02-20
> **tushantin said:**
> It was there about a month ago, but some updates came up and there was this glitch I noticed; the scrollbar vanished, and in its place is some kind of a glitch. I thought it would go away after a bit more updates, but it hasn't and I don't know what to do.

must be something must ve gone wrong with ur config files. you can delete the .openoffice.org directory in ur home folder

```
rm -R ~/.openoffice.org
```
this should remove total 'dot' files in your .openoffice.org directory thats created during first use of openoffice. now start openoffice again and check if you ve restored to your defaults.

---

### Post by Hagar Delest on 2011-02-20
If no change, try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by tushantin on 2011-02-26
I'm sorry for the late response; had been held back due to late 3G payments and my current eProject business. 

@rvchari: I tried your method, but unfortunately it didn't work. I didn't exactly try the command and instead went to the home folder and straight up deleted the .openoffice.org folder. All the preferences were defaulted, but the scroll glitch still hasn't been fixed. 

@Hagar de l'Est: I'm not sure what a vanilla version is, but I'll try your methods as described in your post. If it doesn't help I may have to simply switch to LibreOffice PPA...

Anyway, thanks for the help so far. I'll let you in if the problem gets fixed.

---

### Post by bazcor on 2011-02-26
I had that problem in Pinguy Linux, a offshoot of Ubuntu. The cure for that was to change the window Theme in appearance. May be worth a shot!

Good luck .. Barry

---

### Post by tushantin on 2011-02-26
@bazcor: Aww, man! You're late! But not *too* late. I've already replaced OpenOffice with the recent version of LibreOffice (the GTK integration, even with LibreOffice-gnome pack, isn't 100% good but the suite itself is faster than its predecessor). Turns out it wasn't the problem with the office suites in the first place: The scroll was back in LibreOffice and was functional, but the bar itself was missing so I had to scrub the scroller like swiping on a touchscreen phone (cool and all). 

I changed the GTK theme from Hope GTK to Gaia Sprout and... it worked. The scrollbar's back. Thanks!

But man! I loved that Hope GTK...

---

