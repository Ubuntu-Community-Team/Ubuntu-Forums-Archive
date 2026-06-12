---
title: "Terminal hang or just a quirk?"
date: 2009-12-31
forum: General Help
---

### Post by aplonis on 2009-12-31
So I was following the doc for installing Postfix and got to a point where the install script asked a question. The screen changed color and listed answers to choose from, but presented no way to answer. There was nothing to click and it ignored any and all keys I tried to press.

Rebooted and tried again, same issue.

To complete the install, I had to connect with Putty from a Windows Vista box...where it went fine.

So...does Gnome Terminal have a bug? Or did I simply fail to grok how to answer terminal multiple-choice queries?

When I searched this behavior via Ubuntu lists, I found another who had the exact same issue form three weeks prior...but nobody answered him.

TIA,

Gan

---

### Post by dcstar on 2009-12-31
> **aplonis said:**
> So I was following the doc for installing Postfix and got to a point where the install script asked a question. The screen changed color and listed answers to choose from, but presented no way to answer. There was nothing to click and it ignored any and all keys I tried to press.

Rebooted and tried again, same issue.

To complete the install, I had to connect with Putty from a Windows Vista box...where it went fine.

So...does Gnome Terminal have a bug? Or did I simply fail to grok how to answer terminal multiple-choice queries?

When I searched this behavior via Ubuntu lists, I found another who had the exact same issue form three weeks prior...but nobody answered him.

TIA,

Gan

```
sudo dpkg-reconfigure debconf
```

Choose Gnome.

---

### Post by aplonis on 2009-12-31
Okay, did that. There was no "Gnome" among the choices. So I went with the defaults of "Dialog" and "High" for the two queries respectively. 

Had to do this via Putty from Windoze laptop, of course, since the queries were themselves also dialogs.

As a test, tried the same thing via Gnome termial and it went the same. So now it works. Thanks.

---

