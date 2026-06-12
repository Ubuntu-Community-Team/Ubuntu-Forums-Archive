---
title: "installation of programs"
date: 2011-03-25
forum: General Help
---

### Post by Kaspar44 on 2011-03-25
Hi Ive been having some trouble trying to install a program i downloaded off the web its a shell file i install it via the terminal through the command sh and then follow the instructions until it comes to the prefix i cant write in usr/local so i change it, it installs fine at the new location but when i go to run it through the exe link it say's it cant find the splash images even though there in the folder it wants to access them in usr/local is there anything i can do to install it in usr/local or change it so it will work? :confused:

---

### Post by hal8000 on 2011-03-25
You need admin rights to write to /usr/local.

You ideally need to quote the URL of the file you downloaded and its name.
Linux does not use exe files these belong to windows.
The files contents dictate the file type on linux, not its extension like on windows.
You could break something in Ubuntu if its not wrote for linux, but without any more details you would need to type sudo then your command to install your script

---

### Post by Kaspar44 on 2011-03-26
yeah looks like its working thanks! :)

---

