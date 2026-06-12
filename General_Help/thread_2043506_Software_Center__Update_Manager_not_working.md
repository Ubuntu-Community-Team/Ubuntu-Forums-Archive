---
title: "Software Center / Update Manager not working"
date: 2012-08-16
forum: General Help
---

### Post by juliarain on 2012-08-16
My Ubuntu Software Center and Update Manager are not working, and have not been working for a couple of days. 

**Error Message** (appearing under giant red minus sign in top panel of Unity)
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (
   E: Encountered a section with no Package: header, 
   E: Problem with MergeList    /var/lib/apt/lists/us.archive.ubuntu.com_
   ubuntu_dists_precise-updates_restricted_binary-i386_Packages, 
   E: The package lists or status file could not be parsed or opened. 
)'. This usually means that your installed packages have unmet dependencies. 

I recently upgraded to 12.04 from 10.04 (non-Unity) and have experienced a variety of other random problems. My computer is not as fast as it was before. Gnome shell freezes when I try to simultaneously request a new webpage and adjust the monitor brightness. Are these Gnome problems or Ubuntu problems? Does KDE work better with 12.04? This is all getting really annoying. I'm used to Linux working better than Windows, not the other way around.

---

### Post by juliarain on 2012-08-16
As an exciting new update to the situation, I just tried to uninstall the Software Center so I could reinstall it and see if that would fix the problem, but when I tried that I got a similar error: 

```
julia@computer:~$ sudo apt-get purge software-center
[sudo] password for julia: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by juliarain on 2012-08-16
Fixed it, following instructions from [this forum]("http://ubuntuforums.org/showthread.php?t=863742"). 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

