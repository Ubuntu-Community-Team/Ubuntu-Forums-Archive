---
title: "About the source code"
date: 2010-12-21
forum: General Help
---

### Post by Odaym on 2010-12-21
Maybe this is a silly question, but please bare with me :)
Where does the Linux source code actually sit on my linux machine? I really would like a comprehensive answer, thank you in advance!

---

### Post by psusi on 2010-12-21
Wherever you saved it to when you downloaded it.

---

### Post by ajgreeny on 2010-12-21
You may well have very little, if any, source code on your computer, as the OS can not use source code to run the machine as such.

Linux is "open source" which means all the source code is available to you to download and compile for yourself, if you wish to do so.  However, the beauty of most of the distros available these days, including Ubuntu, is that they are pre-compiled and everything is included as binary packages, all ready for you to download and install without compiling it yourself.

---

### Post by oldos2er on 2010-12-21
When you run **apt-get source <package>**, it is saved to whatever folder the command is run in; it defaults to /home/user.

---

### Post by hakermania on 2010-12-21
Summing up from the 3 above questions:
1) Ubuntu is Open Source
2) This means that you can DOWNLOAD the source code, it isn't inside your machine
3) This can be done by giving  **apt-get source packagename**, e.g. **apt-get source gedit**

---

