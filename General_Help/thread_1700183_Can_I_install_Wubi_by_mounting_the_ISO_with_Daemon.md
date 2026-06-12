---
title: "Can I install Wubi by mounting the ISO with Daemon Tools?"
date: 2011-03-04
forum: General Help
---

### Post by Exsecrabilus on 2011-03-04
Can I use an ISO-mounting program such as Daemon Tools Lite to mount the Ubuntu Desktop 10.10 ISO and install Wubi? (Because I don't have a CD/DVD I can burn it to.)

---

### Post by seawolf167 on 2011-03-04
EDIT: I replied incorrectly thinking about a different topic - yes, you can mount the image with any mounting software and install it (wubi). I don't like the new versions of daemon tools, and suggest you use [VirtualCloneDrive]("http://www.slysoft.com/en/virtual-clonedrive.html") instead. It works essentially the same, just mount it, and you can install it like the disk is in the drive.

For virtualization (my original post): Say you are using VBox and have a copy of the .iso stored somewhere, you can use VBox's 'Virtual Media Manager' to mount the iso for virtual machines (so you don't actually have to mount it on your local machine).

In VBox, click File -> Virtual Media Manager -> change to the CD/DVD images tab, click Add, then add your iso file and it'll be available to your virtual machines.

---

### Post by Exsecrabilus on 2011-03-04
> **seawolf167 said:**
> You don't even need to go that far. Say you are using VBox and have a copy of the .iso stored somewhere, you can use VBox's 'Virtual Media Manager' to mount the iso for virtual machines (so you don't actually have to mount it on your local machine).

In VBox, click File -> Virtual Media Manager -> change to the CD/DVD images tab, click Add, then add your iso file and it'll be available to your virtual machines.

Thanks for replying, but I want to use Wubi, because I do not have enough RAM to run Windows 7 and Ubuntu at the same time. Is the scenario that I asked about in the OP possible?

---

### Post by seawolf167 on 2011-03-04
Aye, after I posted it I realized I replied incorrectly and edited my previous post.

---

### Post by Exsecrabilus on 2011-03-04
What is Virtual CloneDrive? It looks interesting, can you explain to me the benefits of it over Daemon Tools?

---

### Post by seawolf167 on 2011-03-04
From what I remember, the old versions of daemon tools were fine, then they started to add extra features and ads, and later released a 'lite' version of the program and a fully functional 'normal' version that cost $ (this was a couple years ago - I don't know if it has changed since then).

I found VirtualCloneDrive and switched to that since it has [almost] all the features daemon tools has, but doesn't do the annoying things the 'lite' version does like try to change your browser home page, complain when you try to remove it from autostarting, etc.

I'm sure either/both will work just fine though.

---

### Post by bcbc on 2011-03-04
You don't need to mount the iso to install it. You just need wubi.exe and the ISO in the same folder and it will find it and use it. The version of wubi.exe must match the ISO. (Described [here]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?") for offline installs, but works online as well).

---

