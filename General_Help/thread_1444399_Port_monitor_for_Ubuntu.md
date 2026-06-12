---
title: "Port monitor for Ubuntu"
date: 2010-04-01
forum: General Help
---

### Post by forcecore on 2010-04-01
is there some simple port monitor like [**this**]("http://technet.microsoft.com/en-us/sysinternals/bb896644.aspx") that do not require tons of dependencies?

---

### Post by 3rdalbum on 2010-04-01
lsof, or ntop (although ntop will probably bring in a lot of dependencies).

---

### Post by forcecore on 2010-04-01
oh sorry i forgot to mention that GUI based..

ntop is quite big for light integration in UCK

---

### Post by pastalavista on 2010-04-01
In terminal ```
netstat
``` lots of ways to use it ```
man netstat
``` and it's already built in

---

### Post by Jive Turkey on 2010-04-01
The gui based tool for this is called gnome-terminal.  Go to Applications > Accesories > Terminal.  This will bring up a powerful gui interface where you can enter commands to accomplish just about anything you can think of.

Try typing "apropos port" into the graphical interface and you will be presented with about a hundred different possible commands and short descriptions of them, some of which are related to what you are looking for.

---

### Post by forcecore on 2010-04-01
did not find any good way with apropos port, there should be some GUI for port monitoring like this is for Win:
[IMG]http://www.nirsoft.net/utils/cports.gif[/IMG]

---

### Post by forcecore on 2010-04-02
bump, maybe someone sees who knows such tool...

---

### Post by Sin@Sin-Sacrifice on 2010-04-02
There's a bunch of tutorials and information on network security in the networking and wireless section of the forums. Go check it out.

---

### Post by Ancanus on 2010-04-02
None that I know of.
My guess is that if you are at a level where you mind what your ports are up to, you are at a level where you don't mind using the terminal.

---

### Post by forcecore on 2010-04-06
I let everyone know i found miracle tool that is like Everest on windows: hardinfo, it do not require extra masses of dependencies and shows lot of information including ports.

[HardInfo]("http://hardinfo.berlios.de/Screenshots")

---

