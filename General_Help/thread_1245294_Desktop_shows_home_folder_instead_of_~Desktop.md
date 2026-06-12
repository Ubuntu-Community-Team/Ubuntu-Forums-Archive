---
title: "Desktop shows home folder instead of ~/Desktop"
date: 2009-08-20
forum: General Help
---

### Post by fowie on 2009-08-20
I have my ~/Desktop folder mapped to a second harddrive, so 
~/Desktop -> /data/users/Username/Desktop
and on one restart of the computer the second harddrive didn't come up, so Ubuntu mapped my desktop to my home folder instead.  The second hard drive is now back online but even though the gconf setting "Show home dir for desktop" or whatever it's called is unchecked, it's still only showing the home directory.  How do I get my desktop back??

---

### Post by aum11 on 2009-08-23
This worked for me:

Edit ~/.config/user-dirs.dirs and set "XDG_DESKTOP_DIR" to "$HOME/Desktop".

---

### Post by fowie on 2009-08-24
awesome, worked like a charm, thanks!

---

