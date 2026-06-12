---
title: "Wine Ubuntu install error!"
date: 2011-05-09
forum: General Help
---

### Post by projectfox on 2011-05-09
I'm trying to setup Baldur's Gate in Wine and it's giving me this error: "There is no Windows program configured to run that type of file"

I've enabled the file to be allowed to run as an executable, and the program is completely uncorrupted - i just installed it on another computer with Windows.

Any suggestions?

---

### Post by 3 frags left on 2011-05-09
> You need to copy netapi32.dll from Windows XP to ~/.wine/drive_c/windows/system32/ and use in winecfg. After that, installation will start.

Sauce:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12261](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12261)
All of the versions worked platinum.

---

### Post by projectfox on 2011-05-09
I've copied an uncorrupted netapi32.dll from Windows XP into the /system32 folder in the '.wine' directory but i'm still getting the same error.

I've enabled the .dll in the wine configuration.

Any suggestions?

---

### Post by 3 frags left on 2011-05-10
> **projectfox said:**
> I've copied an uncorrupted netapi32.dll from Windows XP into the /system32 folder in the '.wine' directory but i'm still getting the same error.

I've enabled the .dll in the wine configuration.

Any suggestions?
You ought to try installing it in a Virtual Machine, then copying all the files to your drive_c folder. Don't forget the registry!

---

