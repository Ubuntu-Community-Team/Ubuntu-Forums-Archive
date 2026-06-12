---
title: "Lost Evolution after upgrade"
date: 2010-07-25
forum: General Help
---

### Post by rex66 on 2010-07-25
Hi all....I upgraded to Ubuntu 10.04 and it seems to have lost my evolution email program and all the information in it. It is no longer on the panel and no longer in Internet applications but when I go to the software center it says that it is still installed. Is there a chance it is still there and usable? I'd like to keep it rather than switch. How would I find it?

Thanks

---

### Post by lmarmisa on 2010-07-25
Maybe the Evotution icon was deleted.

First of all, check if the Evolution program runs normally. Open a terminal (Applications -> Accesories -> Terminal) and type:

```

evolution

```If you wish to add evolution to the panel, click right button on the panel, Add to panel -> Indicator applet.

---

### Post by dcstar on 2010-07-26
> **lmarmisa said:**
> Maybe the Evotution Application Launcher was deleted.

First of all, check if the Evolution program runs normally. Open a terminal (Applications -> Accesories -> Terminal) and type:

```

evolution

```If you wish to add evolution to the panel, click right button on the panel, Add to panel -> Indicator applet.

There is no separate launcher any more in 10.04, it is simply the mail icon on the top RHS panel.

---

### Post by rex66 on 2010-07-26
Thanks very much for your speedy help!
It does run normally. 
I had to do a custom Application Launcher and when I use it I get a Terminal message stating:

** (evolution:3259): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution:3259): DEBUG: mailto URL program: evolution



But then it opens and runs normally so I guess I can live with that. I thought I'd lost some important emails that I was not smart enough to back up.

Thanks again for your help!

---

### Post by lmarmisa on 2010-07-26
> **dcstar said:**
> There is no separate launcher any more in 10.04, it is simply the mail icon on the top RHS panel.

The **Indicator applet** adds two icons to the top RHS panel:

1) A sound speaker icon for Sound preferences
2) An envelope icon for chat, mail (evolution) and Broadcast Account.

Kind regards,

Luis

---

