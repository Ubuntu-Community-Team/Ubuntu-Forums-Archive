---
title: "Will uninstalling Wine Uninstall it's windows programs that were installed on it?"
date: 2012-07-11
forum: General Help
---

### Post by linuxvstheworld on 2012-07-11
I know this is a stupid question, but I'm on my brother's Ubuntu laptop and I've been having troubles putting Fl Studio on it via Wine. I found another easier to use software(Linux multimedia studio) And he wants to use that instead. So I try Wine un-installer to un-install Fl Studio, but it keeps freezing when it trys and gives up. Either way, he doesn't need wine, so I am assuming uninstalling Wine uninstalls the programs with it. Does it? :)

---

### Post by carl4926 on 2012-07-11
Removing wine does not remove the applications
They are installed in the hidden folder .wine in the home folder
Deleting the folder .wine will delete the installations, but you might prefer to drill down a little further in .wine to delete the actual application folder rather than the whole of .wine
Though if you don't plan to use wine, it'll not really matter

Any application entries in the menu that are there, may need to be edited out manually

---

### Post by linuxvstheworld on 2012-07-11
My brother doesn't need it so I just did ctrl+H at the home folder to show hidden files, then deleted .wine. 

Thanks for the info!

---

### Post by carl4926 on 2012-07-11
> **linuxvstheworld said:**
> my brother doesn't need it so i just did ctrl+h at the home folder to show hidden files, then deleted .wine. 

Thanks for the info!
yw                    :d

---

