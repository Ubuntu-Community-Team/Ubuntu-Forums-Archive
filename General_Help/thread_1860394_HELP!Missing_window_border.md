---
title: "HELP!Missing window border"
date: 2011-10-14
forum: General Help
---

### Post by yiranwu on 2011-10-14
Hi all,

I upgraded to 11.10 on my msi u135 last night.

First of all, the wireless(RT3090) was not recognized.
I used to blacklist the drivers provided by 11.04 because they did not work and I managed to get a working one.
However, after upgrade, old working drivers no longer work.
After playing around for a while I uncommented those line blacklisting the drivers provided by 11.10.  The result is now I have a working but fairly slow wifi connection.

Second, I dislike the unity and tried to remove both unity and unity-2d using apt-get.
After that I installed gnome-session-fallback and rebooted.

Then I found out that I cannot use my old indicators on the new gnome panel so I decided to just try to get used to unity.  At the same time, I noticed that unity is actually there.

Since this is just a netbook, I decided to just have unity-2d so I installed unity-2d and removed unity and rebooted again.

Then something weird happened, at the login screen, there is even no recovery mode but just a unity-2d option.  After logging into the system, there is now window border(which consists of close/min/max icons) for everything I opened.
The compiz package is installed.

I have some experience with Ubuntu but not a lot.

Ideas?

Any help is much appreciated!

Thank you all in advance!

---

### Post by ezramorris on 2011-10-14
Hi,
Welcome to Ubuntu Forums!

You could try reinstalling unity-2d. I'm guessing it's falling back to something else when you log in using the unity 2d option.

Hope this helps,
Ezra.

P.S. Personally, I wouldn't recommend uninstalling default stuff. For future reference, just installing gnome-panel enables the Classic options on the logon screen.

---

### Post by yiranwu on 2011-10-14
> **ezramorris said:**
> Hi,
Welcome to Ubuntu Forums!

You could try reinstalling unity-2d. I'm guessing it's falling back to something else when you log in using the unity 2d option.

Hope this helps,
Ezra.

P.S. Personally, I wouldn't recommend uninstalling default stuff. For future reference, just installing gnome-panel enables the Classic options on the logon screen.

Hi Ezra,

I have tried that but no luck.

Any other ideas?

---

### Post by ezramorris on 2011-10-14
> **yiranwu said:**
> Hi Ezra,

I have tried that but no luck.

Any other ideas?

I'm struggling. Maybe you could try making sure all the default packages are installed?

```
sudo apt-get install ubuntu-desktop
```

If not, maybe someone else will be able to help.

Ezra.

---

