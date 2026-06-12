---
title: "password protecting folders"
date: 2010-01-20
forum: General Help
---

### Post by Adrenochrom3 on 2010-01-20
ok this is what im trying to do. i have some files on my computer, that i dont need any of my friends seeing. and i want to get the folder to prompt me for a password when you are to click on said folder. i tried googleing it and it keeps giving me BS that i dont want. now i know you linux masters can give me the answer i want. 

now one thing yall should know is, on my laptop, i am the only user.

---

### Post by Adrenochrom3 on 2010-01-25
anyone gonna help out?

---

### Post by Wataru8675 on 2010-01-25
Found this on Linux Forums:

> I've been interested in adding passwords to files and directories myself,and that is what brought me to this thread.

I tried this after reading this thread,and it seems to work.
Give this a shot and see what you come up with.

Create a directory on your desktop for this experiment,and name it test.
Copy a few files and paste them into this directory so it isn't empty 
Now open a terminal and enter:

cd Desktop <enter>
zip -e -r test test <enter>
enter a password <enter>
confirm password <enter>

You now have a zip file named test.zip with a password needed to open it."

-linny

I just tried it and it worked fine, as long as you don't need to worry about people reading the file names.

Full post here: [http://www.linuxforums.org/forum/linux-security/18535-how-can-i-protect-folder-password.html](http://www.linuxforums.org/forum/linux-security/18535-how-can-i-protect-folder-password.html)

---

### Post by spiderbatdad on 2010-01-25
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by bluefrog on 2010-01-26
don't give access to your session to your friends. create them accounts they will use. then o-xr on your folders. they won't see them from their session.

---

### Post by ushills on 2010-01-26
or you could try this

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by stinkeye on 2010-01-26
```
sudo apt-get install cryptkeeper
```

You can then start Cryptkeeper from the menu >> Applications >> System Tools >> Cryptkeeper It will launch to your System Tray, click the icon and choose "New encrypted folder". Give it a name and a location on your hard disks to have the encrypted folder. Click "Forward" then enter your password, 

Once that is done nautilus will open your new encrypted folder which is currently empty. You can now move the data you want to make secure into this folder, when you are done, click on the Cryptkeeper System Tray icon again and "untick" the folder that you had just created. Once unmounted the data cannot be read and the folder will become hidden from view. When hidden the folder is simply renamed with a dot preceding it.

To access the data again just click the icon and "tick" the box next to the entry to remount it and make the data accessible.

---

### Post by davy jones on 2010-03-17
can anyone explain a SIMPLE way of password protecting certain folders?? if i wanted to merely hide them then i can just rename it with a dot in the beginning but i want a password prompt everytime that folder is clicked on and none of the solutions anyone has offered is good for that

---

### Post by timgood on 2010-03-17
The solution above is elegant and practical, and does exactly what you want. In order to gain access to your files, you need to input a password. Yes, the folder is accessible, but the information in it is encrypted and unreadable without the password. Try it and see. I did.

---

