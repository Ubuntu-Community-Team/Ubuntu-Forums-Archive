---
title: "two version of Firefox in the same time"
date: 2009-09-16
forum: General Help
---

### Post by cristisava on 2009-09-16
hello, 

I'm recently (2 months) running ubuntu 9.04.

It is working well.

I am using Firefox and it is slow.

I made some checks and on my system is installed 2 version of firefox ( 3.5.2 and 3.0.14).

Can be this the cause of the annoyance?

please advise me!

Thank you!

---

### Post by Grenage on 2009-09-16
It shouldn't, I have both installed (I use both).  You can try removing one:

apt-get remove firefox

or

apt-get remove firefox-3.5

---

### Post by lovinglinux on 2009-09-16
They won't affect each other. Besides, I don't recommend uninstalling version 3.0, because is part of the Ubuntu desktop.

Firefox 3.5 is a lot better than 3.0, but you can still optimize it by following the tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

Keep in mind that the 3.5 version from the repositories is accessed trough a different menu launcher, which is "Shiretoko Web Browser". Additionally, it uses a different profile folder. So if you use both versions, any bookmarks you add or settings you change won't be synchronized with the other version profile.

---

### Post by cristisava on 2009-09-17
Thanks a lot ! It's clear !

---

### Post by StuartN on 2009-09-17
> **lovinglinux said:**
> I don't recommend uninstalling version 3.0, because is part of the Ubuntu desktop.

In what way is Firefox part of the desktop, apart from being the default browser? Surely there is no aspect of Ubuntu's function that would be affected by uninstalling Firefox, or indeed uninstalling all web browsers?

---

### Post by Keilaron on 2009-09-17
I think what lovinglinux means is that it's a dependency of the ubuntu-desktop package (ubuntu-desktop -> ubufox -> firefox); Thus, if you uninstall Firefox, you have to remove the ubuntu-desktop package as well, which means you may miss on certain updates or programs which are controlled via that package.
Therefore, in a sense there IS an aspect of Ubuntu's functionality that's affected by such a decision. Of course, nothing stops you from requesting Synaptic to reinstall it, and see what other packages are suggested (this is what I do, as I've removed other software I'm not interested in e.g. fspot).

---

### Post by mcduck on 2009-09-17
> **StuartN said:**
> In what way is Firefox part of the desktop, apart from being the default browser? Surely there is no aspect of Ubuntu's function that would be affected by uninstalling Firefox, or indeed uninstalling all web browsers?

As far as I know some parts of Gnome, like the Help browser (Yelp), use Gecko for HTML rendering. And Gecko comes as part of Firefox..

(this might have changed, but at least some versions ago removing Firefox removed Yelp and some other Gnome components as well.)

---

### Post by lovinglinux on 2009-09-17
> **StuartN said:**
> In what way is Firefox part of the desktop, apart from being the default browser? Surely there is no aspect of Ubuntu's function that would be affected by uninstalling Firefox, or indeed uninstalling all web browsers?

I have checked synaptic and the ubuntu-desktop metapackage just recommends firefox, so it doesn't depend on it. Nevertheless, there are packages that depend on Firefox 3.0, that cannot be simply replaced by FF 3.5. For instance, gecko-mediaplayer. If you want to use gecko-mediaplayer with FF 3.5, then you need to keep FF 3.0. Besides, there is no good reason to remove FF 3.0.

---

### Post by StuartN on 2009-09-17
> **lovinglinux said:**
> Besides, there is no good reason to remove FF 3.0.

I don't tend fix what it isn't broken, so my systems fill up with fluff until I upgrade the OS.

My question about Firefox is just concern about the consequences of over-dependence on a package like a browser, as with the endless difficulties caused by Internet Explorer's increasing role in Windows.

---

### Post by lovinglinux on 2009-09-17
> **StuartN said:**
> I don't tend fix what it isn't broken, so my systems fill up with fluff until I upgrade the OS.

My question about Firefox is just concern about the consequences of over-dependence on a package like a browser, as with the endless difficulties caused by Internet Explorer's increasing role in Windows.

I agree. I don't think the user will have system-wide issues by removing firefox-3.0, but some browser related stuff might not work. Besides, I don't know how Karmic Koala will make the transition from Shiretoko to Firefox 3.5. If the user removes **firefox-3.0**, it also removes **firefox**, **firefox-gnome-support** and **ubufox**. So I believe if the user upgrade to Karmic Koala in this scenario, he might end up without Firefox. Then will be another chapter in the Shiretoko forum saga.

---

