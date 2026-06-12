---
title: "After Firefox 3.5.1 upgrade Ubuntu gives 3.0 updates?"
date: 2009-08-05
forum: General Help
---

### Post by JimBuntu on 2009-08-05
Hello,

I upgraded Firefox to version 3.5.1 which went perfectly, but I'm still getting 3.0 updates in the update manager. Is there a reason why? When I go to synaptics package manager it shows the installed version is the 3.0. Should this version be uninstalled? I dont want to accidentally revert back to 3.0 by using the update manager...

---

### Post by Intrepid Ibex on 2009-08-05
didn't you install the firefox-3.5 separately?

---

### Post by techstop on 2009-08-05
How did you upgrade to FF3.5? It sounds like you didn't install Shiretoko, but installed from the tar.gz on the Firefox site, or some other similar method.

If you installed Shiretoko, you will get updates through the package manager for both FF3.0 and FF3.5. If you did it any other way, you will get updates only for FF3.0.

Think about it, your package manager can only update packages installed by it. It can't update manual installations.

---

### Post by JimBuntu on 2009-08-05
I used this guide here in the forums: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimizing+firefox]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimizing+firefox") "Installing Other Versions" section.

---

### Post by techstop on 2009-08-05
> **JimBuntu said:**
> I used this guide here in the forums: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimizing+firefox]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=optimizing+firefox") "Installing Other Versions" section.

Well, that's a manual installation (not through the package manager), so what I said above holds true. You will get updates for FF3.0 through the package manager, but not for FF3.5

---

### Post by CatKiller on 2009-08-05
Firefox 3 and Firefox 3.5 are designed to be able to be installed side-by-side. That's why the version of firefox-3.5 in the repos is branded as "Shiretoko."

> **JimBuntu said:**
> I dont want to accidentally revert back to 3.0 by using the update manager...

You won't.

You'll continue to receive security updates to Firefox 3 as long as it is installed. This is a good thing.

---

### Post by JimBuntu on 2009-08-05
So, these updates that you can see in the attached pics at the start of this thread are ok to install? They will work the same? I don't have FF 3.0. When I go to "About Mozilla Firefox" it shows 3.5.1. Is there a way to manually get the updates that are for 3.5.1?

---

### Post by CatKiller on 2009-08-05
> **JimBuntu said:**
> I don't have FF 3.0. When I go to "About Mozilla Firefox" it shows 3.5.1.

No, when you go to "About Mozilla Firefox" *in Firefox 3.5*  it shows 3.5.1. You've already shown that you've *also* got Firefox 3.0 installed.

> Is there a way to manually get the updates that are for 3.5.1?

It depends how you installed it; there are four different methods in the post you listed. If you installed it from the repositories, then of course you'll get security updates. If you installed it by some other method then I have no idea.

---

### Post by aysiu on 2009-08-05
If you install Firefox 3.5.1 using Psychocats or UbuntuZilla, then it will not remove the Ubuntu repositories Firefox 3.0, and you also should not remove it.

If you want, you can install the updates you won't use. You can also lock the Firefox package in Synaptic. Just go to Package > Lock Package.

To update the Mozilla-downloaded Firefox to 3.5.2, close it completely and then paste this command into the terminal: ```
gksudo firefox
``` install the update, restart Firefox, close Firefox, and then start Firefox again normally. Do **not** ever use *sudo firefox*.

---

### Post by michy99 on 2009-08-05
> **JimBuntu said:**
> I don't have FF 3.0.

Wanna bet? Open a terminal and enter:```
firefox-3.0
```

---

### Post by JimBuntu on 2009-08-05
well I'll be...I have 2 firefox's. Hey aysui, what exactly does gksudo firefox do? I did it, and it seemed to completely restart firefox and erased all of my data like history and saved passwords. This is fine but I just want to make sure it is actually updating Firefox 3.5.1

---

### Post by CatKiller on 2009-08-05
> **JimBuntu said:**
> what exactly does gksudo firefox do?

It runs Firefox as root, using root's settings. Both of these functions are essential.

---

### Post by aysiu on 2009-08-05
> **JimBuntu said:**
> well I'll be...I have 2 firefox's. Hey aysui, what exactly does gksudo firefox do? I did it, and it seemed to completely restart firefox and erased all of my data like history and saved passwords. This is fine but I just want to make sure it is actually updating Firefox 3.5.1
```
gksudo firefox
``` launches Firefox as root but with the root user's Firefox profile (this is a good thing), allowing you to update to Firefox 3.5.2 (Help > Check for Updates).

After you've installed updates, restarted, and then closed Firefox, you should launch Firefox as you normally would (from the launcher icon) and then your bookmarks and history will all be there, unaffected.

*sudo firefox* (which you should **never** use) will launch Firefox as root but use your regular profile, which will mess up that profile's ownership, causing you to *really* lose your bookmarks, etc.

---

### Post by JimBuntu on 2009-08-05
Ok, I just realized that I now have the option to "check for updates" in the "help" menu of Firefox. I didn't have this before. I just clicked it and installed a security update.

---

### Post by aysiu on 2009-08-05
Okay, but after you install the updates, you should launch Firefox the normal way.

It is not good to run it as root all the time (*gksudo firefox*)--only to install updates.

---

