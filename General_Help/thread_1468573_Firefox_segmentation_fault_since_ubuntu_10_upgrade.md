---
title: "Firefox segmentation fault since ubuntu 10 upgrade"
date: 2010-05-01
forum: General Help
---

### Post by xi4 on 2010-05-01
Hi all, My firefox won't start since I upgraded to ubuntu 10. I start it in the terminal and get the message "segmentation fault". Can anyone help me get it running again?. Thanks

---

### Post by happyhamster on 2010-05-01
- Does the message say anything else except "segmentation fault"?

- Try moving the file "profiles.ini" from the folder ~/.mozilla/firefox to somewhere else. It's a hidden folder in your home folder. (To be able to see hidden files when using the nautilus file-browser, press ctrl-h).
Then start firefox to let it make a new profile.

---

### Post by lonesloane on 2010-05-02
> **happyhamster said:**
> - Does the message say anything else except "segmentation fault"?

- Try moving the file "profiles.ini" from the folder ~/.mozilla/firefox to somewhere else. It's a hidden folder in your home folder. (To be able to see hidden files when using the nautilus file-browser, press ctrl-h).
Then start firefox to let it make a new profile.

Yep, that's it. Simply renamed the profiles.ini file and Firefox is working again. Looks like one of the installed extensions was having issues...
Thanks for the tip Happyhamster.

---

### Post by xi4 on 2010-05-02
Removing the ini file worked thanks!, and there was nothing other than "segmentation fault"

---

### Post by xi4 on 2010-05-02
Well it worked for a bit, then started crashing randomly. Anyway I got more info which was "attempting to load libmoon" or something like that. This is a package for a silverlight alternative plugin i installed. I removed this package and now it works fine. 


So it looks like the problem was libmoon package

---

### Post by peramus on 2010-05-10
I had the same problem with the silverlight plugin.  Got the error Loading libmoon then segmentation fault.  Tried re-installing moonlight plugin but it did not help had to remove it for firefox to work again.

---

