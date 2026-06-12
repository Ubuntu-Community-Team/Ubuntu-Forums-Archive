---
title: "How to add an entry to the context menu of Gnome terminal?"
date: 2012-02-05
forum: General Help
---

### Post by nodnolse1 on 2012-02-05
Hi, I'd like to add a entry to the Gnome terminal context menu to open folder path with Gnome Nautilus file manager. I'd use the commands 'gnome-open' 'xdg-open'. Just for instance, I'd like to add an entry as this '[gnome terminal with google search support]("http://ubuntuguide.net/add-google-search-support-in-ubuntu-gnome-terminal")'. I also discovered that 'KDE Konsole' has natively the entry/function in the context menu, but, I prefer to use the Gnome one. Thanks for reading and hope for a solution ;)

---

### Post by aasdfasdfg on 2012-02-05
The source code of the modified terminal can be found from the ppa you [posted]("http://bazaar.launchpad.net/%7Etualatrix/ibentu/gnome-terminal/files"):
You can study his modifications and make similar ones, and then compile your own terminal modification. Are you familiar with writing Gtk apps in c?

Once you have made your modifications, feel free to share them with the community like this user did, by creating your own launchpad ppa with your code! Then the cycle may continue...

---

### Post by nodnolse1 on 2012-02-07
> **aasdfasdfg said:**
> The source code of the modified terminal can be found from the ppa you [posted]("http://bazaar.launchpad.net/%7Etualatrix/ibentu/gnome-terminal/files"):
You can study his modifications and make similar ones, and then compile your own terminal modification. Are you familiar with writing Gtk apps in c?

Once you have made your modifications, feel free to share them with the community like this user did, by creating your own launchpad ppa with your code! Then the cycle may continue...

Thank you for the hint, but unfortunately I never programmed, the only 'language' that I know so so is the shell script even if I think that is not classified as a programming language. Anyway, If in some manner I'll can to create it, I'll share it with pleasure. Have a nice day

---

