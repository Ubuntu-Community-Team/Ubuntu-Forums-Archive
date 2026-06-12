---
title: "&quot;Make launcher&quot;-script"
date: 2011-04-23
forum: General Help
---

### Post by McCleod on 2011-04-23
I have no idea where to put my question.

I need a script that makes launcher objects of executables in a given directory.

Can anyone please help me out?

---

### Post by DeMus on 2011-04-23
> **McCleod said:**
> I have no idea where to put my question.

I need a script that makes launcher objects of executables in a given directory.

Can anyone please help me out?

Can you explain some more what it is you want to do? I'm not quite sure yet.

---

### Post by McCleod on 2011-04-23
> **DeMus said:**
> Can you explain some more what it is you want to do? I'm not quite sure yet.

I have a bunch og executable files in a directory. I would like to be able to execute them via icon objects on the Desktop. I could make the launchers by hand but it would take me forever...

I need a script that could fill in the right words at the right place in a .desktop-file and give the file a proper name according to the executable - and then go on to the next executable in line.

The following code is from the launcher "ufsxsci.desktop":


```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=UFS Explorer Standard Recovery
Comment=Data Recovery application for Linux
Exec=ufsxsci
Icon=ufsxsci.xpm
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;System;
StartupNotify=false
MimeType=application/x-ufsxsci
GenericName[en_GR]=
```

Maybe one should make a template and make the script fill the empty spaces or make the script create each line with the apropriate content. I don't know. I'm not a programmer.

---

