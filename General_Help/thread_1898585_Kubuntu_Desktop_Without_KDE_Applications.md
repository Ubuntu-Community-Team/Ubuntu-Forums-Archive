---
title: "Kubuntu Desktop Without KDE Applications"
date: 2011-12-21
forum: General Help
---

### Post by irok30278 on 2011-12-21
After searching everywhere on the internet, I haven't been able to find a way to install the KDE shell without installing the KDE applications.  One site suggested getting it from the Ubuntu Software Center (under Kubuntu Plasma Desktop) but the search results for "kubuntu" are extremely limited and seem to only have the option of installing the applications with it.  I want the shell, just not the KDE apps for fear of clutter and annoyance.  If anybody has a console command for this, it would be greatly appreciated.  Thanks!

---

### Post by dabl on 2011-12-21
I think the kubuntu-desktop meta package does have a bundle of KDE packages in it, but it's only a subset of all the KDE suite.  Not knowing your space limitations or goals for your system, it would be easy enough to just install kubuntu-desktop, then remove the packages that you don't want, leaving the bits of KDE that you want.

---

### Post by QIII on 2011-12-21
What sort of clutter and annoyance do you anticipate?

---

### Post by elliotn on 2011-12-21
I too once wondered to do that, just install the kubuntu desktop the remove the konqueror, etc

---

### Post by amingv on 2011-12-21
I believe you're looking for kde-plasma-desktop

```
sudo apt-get install kde-plasma-desktop
```

It still installs a few core KDE aplications (like browser, file manager, etc), but nowhere nearly as many as kubuntu-desktop or somesuch.

---

### Post by irok30278 on 2011-12-21
> **amingv said:**
> I believe you're looking for kde-plasma-desktop

```
sudo apt-get install kde-plasma-desktop
```

It still installs a few core KDE aplications (like browser, file manager, etc), but nowhere nearly as many as kubuntu-desktop or somesuch.

Wow... I can't believe the command I was looking for was that easy.  Thanks, man!

---

