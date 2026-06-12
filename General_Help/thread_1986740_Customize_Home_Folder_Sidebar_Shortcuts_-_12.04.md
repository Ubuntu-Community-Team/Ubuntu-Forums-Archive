---
title: "Customize Home Folder Sidebar Shortcuts - 12.04"
date: 2012-05-25
forum: General Help
---

### Post by wlane on 2012-05-25
I'm sure this has been answered before, but I can't for the life of me find the answer. I'm sure it's because I'm searching something incorrectly.

I'm trying to customize the home folder shortcuts in 12.04, that is, remove "Pictures", "Videos", "Music", and add other folders such as "Dropbox". In 11.04 you could simply right click and click delete or drop a new folder there, but this is no longer the case.

Any help is greatly appreciated.

---

### Post by drs305 on 2012-05-25
Take a look in ~/.config/user-dirs.dirs

You can place a comment symbol # in front of any you don't want to see in the Nautilus sidebar.

---

### Post by wlane on 2012-05-25
Thank you very much drs305. That couldn't have been easier.

---

