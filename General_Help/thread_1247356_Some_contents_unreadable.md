---
title: "Some contents unreadable?"
date: 2009-08-22
forum: General Help
---

### Post by beatlesfan94 on 2009-08-22
On two of my computers - a desktop and a laptop - when I right-click on "File System" under "Computer", when it's scanning for files, it says "some contents unreadable". I don't know what this really means and why it says that.

I thought it said that on my desktop because maybe I didn't do something right when using Gparted (but everything works alright, and I've done plenty of disk checks at boot time on both computers.) Not only that, but I completely re-formatted my laptop when I installed Ubuntu. I'm not dual-booting Windows on my laptop like I am on my desktop.

Help me please! :) And these drives are new. The desktop is brand new (only a few months probably) and the laptop is old, but I believe the harddrive is new.

---

### Post by AmerNewbieInDE on 2009-08-22
it isnt that they are not readible, they are un-readible with your permisions..

---

### Post by michy99 on 2009-08-22
> **AmerNewbieInDE said:**
> it isnt that they are not readible, they are un-readible with your permisions..

Exactly. If you were to open a nautilus session as root,```
gksudo nautilus
```you would not see that. Nothing is wrong.

P.S. Only use root nautilus sessions when necessary. You can really mess things up if you're not careful.

---

### Post by beatlesfan94 on 2009-08-22
Thanks for the explanation. I'm new to Ubuntu, and I'm still getting used to everything. It's frustrating to have to install and remove packages, or get something to work correctly, or having to do something in the terminal - but it's... interesting. :)

The reason I asked was I found some topics on Google and there was this whole big discussion - posting results from a terminal command, all that good stuff...

Thanks again.

---

