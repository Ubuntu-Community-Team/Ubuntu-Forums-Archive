---
title: "Problem with Synaptic Package Manager"
date: 2010-01-30
forum: General Help
---

### Post by niva2gr on 2010-01-30
Hello everyone!
I am completely new to Linux, and so my questions might be a bit silly. 
So here what's going on.

First of all everytime i try to open the Synaptic Package Manager  i get this message:

[COLOR=Blue]"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"[/COLOR].

What's wrong, and how can i fix it?


Also, i cannot install anything. I tryed to install VLC player from with the software manager, but it got stuck at 0%.
I also tryed to download Skype for Ubuntu 8.10 (that's the latest version), but i got this message:

[COLOR=Blue]"Only one software management tool is allowed to run at the same time." [/COLOR]
How will i find out about what software management tools are installed in my computer, and how do i choose only one?
Does all this have to do with the fact that Synaptic Package Manager does not work?

---

### Post by Soul-Sing on 2010-01-30
its already in the message: ```
sudo dpkg --configure -a
```
in the terminal==>password==>enter

---

### Post by Cunnilingus on 2010-01-30
Try opening the terminal and typing in the command shown in the error message
[http://ubuntuforums.org/showthread.php?t=537126](http://ubuntuforums.org/showthread.php?t=537126)

edit: leoquant beat me to it

---

### Post by niva2gr on 2010-01-30
Thank you guys!

Problem solved!

---

