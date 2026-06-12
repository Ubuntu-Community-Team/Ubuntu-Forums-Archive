---
title: "is hardware management completely automated?"
date: 2011-03-06
forum: General Help
---

### Post by bongorider on 2011-03-06
In remix I have a "Device manager", but it really isn't a manager, because other than viewing devices you cannot actually do anything, it's more of a "device viewer", I have read online that ubuntu has a system -> Administration tool for enabling drivers etc, but I can't find anything like this on remix.  What do I do if I want to use an old driver or a different driver to the one Ubuntu select automatically?

---

### Post by 3rdalbum on 2011-03-06
If you have to manage things such as "what piece of code does the computer run to work with a peripheral device" then the computer is merely wasting your time and you'd be better off using a pen and paper.

In short, you don't really do that stuff on Linux, and I personally would say that you should never be able to do that with personal computers. They are there to make life easier. If they require constant babying then I'd rather not use one.

---

### Post by bongorider on 2011-03-06
Well regardless of what everyone's personal opinions are, is it a fact that you simply cannot manage drivers in Ubuntu remix?

---

### Post by mcduck on 2011-03-07
> **bongorider said:**
> Well regardless of what everyone's personal opinions are, is it a fact that you simply cannot manage drivers in Ubuntu remix?

Sure you can, just pop open a terminal and start tweaking. Although it's quite unlikely you could improve anything by changing to different driver versions, the *opposite* is much more likely... :D

edit: Actually it's exactly the same as with the Desktop version, the graphical driver tool there isn't made for installing/switching any drivers you want, it's only there to allow you to install a proprietary driver if some of your hardware components requires one to work, and then allows you to switch between that proprietary driver and the default one.

It's really rather rare you'd ever need to change your drivers in any other way than to make sure you are running the latest available version: Which Ubuntu handles automatically for you though the Update Manager. Need to downgrade a driver is rather special case and has to be done manually.

---

