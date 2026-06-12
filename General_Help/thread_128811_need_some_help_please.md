---
title: "need some help please"
date: 2006-02-12
forum: General Help
---

### Post by Fallen2 on 2006-02-12
I'm trying to install an .exe file but when I do I get this message through the terminal  **E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)**.  How do I fix that so uI can have permission?

---

### Post by kaamos on 2006-02-12
What are you trying to install? .exe sound pretty suspicious..

The error means that you have another application running that uses dpkg (like synaptic). Also everything that uses dpkg requires sudo (so "command" should be "sudo command").

---

### Post by Fallen2 on 2006-02-12
[QUOTE=kaamos]What are you trying to install? .exe sound pretty suspicious..

The error means that you have another application running that uses dpkg (like synaptic). Also everything that uses dpkg requires sudo (so "command" should be "sudo command").[/QUOTE]

Google Player.  So then what should I do?

---

### Post by kaamos on 2006-02-12
I think google has released their player only for windows. In general, .exe is a windows executable for a windows program. So as you can't install mac software in windows, you can't install windows software in linux.

The player could perhaps be made to run with an emulator or an app like wine. [http://www.winehq.com/](http://www.winehq.com/)

---

### Post by Fallen2 on 2006-02-12
[QUOTE=kaamos]I think google has released their player only for windows. In general, .exe is a windows executable for a windows program. So as you can't install mac software in windows, you can't install windows software in linux.

The player could perhaps be made to run with an emulator or an app like wine. [http://www.winehq.com/](http://www.winehq.com/)[/QUOTE]
That's what I'm trying to run it with.  but how do I install it using WINE?

---

### Post by kaamos on 2006-02-12
If you have not already added the wine repo and installed the newest wine, do it now. Open a terminal and type
```
sudo gedit /etc/apt/sources.list
```
Give your password, and a file opens in a text editor. Add this line to the end of the file
> deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
Save the file. Then give these commands in the terminal
```
sudo apt-get update
sudo apt-get install wine
```
Now wine is installed.

For installing the player, use the command "wine" for the installer. Like
```
wine google_player_install.exe
```

---

### Post by Fallen2 on 2006-02-12
[QUOTE=kaamos]If you have not already added the wine repo and installed the newest wine, do it now. Open a terminal and type
```
sudo gedit /etc/apt/sources.list
```
Give your password, and a file opens in a text editor. Add this line to the end of the file

Save the file. Then give these commands in the terminal
```
sudo apt-get update
sudo apt-get install wine
```
Now wine is installed.

For installing the player, use the command "wine" for the installer. Like
```
wine google_player_install.exe
```[/QUOTE]
None of the installation works.  I downloaded LimeWire and the file on the desktop reads **LimeWireWin.exe**, now how do I install that using WINE?  I tried doing it like you said but I had no luck.

---

### Post by kaamos on 2006-02-12
1) I think that Limewire has a native linux client so no need to use wine
2) A better alternative would be frostwire as it is open source. You can install it by downloading this: [http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.5-0.i586.deb?download](http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.5-0.i586.deb?download)
and then
```
sudo dpkg -i FrostWire-4.10.5-0.i586.deb
```
Both probably need java so search the ubuntu wiki how to install that.

---

