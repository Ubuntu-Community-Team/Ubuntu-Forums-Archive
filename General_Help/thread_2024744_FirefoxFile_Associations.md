---
title: "Firefox/File Associations?"
date: 2012-07-14
forum: General Help
---

### Post by ArminasAnarchy on 2012-07-14
Hi all, lets start with a celebration of my first post on the Ubuntu forums. :) It feels great to be a member of "the community" proper, and this feels like some sort of induction!

Apologies if this is posted in the wrong forum, but...

Basically, I've got some problems with Firefox. Currently I'm running the Aurora version (I've added the PPA to ensure it's updated on my system, currently running "15.0a2 (2012-07-13)" - obviously this will change over the next few days as updates are virtually daily. I've a feeling it's more related to Kubuntu anyway, since I've never had this problem before (I've run Ubuntu, Mint, Fedora before settling with Kubuntu - I'm in love with KDE!).

Issue is as follows: whenever I'm sent a link (for instance, over Pidgin) or when opening a hyperlink from a .odt file in LibreOffice, it is not opening with Firefox. Having previously had Rekonq installed (and now UNinstalled), it tries to open it through that, before realising the program is missing. Presumably there's just some config file to edit somewhere, but I don't same to be able to do it through the file associations under the system settings.

Another small and possibly similar issue, after downloading a file I find it handy to navigate to it by right clicking and selecting "Open File Location". Firefox doesn't seem to even attempt to open my default file manager (95% sure it's Dolphin - that's what was used in KDE installs I've previously run, and I've done nothing to change it). I've no idea where the Linux equivalent of the Dolphin .exe file would be found - as a clumsy work around, I could navigate to that if told how, but it seems that isn't so much fixing the problem as taping over the cracks and it'd be good to know what was wrong!

Sorry this is a little rambly - I've tried to pre-empt any questions that could be asked and provide as many details as possible! :)

Cheers,

AA.

---

### Post by Rexilion on 2012-07-14
Maybe some old remnants inside the following file?

~/.local/share/applications/mimeapps.list

---

### Post by ArminasAnarchy on 2012-07-17
> **Rexilion said:**
> Maybe some old remnants inside the following file?

~/.local/share/applications/mimeapps.list

No luck I'm afraid :(. The only things in /share are the "Trash" file and a plain text doc called .directory (with hidden files shown).

Any further ideas? Is it possible this .local file would be in another location?

( PS I'm working on the principle that ~/ refers to the home folder - I'm still relatively new to Ubuntu).

---

### Post by ArminasAnarchy on 2012-07-19
Pidgin problem solved...now if someone can suggest a fix for Firefox, that would be brilliant!

---

### Post by Wirephire on 2012-07-19
Go to "Systemsettings -> Default Applications -> Web Browser" and set it to **firefox**.
Also make sure that **dolphin** is set as your default file manager.


*~wph*

---

### Post by ArminasAnarchy on 2012-07-20
> **wirephire said:**
> Go to "Systemsettings -> Default Applications -> Web Browser" and set it to **firefox**.
Also make sure that **dolphin** is set as your default file manager.


*~wph*

Done, and done. I'll reboot later and report back (currently working), but thus far no fix. Cheers anyway!

---

### Post by Wirephire on 2012-07-21
Since it won't set firefox as default browser, follow the cli method:
```
sudo update-alternatives --config x-www-browser
```This will show all installed browsers on your system. Choose the number of the browser you want to set as default and hit enter.


*~wph*

---

