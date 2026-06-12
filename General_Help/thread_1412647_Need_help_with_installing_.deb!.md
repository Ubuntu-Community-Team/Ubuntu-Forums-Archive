---
title: "Need help with installing .deb!"
date: 2010-02-21
forum: General Help
---

### Post by Imaginary-r4e- on 2010-02-21
Hi! I'm trying to install code::blocks to Ubuntu 8.04 but I have failed so far. The following text is my input and the PCs output in the terminal:
```
anton@nti-laptop:~$ sudo dpkg --configure -a
[sudo] password for anton: 
anton@nti-laptop:~$ dpkg --install code.deb
dpkg: requested operation requires superuser privilege
```[I]
[COLOR=Black]Best Regards, Imaginary-r4e.[/COLOR][/I]

---

### Post by 2hot6ft2 on 2010-02-21
> **Imaginary-r4e- said:**
> Hi! I'm trying to install code::blocks to Ubuntu 8.04 but I have failed so far. The following text is my input and the PCs output in the terminal:
```
anton@nti-laptop:~$ sudo dpkg --configure -a
[sudo] password for anton: 
anton@nti-laptop:~$ dpkg --install code.deb
dpkg: requested operation requires superuser privilege
```[I]
[COLOR=Black]Best Regards, Imaginary-r4e.[/COLOR][/I]
No sudo at the start of the second command
```
dpkg --install code.deb
```
should be
```
sudo dpkg --install code.deb
```

---

### Post by Imaginary-r4e- on 2010-02-21
Thanks, I am no longer restricted by anything. However, I still got a problem. Am I not entering the directory in the right way? Something is obviously wrong and I can't figure it out by the output I get.
```
anton@nti-laptop:~$ sudo dpkg --install code.deb
dpkg-split: error reading code.deb: Is a directory
dpkg: error processing code.deb (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 code.deb

```
```
anton@nti-laptop:~$ sudo dpkg --install /home/anton/code.deb
dpkg-split: error reading /home/anton/code.deb: Is a directory
dpkg: error processing /home/anton/code.deb (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 /home/anton/code.deb
```
*Best Regards, Imaginary-r4e.*

---

### Post by 2hot6ft2 on 2010-02-21
When creating the deb, did you create a folder by the same name? Or is there a folder by that name there?

It's saying there is a folder by that name. A deb should not be a folder.

---

### Post by Imaginary-r4e- on 2010-02-21
Ah, thank you. When the deb-files was extracted it seems that they were put in a folder with the ".deb"-ending in its name. Feels kind of stupid not to have noticed that it was a folder-icon all along. Anyways, problem solved. Thanks again.

*Best Regards, Imaginary-r4e.*

---

### Post by 2hot6ft2 on 2010-02-21
You're welcome. Love how ubuntu and linux in general actually tells you something about what went wrong instead of just failing. Have fun.
:guitar:

---

