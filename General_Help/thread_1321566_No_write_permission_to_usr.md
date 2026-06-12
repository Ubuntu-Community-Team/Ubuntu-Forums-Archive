---
title: "No write permission to /usr/"
date: 2009-11-10
forum: General Help
---

### Post by Assim on 2009-11-10
Hello,

I tried to install a game from a .run file, everything seemed fine when I tried to install it from the terminal but the thing that happened was that the default location for installing the game was somewhere on the /usr/ directory, and when I clicked next it says that I have no write permission to usr. Any suggestions?

---

### Post by eldragon on 2009-11-10
only root can write there..

run the game installer with gksu preceding it.

---

### Post by P4man on 2009-11-10
try running the installer with root privileges. Run the same command but add "sudo" in front.

---

### Post by dox_drum on 2009-11-10
Did you try with super-user power?

---

### Post by scouser73 on 2009-11-10
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by coffeecat on 2009-11-10
It is a very bad idea to copy files into /usr, with or without the GUI, unless you are experienced and know what you are doing.

**Assim**, you have a *.run file which is the installer. That will do the work for you. [Have a look at this link](https://help.ubuntu.com/community/InstallingRunPackage). Unfortunately, that does not tell you how to get root privileges which you will probably need when you try to run the *.run package. Post more details, particularly the full name of the *.run file, and someone will tell you how to do this from the terminal.

---

### Post by Assim on 2009-11-10
Thanks for the reply but it still doesn't work.

I'm installing the .run file using this tutorial: [http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)

---

### Post by Elaztic on 2009-11-10
Assim, which game are you trying to install.
Please provide more info in your requests for help.

---

