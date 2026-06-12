---
title: "Where do program files go?"
date: 2010-10-25
forum: General Help
---

### Post by Jetso on 2010-10-25
When you use Synaptic or the software center, or a .deb to install something, where do all of that programs files go. For example, in Windows they go to C:/Program Files.

---

### Post by cgroza on 2010-10-25
It depends. They may be going to /opt/, /usr/ /bin/. Most of them go to /usr/bin.

---

### Post by lykwydchykyn on 2010-10-25
It's different in Linux; the files don't all go to the same place.  

The executable for the program goes usually goes to /usr/bin/
The configuration settings to /etc
The program data goes to /usr/share
Library files to /usr/lib
Launcher files (shortcuts) to /usr/share/applications/

and so on.

If you want to see what files are contained in the .deb file, look at the package properties in Synaptic and go to the "installed files" tab.  Or at the command line do:
```

dpkg -L packagename

```

More information on the structure of the filesystem can be found here:
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by sikander3786 on 2010-10-25
You can also search for them from terminal using whereis command e.g,

```
whereis firefox
```

---

### Post by xircon on 2010-10-25
Or:
```
which firefox
```

---

### Post by AlphaLexman on 2010-10-25
The command:
```
whereis
```
Will give all instances of the binary file, whereas:
```
which
```
Will tell you which one is the default.

---

