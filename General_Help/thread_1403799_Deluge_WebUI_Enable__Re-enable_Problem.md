---
title: "Deluge WebUI Enable / Re-enable Problem"
date: 2010-02-10
forum: General Help
---

### Post by cristofaro on 2010-02-10
Hi. I recently installed Deluge 1.2.0 from the following PPA:

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

I am using this on two different Linux computers. One is running Linux Mint 8 and the other is running Ubuntu Netbook Remix 9.10. The first time on either computer when I enable WebUI in the Deluge GUI it works fine. However if I ever disable it in plugins section I am subsequently unable to re-enable it (doesn't appear in the side panel again). Rebooting or reinstalling Deluge seems to have no effect.

Is this a bug or am I doing something wrong? Can anyone else replicate this problem as described? I have tried searching various forums and buglists but was unable to find anything.

---

### Post by Anubis on 2010-02-15
Confirmed.

---

### Post by cristofaro on 2010-02-16
So is there any known fix or should we submit a bug?

---

### Post by Anubis on 2010-02-18
> **cristofaro said:**
> So is there any known fix or should we submit a bug?

I just deleted all things webui related from ./config/deluge and restarted deluge and deluged then reenabled the webui plugin and it stays applied. 

BTW, the #deluged was completely useless in any assistance whatsoever in regards to this matter.

---

