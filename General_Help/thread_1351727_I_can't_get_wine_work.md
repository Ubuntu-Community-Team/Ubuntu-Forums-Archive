---
title: "I can't get wine work"
date: 2009-12-10
forum: General Help
---

### Post by cypherdtraitor on 2009-12-10
Wine has never worked for me. Just recently, I purged and re-installed with the latest edition of Wine for Intrepid Ibex from Wines repository.

Now, I placed a completely contained copy of the popular software "project 64" in a file called P64 in my home folder. I also placed the install in my home folder.

Neither of these do anything bug hang for 8 or 9 seconds when I try to run them with Wine. In the CLI, it looks something like this:

```
cypher@Hal:~$ cd ~/p64
cypher@Hal:~/p64$ project64.exe
bash: project64.exe: command not found
cypher@Hal:~/p64$ wine project64.exe
Warning: could not find DOS drive for current working directory '/home/cypher/p64', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\project64.exe": Module not found
cypher@Hal:~/p64$ Warning: could not find DOS drive for current working directory '/home/cypher/p64', starting in the Windows directory.
bash: Warning:: command not found
cypher@Hal:~/p64$ wine: could not load L"C:\\windows\\system32\\project64.exe": Module not found
```
Note that this is the contained application, not the installer.

I'm a little confused that it is trying to load from an emulated C drive. I would try to relocate this C: drive to my home directory or something, but it won't let me. 

Anyone know what's wrong?

---

### Post by cypherdtraitor on 2009-12-10
RESOLVED:

psudo-code

winecfg
(the GUI opens)
(Click Drives tab, autodetect, apply, exit)
wine ~/p64/project64.exe

So far the performance is good. Some odd color issues. I may turn this into a tutorial.

---

