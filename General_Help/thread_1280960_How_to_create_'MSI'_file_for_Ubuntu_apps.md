---
title: "How to create 'MSI' file for Ubuntu apps?"
date: 2009-10-02
forum: General Help
---

### Post by blurboy on 2009-10-02
I've just developed an application. Is there any 'MSI' file for distributing Ubuntu applications? (Package?)
 
I would like to create a setup file so that the user will just have to click 'next' 'next' and 'next' to install the application.

---

### Post by falconindy on 2009-10-02
.deb is the equivalent type of packaging. Linux apps don't usually do graphical installs, though. Everything is predetermined and/or overridden with flags at runtime.

dpkg -i mypackage.deb

..and everything goes to the right place. See [this thread](http://ubuntuforums.org/showthread.php?t=910717) for details on how to make a basic .deb file.

---

### Post by blurboy on 2009-10-02
thanks! i will try it out

---

### Post by blurboy on 2009-10-02
EXACTLY what i was looking for! THANKS!

---

### Post by blurboy on 2009-10-10
mkdir helloworld_1.0-1/usr
mkdir helloworld_1.0-1/usr/local
mkdir helloworld_1.0-1/usr/local/bin
cp "~/Projects/Hello World/helloworld" helloworld_1.0-1/usr/local/bin

How can i install the files in a folder onto Desktop? the user name is different for every computer...

---

### Post by akakingess on 2009-10-10
> **blurboy said:**
> mkdir helloworld_1.0-1/usr
mkdir helloworld_1.0-1/usr/local
mkdir helloworld_1.0-1/usr/local/bin
cp "~/Projects/Hello World/helloworld" helloworld_1.0-1/usr/local/bin

How can i install the files in a folder onto Desktop? the user name is different for every computer...

Not an expert, but could you use just " ~/Desktop "?

---

### Post by blurboy on 2009-10-10
sorry i dont get what you mean..

~/Desktop?

Do I create a foler named "~" and then a Desktop folder inside it?

I tried and it didn't work.. it created the folder "~" on client PC when i installed it.

How can i set a folder name to be dynamic to get the user's name?

---

### Post by lisati on 2009-10-10
> **blurboy said:**
> sorry i dont get what you mean..

~/Desktop?

Do I create a foler named "~" and then a Desktop folder inside it?

I tried and it didn't work.. it created the folder "~" on client PC when i installed it.

How can i set a folder name to be dynamic to get the user's name?

Not quite: "~" is like shorthand the current user's home directory and "~/Desktop" always points to the current user's desktop.

---

### Post by blurboy on 2009-10-10
so base on dgkp how can I create a package so that when user double clicks on it, it will unpack all the files onto the CURRENT USER desktop??

---

