---
title: "Cannot uninstall Safari 4 from Wine!"
date: 2009-12-05
forum: General Help
---

### Post by jeb800e on 2009-12-05
Please help me out here! I am experimenting with PlayonLinux and Wine, and I cannot uninstall Safari from Wine! I have been using the "Wine Application Uninstaller" to currently uninstall software from Wine. Please help me out here!
Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
You can go into the /home/username/.wine folder and delete the folder associated to Safari. The uninstall software isn't that special.

---

### Post by jeb800e on 2009-12-05
Okay. I removed everything I could find under my .wine folder relating to Safari, including from/the folders within that had anything to do with Apple or Safari, but, Safari, Apple Application Support, and Apple Software update are still found in the Wine Application Uninstaller, and they still open up! Please help me!

---

### Post by jeb800e on 2009-12-05
Is this considered violating the EULA or Terms of Use of Safari or any other program if I try to remove a program manually? What if I don't delete ALL the files, like lets say I didn't see the other files or I am new to removing manually?

---

### Post by howefield on 2009-12-05
Uninstalling programs from Wine can be problematic and appears to be a known issue with lots of bugs filed on the issue covering many different applications, but not a high priority to fix as yet.

[http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

---

### Post by jeb800e on 2009-12-05
Okay, I have removed my entire ~/.Wine directory, plus all the Wine-created menu entries. Overall, I have typed in all the commands the URL you sent me told me to do within part 5.1 of the Wine hq FAQ. Should there be *any* remnants or leftover files of Safari or any other Windows program on my computer?

So, I am still wondering, is it against the EULA or Terms of Use, Licenses, etc. of programs (mainly proprietary ones like Safari, etc.) to remove manually? What if I miss a part, or didn't recognise a part, etc.?

---

### Post by howefield on 2009-12-05
> **jeb800e said:**
> So, I am still wondering, is it against the EULA or Terms of Use, Licenses, etc. of programs (mainly proprietary ones like Safari, etc.) to remove manually? What if I miss a part, or didn't recognise a part, etc.?

I really wouldn't worry about that, if it was illegal to use the program you might have a problem, but seeing as it isn't....  

Uninstalling windows programs very often means you have registry entries and all sorts of other cruft left behind post removal, whether in a real/virtualised/wine installation, if your fears were to be the case, then virtually every single computer owning user would be guilty.

I'd be tempted to put money on Safari not completely uninstalling cleanly on any platform.

---

