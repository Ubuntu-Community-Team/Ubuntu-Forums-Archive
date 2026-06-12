---
title: "Strange things afoot!!"
date: 2011-07-13
forum: General Help
---

### Post by ian3006 on 2011-07-13
Hi guys.

I have done a search, but found nothing matching my problems.

I run Natty on two laptops; mine is a Compaq Presario CQ61 and the other is my daughters which I passed on to her, a Samsung R60 plus.

I upgraded my machine pre-release and having seen it, junior wanted hers upgrading, which I did as soon as the stable release came out.

Now, all is fine on the Compaq, but on the older Samsung there have been and still are ongoing problems.

Sometimes when booting up Unity loads. More often than not though it doesn't. Also, logging out doesn't work - a few black and white lines followed by a complete freeze.

I have tried all sorts, including two full clean installs, but I can't nail this.

I have a feeling that it's graphics card related, the Samsung has ATI Radeon (x1250).

I try to reset Unity, but towards the end of the process I get the following two fatal errors:
[B][I]
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected[/I][/B]

Any help would be gratefully accepted as the daughter is now a convert to Ubuntu and I don't want her to lose faith.

Regards,

Ian.

---

### Post by mali2297 on 2011-07-13
Can you see any error messages in the file /var/log/Xorg.0.log?

Are you using the open-source or the proprietary driver for the graphics card?

I do not know how old your graphics card is, but if you previously used the proprietary driver, it might be that it no longer supports the card.

---

### Post by ian3006 on 2011-07-13
No error messages lurking in there. And no propriety drivers.

Anyway, in a moment of madness, I've upgraded junior to 11.10 Alpha and all is well. I know it isn't stable, but the applications that she needs seem okay so we'll live with it.

Very odd indeed.

Regards.

---

