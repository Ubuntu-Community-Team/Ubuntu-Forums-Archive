---
title: "Blocking Updates (Only Some of Them)"
date: 2009-12-20
forum: General Help
---

### Post by SuperMike on 2009-12-20
I need to keep getting updates for everything except Firefox and XULRunner, which I can update myself because I like to stay more cutting edge on those and use like FF 3.5.6. I tried unchecking these and moving on with regular update installation, but I can't get the other updates to stop prompting me with the little orange icon.

I have Ubuntu 8.04 LTS.

How do I disable only those updates so that I don't keep getting prompted for them?

---

### Post by audiomick on 2009-12-20
I have never done this, but I read it in a post. It might or might not be what you want.

If you open synaptic package manager, find the package and select it, in the menu bar under "package" there is an option to fix the version so that it wont be updated. I don't know how that will react to you manually updating the packages.

---

### Post by Agent ME on 2009-12-20
If you're installing firefox yourself from source, then you should remove the firefox package, then reinstall firefox from source.

---

### Post by MaxIBoy on 2009-12-20
You can select the desired packages in Synaptic, then go to the "package" menu at the top of the screen and select "lock version." See first attached screenshot.

You can track down all your locked packages later by going to "status" and then "pinned" (see second screenshot.)

---

### Post by SuperMike on 2009-12-21
MaxIboy -- that did the trick. It's now stopping those updates so that I can do them on my own.

---

