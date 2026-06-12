---
title: "google saving a file search.json file"
date: 2011-12-15
forum: General Help
---

### Post by 3rdsurfer on 2011-12-15
i am on ubuntu 11.0 with kde, using firefox


when i try to do a google search, it prompts me to download a file search.json which seems to be a text file which all looks like jiberish 100,000 characters long.

what is this and how do i get it to stop?

---

### Post by lovinglinux on 2011-12-16
See post #757 onwards at [http://ubuntuforums.org/showthread.php?t=1193567&page=76](http://ubuntuforums.org/showthread.php?t=1193567&page=76) for a discussion about the same issue. The user solved the problem by creating a new Firefox profile. However, this will probably be fixed by deleting *prefs.js* file in your profile at  ~/.mozilla/firefox/<profilename>. Keep in mind that deleting that file erase all your Firefox settings. Make a backup of your profile before deleting files. Also keep in mid that you need to close Firefox before deleting profile files.

---

