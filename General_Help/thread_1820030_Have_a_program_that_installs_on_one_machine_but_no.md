---
title: "Have a program that installs on one machine but not on another ..."
date: 2011-08-07
forum: General Help
---

### Post by ahmadka on 2011-08-07
I'm trying to install the Unix version of Rapidshare manager on an Ubuntu VPS I have .. The  installation script is this: [https://www.rapidshare.com/files/450240029/rsm2_linux.sh](https://www.rapidshare.com/files/450240029/rsm2_linux.sh)

I have two Ubuntu VPS machines .. On the first one, after chmod'ing the program installs fine, however on this other VPS, after chmod'ing and running the script I get this error:

```
Starting Installer ...
Xlib: extension "RANDR" missing on display ":1.0".
Could not deteremine disk space: Cannot run program "df": java.io.IOException: error=12, Cannot allocate memory
```

The the installer's GUI comes up, I go through the program, and although it says that its installed, its really not ..

Also, 'df' command runs fine on this Ubuntu VPS, and shows tons of available disk space, so I don't know what's the problem .. :/

---

### Post by ahmadka on 2011-08-08
Can someone help me here please ?? :(

---

### Post by blueridgedog on 2011-08-08
Are the two xorg.conf files identical?

---

