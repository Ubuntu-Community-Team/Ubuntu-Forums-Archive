---
title: "For all you Chromium fans"
date: 2012-07-30
forum: General Help
---

### Post by vasa1 on 2012-07-30
[Active PPA for latest stable chromium?]("http://askubuntu.com/questions/169874/active-ppa-for-latest-stable-chromium")

> I had the exact same problem, and had come to the conclusion that Chromium had been abandoned (switched to FireFox; worst idea ever!). In any case, when the Unity Webapps Preview was released I installed it right away, and it updated both FireFox and Chromium. After FireFox moving so slowly it hurt, I moved back to Chromium and decided I could live with it being outdated... Lo and behold! It had been updated! 
Read the rest for a how-to. (I've not tried it because I'm happy with Chrome.)

---

### Post by vasa1 on 2012-07-30
There's an interesting follow-up [here]("http://askubuntu.com/questions/170235/how-do-i-cherry-pick-packages-from-a-ppa"). A poster wants to know if one could just cherry pick the Chromium browser from the ppa.

---

### Post by vasa1 on 2012-07-31
The person who asked the question has provided an answer. In part, "The trick is using two pinning clauses. The first to disallow ALL packages from the PPA and the second to select the ones you want."

---

### Post by daKoolaid on 2012-08-12
> **vasa1 said:**
> The person who asked the question has provided an answer. In part, "The trick is using two pinning clauses. The first to disallow ALL packages from the PPA and the second to select the ones you want."

We could also manually add the ppa to sources.list, upgrade Chromium only and then comment out that ppa for normal system updating. Chromium won't be updated all that often I'd think. I just updated to Chromium 20 like this, definitely feels faster than 18!

I used to do this with some Mint packages in a Debian base.

Edit: If you go to chrome:sandbox in the address bar, you will see suid and namespaces sanboxing enabled. You don't get this with the daily snapshots from the commondatastorage site so a benefit for repo Chromium.

I'm on xubuntu and I added the Unity/webapps ppa. There were only 3 packages it wanted to upgrade. Chromium, Chromium ffmpeg codecs and libindicator-messages-status-provider. If you're on xubuntu, this is definitely the way to go. Even with Unity, it's just a matter of only selecting Chromium and codecs for upgrade. I'm happy now. :)

---

### Post by vasa1 on 2012-09-05
[http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html#more](http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html#more)

---

### Post by vasa1 on 2012-12-02
> Hi folks,

Chad, who is tasked with getting the Chromium ppa [1] back in the land of
the living is now at the stage that we can check progress using his
personal PPA [2]. Please test and report back.

Thanks,

Phill.
1. [https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable)
2. [https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily](https://launchpad.net/~cmiller/+archive/chromium-browser-stable-daily)
[https://lists.ubuntu.com/archives/lubuntu-users/2012-December/003125.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-December/003125.html)

---

