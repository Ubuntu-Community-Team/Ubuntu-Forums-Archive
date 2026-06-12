---
title: "Questions about fonts and font collections"
date: 2010-04-09
forum: General Help
---

### Post by JEBB on 2010-04-09
I copied an OpenOffice document from my Mac to my Linux netbook and found that some fonts in the original weren't on my netbook.  This leads to ask these questions:  In Linux are fonts installed for system wide use like on my Mac or are they program specific like in Windows?  If they are system-wide, can you suggest some font collections and sources for them?

Thanks

---

### Post by fragos on 2010-04-09
Fonts are installed system wide in Linux. Individual users may have their own fonts by placing the font files in /home/{user}/.fonts. To make new fonts visible to all aps you can reboot or run "sudo fc-cache -fv" in a terminal window.

---

### Post by coffeecat on 2010-04-09
> **JEBB said:**
> If they are system-wide, can you suggest some font collections and sources for them?

You'll probably need the Microsoft core fonts which cannot be included in a default install for licensing reasons. These include Times New Roman, Arial, Comic Sans (:(), Webdings and a few others. You can install them by selecting the ttf-mscorefonts-installer package in System > Adminstration > Synaptic.

There are also many other ttf* packages in the repositories. Have a look in Synaptic.

**Edit:** just noticed from your sig that you are running Jaunty on your netbook. At some time in the past the ttf-mscorefonts-installer package was called something like msttcorefonts. I can't remember whether that was so in Jaunty or much earlier. If you can't find ttf-mscorefonts-installer have a search for 'corefonts'. It'll be there somewhere. Or you could install the package ubuntu-restricted-extras which is primarily for restricted multimedia codecs, flash and java, but includes the ms fonts.

---

