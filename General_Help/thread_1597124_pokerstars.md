---
title: "pokerstars"
date: 2010-10-14
forum: General Help
---

### Post by w0wz3rz on 2010-10-14
noob here...i've tried the couple quick fix commands(detailed here [http://ubuntuforums.org/showthread.php?t=1569849&highlight=pokerstars](http://ubuntuforums.org/showthread.php?t=1569849&highlight=pokerstars)) and i get an error message:

"unable to set CAP_SETFCAP effective capability: Operation not permitted"

anyone know what i should do to get pokerstars working :confused:

thanks

---

### Post by Quackers on 2010-10-15
Welcome to ubuntuforums :-)
You need to put sudo before the setcap commands. You may get an error that setcap can't be used until you install something else. The necessary command is given in the error message.
You will also need to mark the Pokerstars.exe (or it's shortcut) as executable. (Right-click on the file and select Properties then Permissions and check the box.

---

### Post by w0wz3rz on 2010-10-15
thanks man, that fixed it. :guitar: i shouldve known sudo was missing, derp!

---

### Post by Quackers on 2010-10-15
Lol, I did the same thing first time following the guide :-)  Then I realised, doh!
Glad it helped a fellow Pokerstars player :-)

---

