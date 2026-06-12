---
title: "reverting 10.04 to 9.10"
date: 2010-05-26
forum: General Help
---

### Post by Gakumerasara on 2010-05-26
I was wondering if anyone could tell me a simple way to revert my 10.04 (2.6.31.21) to 9.10.

<rant>10.04 has been a disaster for my Acer laptop.  NVidia must hate Ubuntu because any time I try to load into 2.6.32.22, the damn thing black-screens and dies.  2.6.31.21 "works", but I get flooded with errors related to the generic nvidia drivers.  And I've specifically NOT installed the proprietary drivers because I know from past experience that they kill my computer, regardless of which Ubuntu version I use.  Plus 10.04 is just... why did they change everything?  The default color scheme makes my eyes bleed, and even the close/minimize/maximize buttons are in the wrong place.  But that's minor...  The real problem is that my graphics capabilities are shot to hell, and since this is a computer used for work-related image processing, I need 9.10 back.</rant>

Reinstalling from disk is not an option since any install disc (alt or otherwise) newer than 8.04 fails.  (A fresh install of 9.10 involved installing 8.04 => 8.10 => 9.04 => 9.10)  Is there a simple apt-get type command I can use to revert it?  If so, please let me know; thanks.

---

### Post by philinux on 2010-05-26
> **Gakumerasara said:**
> I was wondering if anyone could tell me a simple way to revert my 10.04 (2.6.31.21) to 9.10.

<rant>10.04 has been a disaster for my Acer laptop.  NVidia must hate Ubuntu because any time I try to load into 2.6.32.22, the damn thing black-screens and dies.  2.6.31.21 "works", but I get flooded with errors related to the generic nvidia drivers.  And I've specifically NOT installed the proprietary drivers because I know from past experience that they kill my computer, regardless of which Ubuntu version I use.  Plus 10.04 is just... why did they change everything?  The default color scheme makes my eyes bleed, and even the close/minimize/maximize buttons are in the wrong place.  But that's minor...  The real problem is that my graphics capabilities are shot to hell, and since this is a computer used for work-related image processing, I need 9.10 back.</rant>

Reinstalling from disk is not an option since any install disc (alt or otherwise) newer than 8.04 fails.  (A fresh install of 9.10 involved installing 8.04 => 8.10 => 9.04 => 9.10)  **[COLOR="Red"]Is there a simple apt-get type command I can use to revert it?  If so, please let me know[/COLOR]**; thanks.

No there isn't, only reinstall. Since you need this machine to work stick to the 2.6.31.21 kernel and deactivate the nvidia driver, stick to the nouveau driver.

---

