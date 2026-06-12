---
title: "Installing .exe files using Wine?"
date: 2011-09-17
forum: General Help
---

### Post by Bryan334 on 2011-09-17
I downloaded the .exe file for the starshatter game demo, but when I right click on it and select "Open With Wine Windows Program Loader", A message appears saying:

Blocked: wine start /unix
The file '/home/bryancm/Downloads/StarshatterDemo.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the _executable bit_.

I know the program isn't dangerous, but what am I doing wrong. How do I install the exe with WINE? Thanks for any help. God bless and God speed.

---

### Post by Morbius1 on 2011-09-17
Please see this: [http://ubuntuforums.org/showpost.php?p=10757436&postcount=2](http://ubuntuforums.org/showpost.php?p=10757436&postcount=2)

---

### Post by gandaran on 2011-09-17
right click the .exe file » properties » permissions tab » mark the box allow executing file

---

### Post by corncob on 2011-09-17
When you right-click on the file go to properties, then click on the Permissions tab and check 'allow executing file as program'.  If you want it to open with Wine as its default you can set this in the 'Open With' tab.

---

### Post by Bryan334 on 2011-09-17
Thanks for the help.

---

### Post by galacticaboy on 2011-09-17
Just in case anyone needs this, if you are using Xubuntu, you cannot right click on the file and then mark it as executable, you have to do a command. Right click in the folder that the .exe is in and click "Open a terminal here" then type "chmod +x "insert name of program here without quotation marks" then press enter. That should do it if you use Xubuntu!

---

### Post by Morbius1 on 2011-09-17
Remember folks, Wine itself is incapable of determining if a given file has a Linux executable bit set.

---

