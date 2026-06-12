---
title: "Panel missing after switching desktops"
date: 2009-08-16
forum: General Help
---

### Post by rdmike on 2009-08-16
Hi all,

Everything is working well with Ubuntu except that whenever I switch from desktop 1 to any of the other three I have no top panel. I have compiz-fusion manager installed but don't see a setting to correct this. I'm sure its something simple but can't seem to figure it out. A lot of surfing for answers pointed me to netbook issues but I'm not using a netbook lol. Can anyone help me out please? :-)

---

### Post by P4man on 2009-08-16
Hmm.. perhaps have a look in ```
gconf-editor
```
Specifically in apps > panel > default_setup > top levels. 
Then im guessing screen is not set to zero? Compare top and bottom panels might give a clue.

If all else fails, just delete the panel and reconfigure a new one

---

### Post by rdmike on 2009-08-17
> **P4man said:**
> Hmm.. perhaps have a look in ```
gconf-editor
```
Specifically in apps > panel > default_setup > top levels. 
Then im guessing screen is not set to zero? Compare top and bottom panels might give a clue.

If all else fails, just delete the panel and reconfigure a new one

Shouldn't the OS automatically include the panels in each desktop window? I didn't see anything per your suggestion that seemed like it was what I needed. Other thoughts or suggestions?

---

### Post by rdmike on 2009-08-17
Ok, issue solved. It turns out my horizontal desktop setting (4) was ok but my vertical desktop setting was at (2) instead of one. Once I changed that to (1) everything was ok in terms of the panels being where they should be.

Thanks for the reply. :-)

---

