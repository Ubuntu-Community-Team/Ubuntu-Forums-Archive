---
title: "can't install flash-please help"
date: 2012-05-23
forum: General Help
---

### Post by mejbr2003 on 2012-05-23
I just installed a fresh 12.04
I'm not to linux-wise and can't seen to get flash to work
can anyone walk me though it or any good ideas?
I've downloaded the targz and the rpm and cant seem to do a thing with them
I've followed some web advice, no luck
thanks for any and all help

---

### Post by MG&amp;TL on 2012-05-23
.tar.gz and .rpm are not ubuntu packages.

Get "flashplugin-installer" from the software centre, or open a terminal and type:

```
sudo apt-get install flashplugin-installer
```

---

### Post by sikander3786 on 2012-05-23
The easiest and the best method for having the latest Flash is to use flash-aid Firefox add-on:

[http://www.tuxgarage.com/2011/05/manage-your-flash-plug-ins-by-using.html](http://www.tuxgarage.com/2011/05/manage-your-flash-plug-ins-by-using.html)

If you want to install it from the repositories, press 'Ctrl + Alt + T' and in the 'Terminal' that opens up, run:

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by MadmanRB on 2012-05-23
You dont install them like you do in windows, there is a thing called the Ubuntu software center its in your sidebar.
open it up and seartch for ubuntu restricted extras and flash and the like will be installed.
The only time you should install from a website is with say installing google chrome and use a .deb installer for your system for that one as its not in the software center.
Dont dig into command line unless you have to

---

