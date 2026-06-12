---
title: "Deleted Mail / Chat notification widget, how to replace"
date: 2010-08-31
forum: General Help
---

### Post by riprowan on 2010-08-31
I inadvertently removed the mail/chat widget from my top panel.  This is the one that shows a green mail icon when I have mail, and lets me select "Chat" / "Mail" / "Broadcast" to start Empathy or Gwibber.

How do I get it back?   I looked through the list of widgets to add back to the panel and can't find it.

TIA.

---

### Post by ean5533 on 2010-08-31
> **riprowan said:**
> I inadvertently removed the mail/chat widget from my top panel.  This is the one that shows a green mail icon when I have mail, and lets me select "Chat" / "Mail" / "Broadcast" to start Empathy or Gwibber.

How do I get it back?   I looked through the list of widgets to add back to the panel and can't find it.

TIA.

It depends on how you removed it. First, make sure that you have that indicator installed:

```
sudo apt-get install indicator-messages
```

If it's already installed, then I believe you can right-click on the indicator applet and go to properties, and selectively turn on/off certain indicators.

(Note, I'm not in front of an Ubuntu machine so I'm doing this from memory)

---

### Post by riprowan on 2010-08-31
Thanks!  You inadvertently answered my question - what I didn't know was that the applet was called the "Indicator Applet".  I just re-added it to the panel.

---

