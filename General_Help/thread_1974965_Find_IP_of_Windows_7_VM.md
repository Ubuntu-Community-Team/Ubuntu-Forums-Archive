---
title: "Find IP of Windows 7 VM"
date: 2012-05-06
forum: General Help
---

### Post by marshall1001 on 2012-05-06
Hi, I have a Windows 7 VM that I'm trying to run a Tekkit 2.1.1 server (Minecraft) on. I can't run it on my host as I'm on 11.04 and can't really get Java 7 to play nice.

Anyway, the console in my Windows 7 virtual machine says that the Tekkit server is all fine and dandy, whilst the result of ipconfig gives me 10.0.2.15.

I'm trying to connect to the machine inside Ubuntu but the Tekkit Launcher keeps polling the server and saying it can't find it almost instantaneously.

I've very little knowledge on how Virtual Networking is done so any help would be greatly appreciated ^_^ Cheers.

---

### Post by jerome1232 on 2012-05-06
Go into the settings of the virtual machine, change the adapter to bridged mode so that it gets an ip that's actually on your LAN. Should be fine from there.

---

