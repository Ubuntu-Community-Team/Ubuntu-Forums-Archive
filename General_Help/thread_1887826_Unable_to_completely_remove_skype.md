---
title: "Unable to completely remove skype"
date: 2011-11-28
forum: General Help
---

### Post by Nathre on 2011-11-28
Hello everyone. My problem is that I tried to install skype i386 on my ubuntu64 using ia32-libs but I couldn't. When I tried to remove my skype I did it using the software center but forgot to quit skype. After that it wasnt on my software center or my synatics pm... but I can still launch it from unity :(  I already used "sudo apt-get autoremove --purge skype" but it says it's not installed. 

Already restarted my pc but still I can launch it but not remove. Need your help :s

---

### Post by ExileAmongYou on 2011-11-28
The best place to start would be to search for the skype folder that's (presumably) still on your system. Open "Search for files" (the search application), set the Look in folder: option to "File system" (so it searches your whole drive), and search for skype. Hopefully this will turn up a folder containing the installed files, and with any luck, a Readme file that might tell you how to uninstall it.

If you find the folder, but there's no uninstall instructions, post some details about where the folder is and what files it contains.

---

### Post by vangop on 2011-11-28
Try 
```
sudo apt-get autoremove --purge skype:i386
```

---

