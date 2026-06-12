---
title: "Run Putty Command from Windows shortcut"
date: 2012-05-18
forum: General Help
---

### Post by JasonMarquez on 2012-05-18
I would like to make a shortcut on my Windows 7 desktop that will open putty and connect to a server and run a bash script. Is this possible? I would like to do this so I don't have to contentiously connect to the server and type in the command.

---

### Post by steeldriver on 2012-05-18
if you do the 'full' Windows install of puTTY it includes a commandline ssh tool called 'plink.exe' which you could put in a bat file, I would think

---

### Post by JasonMarquez on 2012-05-18
Perfect! I decided to make a batch file for this like you said. Problem I ran into is that it won't run the commands in putty :S

```

@echo off

echo ------------
echo 1 - Start Teamspeak
echo 2 - Stop Teamspeak
echo 3 - Start Minecraft
echo 4 - Stop Minecraft
echo 5 - Start Left4Dead
echo 6 - Stop Left4Dead
echo 7 - Start Vuze
echo 8 - Stop Vuze
echo ------------

Choice /C 12345678 /M "Choose an Option"
If Errorlevel 8 Goto 8
If Errorlevel 7 Goto 7
If Errorlevel 6 Goto 6
If Errorlevel 5 Goto 5
If Errorlevel 4 Goto 4
If Errorlevel 3 Goto 3
If Errorlevel 2 Goto 2
If Errorlevel 1 Goto 1

Goto End

:8
cls
echo "Stoping Vuze"
echo Not supported yet
Goto End

:7
cls
echo "Starting Vuze"
echo Not supported yet
Goto End

:6
cls
echo "Stopping Left4Dead"
echo Not supported yet
Goto End

:5
cls
echo "Starting Left4Dead"
cd C:\Program Files (x86)\PuTTY
putty.exe -ssh -load "Hamachi" -l jason -pw 9801634
sudo bash /home/jason/Desktop/left4dead.sh
Goto End

:4
cls
echo "Stopping Minecraft"
echo Not supported yet
Goto End

:3
cls
echo "Starting Minecraft"
cd C:\Program Files (x86)\PuTTY
putty.exe -ssh -load "Hamachi" -l jason -pw 9801634
sudo bash /home/jason/Desktop/minecraft.sh
Goto End

:2
cls
echo "Stopping Teamspeak"
cd C:\Program Files (x86)\PuTTY
putty.exe -ssh -load "Hamachi" -l jason -pw 9801634
sudo bash /home/jason/teamspeak3-server_linux-x86/ts3server_startscript.sh stop
Goto End

:1
cls
echo "Starting Teamspeak"
cd C:\Program Files (x86)\PuTTY
putty.exe -ssh -load "Hamachi" -l jason -pw 9801634
sudo bash /home/jason/teamspeak3-server_linux-x86/ts3server_startscript.sh start
Goto End

```

---

### Post by JasonMarquez on 2012-05-18
Fixed it

---

