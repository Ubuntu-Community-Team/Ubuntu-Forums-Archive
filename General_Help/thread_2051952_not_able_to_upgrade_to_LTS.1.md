---
title: "not able to upgrade to LTS.1"
date: 2012-09-02
forum: General Help
---

### Post by derekcentrico on 2012-09-02
I've been running 12.04 for some time.  I install all updates twice weekly, so the system isn't behind on those.

When I do a do-release-upgrade, there is nothing available.

I figured that by updating everything as I do I must already have the 12.04.1 components installed.

But, my Details pane states that I'm running 12.04 LTS and not 12.04.1.  

Am I missing something here?

---

### Post by cottfcfan on 2012-09-02
If you have everything updated you are already running 12.04.1.
You are not missing anything. That is normal.

---

### Post by derekcentrico on 2012-09-02
> **cottfcfan said:**
> If you have everything updated you are already running 12.04.1.
You are not missing anything. That is normal.

That was my expectation.  

However, I would expect it to at least show 12.04.1 in the Details rather than the 12.04.  I could have sworn that the LIVE CD of .1 shows it as being 12.04.1.

So for the lifetime of 12.04 LTS on my system, it will not show anything aside from 12.04 whilst other newer installs might.  Is that accurate?

---

### Post by cottfcfan on 2012-09-02
No. It doesn't matter if you have 12.04.1, 2, 3, or 4.
It will always show up in your details panel as 12.04 LTS.
Just keep it updated and you'll be fine.

---

### Post by PaulW2U on 2012-09-02
> **derekcentrico said:**
> However, I would expect it to at least show 12.04.1 in the Details rather than the 12.04.  I could have sworn that the LIVE CD of .1 shows it as being 12.04.1.

Typing **lsb_release -a** in a terminal window will confirm you are running 12.04.1.

---

### Post by derekcentrico on 2012-09-02
> **cottfcfan said:**
> No. It doesn't matter if you have 12.04.1, 2, 3, or 4.
It will always show up in your details panel as 12.04 LTS.
Just keep it updated and you'll be fine.

> **PaulW2U said:**
> Typing **lsb_release -a** in a terminal window will confirm you are running 12.04.1.

Gracias to you both.  Glad to be know how this works for LTS releases.

---

