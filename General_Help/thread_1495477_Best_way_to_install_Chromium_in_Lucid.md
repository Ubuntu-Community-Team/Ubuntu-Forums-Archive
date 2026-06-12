---
title: "Best way to install Chromium in Lucid"
date: 2010-05-28
forum: General Help
---

### Post by Orographic on 2010-05-28
Hi all,

I've had a look at both Google Chrome and Chromium and prefer the latter at this stage. Google Chrome via the deb did install but didn't give me an entry in the menus and it seemed buggy.

So my question is:

Is it okay to follow this way to install Chromium?

[http://www.techdrivein.com/2010/02/install-chromium-web-browser-in-ubuntu.html](http://www.techdrivein.com/2010/02/install-chromium-web-browser-in-ubuntu.html)

Or better just from synaptic?

I don't think the synaptic version gets any updates at all?

---

### Post by sxmaxchine on 2010-05-28
I would do what it says on that website

---

### Post by colorlessprism on 2010-05-28
i prefer to use to repo's. if your worried about updates you can always get a ppa from launchpad. here is the list:

Beta Channel PPA: [https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta)

Dev Channel PPA: [https://launchpad.net/~chromium-daily/+archive/dev](https://launchpad.net/~chromium-daily/+archive/dev)

Daily debs (untested): [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by whitethorn on 2010-05-28
Have you tried

```
sudo apt-get install chromium-browser
```

I'm not sure but you might need the medibuntu repositories.

---

### Post by Joe-ubunt on 2010-05-28
I always just use [Ubuntu Tweak]("http://ubuntu-tweak.com/") (click here). After it's installed just go to sources center and enable Google and then go to Application Center to install. Google Chrome has been very stable for me and I get the regular updates for the browser. You can install Chromium if you prefer it to Chrome but they were identical to me except Chromium seemed to update more often than Chrome. Both were very stable but I use Chrome. 
 
Ubuntu Tweak is good for many other things also (change buttons to the right in window manager, cleaning up space, installing programs, changing things, etc.

---

### Post by geirha on 2010-05-28
It's in universe, just open Applications -> Ubuntu Software Center, search for chromium and install.

---

### Post by Orographic on 2010-05-28
Thanks everyone, excellent posts there. So, if i use the synaptic version of Chromium does that not update for the whole lifetime of Lucid?

I may re-connect to my testing drive and install Tweak and see how that goes. I'm just a bit reluctant to use Google Chrome though, it seems a bit against the spirit of Ubuntu but then again, I use Flash!

---

### Post by Orographic on 2010-05-28
Okay, I've installed Ubuntu Tweak and gone into sources centre and enabled Google Stable Source but when I go to Applications there is only Google Chrome Beta and Google Chrome Unstable. Where is the Google Chrome Stable that was released four days ago?

When I initially installed the Google Chrome .deb on a clean version of Lucid on this testing hard drive there was no item in the menus for it, even after multiple restarts of my system. I had to start it in terminal.

---

### Post by geirha on 2010-05-29
> **Orographic said:**
> Thanks everyone, excellent posts there. So, if i use the synaptic version of Chromium does that not update for the whole lifetime of Lucid?


It will get updates, but only if a security hole or a serious bug is found and fixed. New features will generally not be added.

---

### Post by Orographic on 2010-05-30
Thanks for that. Have left it off my main drive for now. Its still very early days for this browser, seems to be a bit buggy via Google search on it.

---

