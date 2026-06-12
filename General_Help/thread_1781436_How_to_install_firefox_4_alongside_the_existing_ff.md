---
title: "How to install firefox 4 alongside the existing ff 5 on 11.04"
date: 2011-06-13
forum: General Help
---

### Post by hihihi100 on 2011-06-13
Before you start thinking that I made a mistake with the title of the thread, or thinking that FF5 has not been ye unvelied (it is, its a beta AFAIK), read my story:

I dont know how it happened, I think it may be a ppa, but I dont know which one (could it be independent third party sources?). Other ideas are welcomed.

Thing is: when I click the FF icon I access to ff5, and there are a number of aps that are not compatible, thus, my need to keep using ff4. I googled and found: [http://www.wikihow.com/Install-multiple-versions-of-Firefox-on-Ubuntu](http://www.wikihow.com/Install-multiple-versions-of-Firefox-on-Ubuntu)

and tried to follow the instructions:

ff5 works without issues
ff4: created a new directory in /home/dexter/Compiled/firefox4, where I extracted ff4.tar.bz2

I have also run ```
firefox -profilemanager
```and created 2 profiles: Firefox5 and Firefox4
 Firefox5 leads to ff5 without issues, I didnt change anything
 Firefox4: I have tried to link it to the current folder of ff4, so it reads: /home/dexter/Compiled/firefox4

Launchers:
the ff icon leads to ff5, no issues
newly created ff4 launcher reads: /home/dexter/Compiled/firefox4 -no-remote -P "Firefox4"

but when clicked:

Could not launch application, Failed to execute child process "/home/dexter/Compiled/firefox4" (Permission denied)

help please.

---

### Post by pqwoerituytrueiwoq on 2011-06-13
you can use mozilla's version
here is a script i made to install firefox
[http://ubuntuforums.org/showthread.php?t=1708905](http://ubuntuforums.org/showthread.php?t=1708905)
it will not replace the existing firefox

---

