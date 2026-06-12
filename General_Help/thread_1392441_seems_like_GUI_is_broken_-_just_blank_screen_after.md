---
title: "seems like GUI is broken - just blank screen after login"
date: 2010-01-28
forum: General Help
---

### Post by keevill on 2010-01-28
Using Karma and kubuntu -single boot.
When I restarted my machine, the login appeared as usual and I entered my usual password but it was not accepted . I tried several times including making sure that caps lock / num lock etc were not invoked.

I then rebooted into recovery mode and let it run its course.
When I rebooted and input my login password, I can get a bit further. The login is accepted but the GUI opens with a blank wallpaper and the terminal prompt window open at the keevill@keevill-desktop.

The ls command shows the name of the files which are on the desktop but they are not visible on the GUI nor are any other icons for applications.
It seems like the kubuntu GUI is broken or something.
I tried uninstall and then re-install but just the same.
If I am forced to re-install Ubuntu I guess this means I lose all my settings and applications will have to be all installed again ??
How can I avoid this?

---

### Post by nothingspecial on 2010-01-28
Can you remember anything you may have done that caused this?

---

### Post by keevill on 2010-01-28
> **nothingspecial said:**
> Can you remember anything you may have done that caused this?

Nope ! The only error message I was getting prior to this was a 'lack of space' on the virtual partition within Sun Virtualbox - but this has been happening for some days now.
Oh - I did update some packages requested by UB as normal but as I recall, all booted up normally after that.

-keevill-

---

### Post by warfacegod on 2010-01-28
Sounds like you might need to reinstall your desktop. Synaptic> mark kubuntu-desktop for complete removal> apply> then install it again. Then go to Edit in the top left and select Fix Broken Packages.

---

### Post by keevill on 2010-01-28
> **warfacegod said:**
> Sounds like you might need to reinstall your desktop. Synaptic> mark kubuntu-desktop for complete removal> apply> then install it again. Then go to Edit in the top left and select Fix Broken Packages.

I can't get to Synaptic !
Just got Terminal

---

### Post by warfacegod on 2010-01-28
> **keevill said:**
> I can't get to Synaptic !
Just got Terminal

```
sudo synaptic
```

---

### Post by nothingspecial on 2010-01-28
If you have no space and then downloaded updates then that could be the root of your issue. Give kubuntu more space.

---

### Post by keevill on 2010-01-29
> **warfacegod said:**
> ```
sudo synaptic
```

This did the job !
Many thx!
-keevill-

---

### Post by warfacegod on 2010-01-29
Great! does that mean your GUI isn't broken any more?

---

