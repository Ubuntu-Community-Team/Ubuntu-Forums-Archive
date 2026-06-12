---
title: "nautilus could not create the required folder error"
date: 2010-07-15
forum: General Help
---

### Post by iceman600 on 2010-07-15
Im having this error when im trying to edit my root directories... First time happen to me. I have no idea what to do... Help needed. 
thanks...

---

### Post by ajgreeny on 2010-07-15
As a general point, it is unwise to mess around with root file system unless you know what you are doing, and what the consequences might be.  However to make that folder just run ```
sudo mkdir /root/.config/nautilus
``` in terminal.

Why do you need that folder?

---

### Post by AlphaLexman on 2010-07-15
Your personal setting and configurations should ALL be in your /home/username/ directory, symbolized by a '~/' double-check all your syntax and documentation.

---

### Post by iceman600 on 2010-07-15
> **ajgreeny said:**
> As a general point, it is unwise to mess around with root file system unless you know what you are doing, and what the consequences might be.  However to make that folder just run ```
sudo mkdir /root/.config/nautilus
``` in terminal.

Why do you need that folder?

did that command still i got an error... i need to to something on the root directory and i cant edit any of them unless im on root... im accessing it by opening it as an administrator and im getting this error...

---

### Post by iceman600 on 2010-07-15
> **AlphaLexman said:**
> Your personal setting and configurations should ALL be in your /home/username/ directory, symbolized by a '~/' double-check all your syntax and documentation.

it always been like that right?! i never changed anything  regarding directories... i always do this... but now im getting this error... i dont know where the error is coming from?

---

### Post by AlphaLexman on 2010-07-15
Nautilus MUST have run as 'root'. The 'home' directory for root is '/root' you must be root to create config files as root. (YOU DON'T WANT THIS!)

Nautilus SHOULD store settings in /home/username/.nautilus when executed first by you.

Check:
```
whoami
```

---

### Post by iceman600 on 2010-07-15
> **AlphaLexman said:**
> Nautilus MUST have run as 'root'. The 'home' directory for root is '/root' you must be root to create config files as root. (YOU DON'T WANT THIS!)

Nautilus SHOULD store settings in /home/username/.nautilus when executed first by you.

Check:
```
whoami
```

i dont understand... but i used to just right click a folder and run as administrator before... now i cant?! :confused:

---

### Post by AlphaLexman on 2010-07-15
> **iceman600 said:**
> i dont understand... but i used to just right click a folder and run as administrator before... now i cant?! :confused:
Why do you want to view/open folders as root? That is just bad practice. If permissions are set correctly, non-root users can read, but not write system and root files.

There is another user and thread here: [http://ubuntuforums.org/showthread.php?t=1530801](http://ubuntuforums.org/showthread.php?t=1530801) going on con-currently. Please follow.

---

### Post by ajgreeny on 2010-07-15
Note all the warnings here already, but you can install gksu-nautilus to get the right click "open as administrator" option.

But you still don't say why you need to do whatever it is you are trying to do!

---

### Post by iceman600 on 2010-07-15
> **ajgreeny said:**
> Note all the warnings here already, but you can install gksu-nautilus to get the right click "open as administrator" option.

But you still don't say why you need to do whatever it is you are trying to do!

gksu-nautilus already installed... thats what im trying to do... right clicking the  folder/file im having error.


im editin my host file and some default images...  like in covergloobus. 
i cant edit the root directory...

---

### Post by dcstar on 2010-07-16
> **iceman600 said:**
> 
........
im editin my host file and some default images...  like in covergloobus. 
i cant edit the root directory...

These are not in the **/root** folder, only files related to the root account are in that folder.

**Exactly** what are you trying to edit?

---

