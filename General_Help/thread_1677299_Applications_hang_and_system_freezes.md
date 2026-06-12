---
title: "Applications hang and system freezes"
date: 2011-01-28
forum: General Help
---

### Post by luvshines on 2011-01-28
I am running Ubuntu 10.10 on a Lenovo Thinkpad T61p with 2GB RAM.
When I was on Ubuntu 10.04, one day suddenly Azureus hung at the 'loading plugin' screen as it begins. I had to hard reboot my system and it(Azureus) never worked after that so I removed it.
Then after a couple of months same thing happened with Adobe Acrobat reader. As soon as I opened any pdf and started to scroll, it hung. System didn't respond and had to hard reboot. I moved to foxit reader

Then I upgraded to 10.10 and now mplayer hangs occasionally if I try to switch it to full screen. System stops responding totally

Any ideaz/suggestions ?
Where to begin debugging from ?
I can't figure out any pattern or any way to reproduce it.

**I haven't tried Acrobat reader and Azureus on 10.10**

---

### Post by luvshines on 2011-01-29
[color="red"]**** bump ****[/color]

---

### Post by midhuno on 2011-01-31
i hav d same problem
plzzzzzzzz help me
ubuntu 10.04 never hang

---

### Post by luvshines on 2011-02-12
**** Another bump ****

---

### Post by davidmohammed on 2011-02-12
what is the graphics card for that computer?

Are you using any proprietary graphics driver?  If so, what - and how did you install it?

---

### Post by luvshines on 2011-02-13
> **davidmohammed said:**
> what is the graphics card for that computer?

Are you using any proprietary graphics driver?  If so, what - and how did you install it?

This is what it says for graphics card```
lspci  | grep -i "vga\|display"
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro FX 570M] (rev a1)
```

I installed the drivers from System --> Administration --> Additional drivers, the one which was recommended

---

### Post by dino99 on 2011-02-13
its time to look at errors logged, that can help

---

### Post by luvshines on 2011-02-13
Ok, but do Adobe reader or mplayer log error messages to some file or produce any core dump for analysis ?
Since the system hangs completely, the only way to look into the error logs is after a hard reboot

---

### Post by dino99 on 2011-02-13
> **luvshines said:**
> Ok, but do Adobe reader or mplayer log error messages to some file or produce any core dump for analysis ?
Since the system hangs completely, the only way to look into the error logs is after a hard reboot

into /home:
.xsession-errors
.adobe
.mplayer
& so on

into /var/log/ (system admin logviewer)

---

### Post by luvshines on 2011-05-22
Not facing these issues now. Didn't do anything special, just regular upgrades.
Closing this thread for now

---

