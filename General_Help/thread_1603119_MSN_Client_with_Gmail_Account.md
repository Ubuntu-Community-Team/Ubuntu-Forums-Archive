---
title: "MSN Client with Gmail Account"
date: 2010-10-22
forum: General Help
---

### Post by Preau on 2010-10-22
On windows I use my Gmail account to sign into Windows Live Messenger.
So my Gmail account is my windows live ID.

But Empaty on Ubuntu 10.04 wont let me log in. Is there any setting that should be changed or is a whole different client needed to make it work?

---

### Post by Grenage on 2010-10-22
What happens when you try?

---

### Post by Preau on 2010-10-22
Disconnected - No Reason Given

And then it keeps retrying.
I have the settings as:

Server: messenger.hotmail.com
Port: 1863

---

### Post by dj_penguin on 2010-10-22
> **Preau said:**
> Disconnected - No Reason Given

And then it keeps retrying.
I have the settings as:

Server: messenger.hotmail.com
Port: 1863

I had a similar problem on Maverick. Open up Synaptic and check whether you have both telepathy-butterfly and telepathy-haze installed.  If you do, try uninstalling telepathy-butterfly and restarting.

---

### Post by Grenage on 2010-10-22
> **dj_penguin said:**
> I had a similar problem on Maverick. Open up Synaptic and check whether you have both telepathy-butterfly and telepathy-haze installed.  If you do, try uninstalling telepathy-butterfly and restarting.

I recommend not uninstalling telepathy-butterfly, instead do this:

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

*Replace* the CONTACTS line with:

```
CONTACTS = ("contacts.msn.com", "MBI")
```

---

### Post by dj_penguin on 2010-10-22
** oops **
Accidental duplicate post

---

### Post by dj_penguin on 2010-10-22
** oops **
Accidental duplicate poste

---

### Post by dj_penguin on 2010-10-22
> **Grenage said:**
> I recommend not installing telepathy-butterfly, instead do this:

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

Replace the contacts line with:

```
CONTACTS = ("contacts.msn.com", "MBI")
```
I wasn't suggesting that the OP install butterfly, I was suggesting the they remove it.  Perhaps something was lost in the translation.

---

### Post by Grenage on 2010-10-22
> **dj_penguin said:**
> I wasn't suggesting that the OP install butterfly, I was suggesting the they remove it.  Perhaps something was lost in the translation.

It was a typo on my behalf.; I meant to say uninstall.  I removed butterfly (what a lovely name), and while it did work, I had a few glitches.  The workaround above was posted by someone on the bug report, and seems to do the job nicely.

---

### Post by Preau on 2010-10-23
Thanks Grenage it worked :D

---

