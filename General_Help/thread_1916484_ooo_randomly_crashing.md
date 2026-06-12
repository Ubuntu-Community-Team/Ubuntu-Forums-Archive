---
title: "ooo randomly crashing"
date: 2012-01-28
forum: General Help
---

### Post by qwertyjjj on 2012-01-28
I had the original install of ooo with MMeerkat but it would randomly crash (specifically on calc) and I always had to reload the documents through recovery.
So, I uninstalled them all through Synaptic and installed ooo version 3.
However, the same thing seems to be happening. There is no pattern to it, it could be copy and pasting into a cell, just typing a function, etc.

Any ideas what I can do?

---

### Post by Double.J on 2012-01-28
Hi there!

When you removed with synaptic, did you click on "remove" or "completely remove"?
"remove" is the same as
```
sudo apt-get remove packagename
```

"completely remove" is the same as
```
sudo apt-get purge packagename
```

In short completely remove also removes the configuration files. If the problem with open office was in the configuration files not delteted, then it could have come back?

If done through the terminal, I'd also recommend  auto cleaning after purging:

```

sudo apt-get purge packagename && sudo apt-get autoclean
```

Hope it helps... if this doesn't then we can be fairly sure it isn't oOo :-k

---

### Post by qwertyjjj on 2012-01-28
> **gnu/mirow said:**
> Hi there!

When you removed with synaptic, did you click on "remove" or "completely remove"?
"remove" is the same as
```
sudo apt-get remove packagename
```

"completely remove" is the same as
```
sudo apt-get purge packagename
```

In short completely remove also removes the configuration files. If the problem with open office was in the configuration files not delteted, then it could have come back?

If done through the terminal, I'd also recommend  auto cleaning after purging:

```

sudo apt-get purge packagename && sudo apt-get autoclean
```

Hope it helps... if this doesn't then we can be fairly sure it isn't oOo :-k

I think I just clicked remove.
How can I completely get rid of everything now and start again?
DO I remove all the help files also?
I tried sudo apt-get remove openoffice but it couldn't find it

---

### Post by ajgreeny on 2012-01-28
It might be worth trying to replace OOo with LibreOffice using the libreoffice ppa for 10.10.

I have done that on my 10.04 Lucid and find it much better than the supplied version of OOo for Lucid.
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Enable that and then search for libreoffice in synaptic, click to install, and the system will make sure that everything is removed that needs to be before installing LO.

---

### Post by qwertyjjj on 2012-01-30
> **ajgreeny said:**
> It might be worth trying to replace OOo with LibreOffice using the libreoffice ppa for 10.10.

I have done that on my 10.04 Lucid and find it much better than the supplied version of OOo for Lucid.
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Enable that and then search for libreoffice in synaptic, click to install, and the system will make sure that everything is removed that needs to be before installing LO.

What exactly is Libre Office anyway? What's the difference between that and OOO?

Anyway, I still have a problem despite uninstalling and reinstalling. Crashes randomly, doesn;t matter whether I use calc or Writer or whatever.

---

### Post by qwertyjjj on 2012-02-09
I uninstalled OOO 3 and installed Libre but the same thing is happening.
Something is causing it to crash and it has started spreading to FF, Firefix now crashes every so often.

---

### Post by Hagar Delest on 2012-02-09
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

You should also install the vanilla version, more robust IMHO: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Can't say if LibO is more or less stable, I only use OOo (3.3.0).

---

### Post by qwertyjjj on 2012-02-10
> **Hagar Delest said:**
> First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

You should also install the vanilla version, more robust IMHO: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Can't say if LibO is more or less stable, I only use OOo (3.3.0).

Already did that in the steps above.
Libre doesn't use OOO libraries does it? If it doesn;t, you would have thought it would be more stable but it is still crashing just like OOO.

---

### Post by Thorsen V on 2012-02-10
Big memory hungry apps randomly crashing *might* indicate a memory issue.

It might be an idea to reboot your machine and run a memtest from the boot menu.

This can take quite a while (try running it overnight perhaps?) then hopefully when it passes at least you can eliminate bad memory as a possible cause for your woes.

Good luck

---

### Post by Hagar Delest on 2012-02-10
> **qwertyjjj said:**
> Already did that in the steps above.
Sorry but I don't see where you say that the profile has been reset (renamed or deleted). Reinstalling won't delete that folder.

---

### Post by qwertyjjj on 2012-02-11
> **Hagar Delest said:**
> Sorry but I don't see where you say that the profile has been reset (renamed or deleted). Reinstalling won't delete that folder.

Sorry, I must have tried that on another post.
Either way, doesn't Libre office use a different profile folder?
As both Libre and OOO crash randomly.

---

### Post by Hagar Delest on 2012-02-11
They both have a specific profile indeed. But LibO could try to import the OOo one silently. So better rename both of them.
NB: If you get the registration wizard, then you're sure the profile has been reset.

---

### Post by qwertyjjj on 2012-02-12
> **Hagar Delest said:**
> They both have a specific profile indeed. But LibO could try to import the OOo one silently. So better rename both of them.
NB: If you get the registration wizard, then you're sure the profile has been reset.

No reg wizard appears in Libre for some reason?
I deleted the entire .openoffice folder in /home as I do not have it installed.
I then renamed the user profile in Libre to user.old

---

### Post by Hagar Delest on 2012-02-12
Hmm, indeed, no registration wizard with LibO...
It may have been removed then. Renaming the profile does reset it so it should be fine. Else, there is something else.

The crashes occur with specific documents?

---

