---
title: "extracting .exe files"
date: 2012-06-19
forum: General Help
---

### Post by soulresonence on 2012-06-19
Hi
I'm trying to sort out some wifi issues on my laptop. I've managed to download the windows drivers for the hardware from which I believe I need to extract .inf .sys and .bin files. I've been unable to do this using archive manager on ubuntu or using universal extractor on a win7 machine. Archive manager doesn't recognise the .exe file and win7 has issuses with the driver being a XP or vista driver. 
Any help would be greatley appreciated

---

### Post by kanikilu on 2012-06-19
**If** it's a self-extracting exe archive (which all aren't), 7zip should be able to do it:

```
sudo apt-get install p7zip-rar
7z e filename.exe
```

If it's not an archive, you could try opening it with wine, but that may not work either...

---

### Post by cortman on 2012-06-19
You do know that Windows drivers will not work in Ubuntu?

---

### Post by qamelian on 2012-06-19
> **cortman said:**
> You do know that Windows drivers will not work in Ubuntu?
They actually might if the OP is trying to use ndiswrapper. For many of us, that was the only way to get wireless working at all a few years ago. The ndiswrapper tool requires you to have the necessary files extracted from the Windows installer as it uses the inf file to load the drivers.

---

### Post by kanikilu on 2012-06-19
> **cortman said:**
> You do know that Windows drivers will not work in Ubuntu? Could be that OP is trying to use ndiswrapper?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Windows_driver](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Windows_driver)

//edit: too slow :)

---

### Post by uylug on 2012-06-19
Exactly, that's what I guess. Ndiswrapper has worked excellent for me in the past. All you need is the right drivers making sure that they match your architecture as well.

---

### Post by soulresonence on 2012-06-20
@[kanikilu]("http://ubuntuforums.org/member.php?u=87527"),
Thanks I'll give the code a try.
 Thanks for your replys

---

### Post by soulresonence on 2012-06-20
Oh and yes, I'm using ndiswrapper!

---

### Post by soulresonence on 2012-06-20
> **kanikilu said:**
> **If** it's a self-extracting exe archive (which all aren't), 7zip should be able to do it:
 
```
sudo apt-get install p7zip-rar
7z e filename.exe
```
 
If it's not an archive, you could try opening it with wine, but that may not work either...
 
OK I've tried the code and after entering the first line it asks for my password but nothing can be entered in the terminal, if you type noting appears, the cursor doesn't move.
 
I tried opening the driver with wine again; For a few seconds an icon appears that looks like a stylised WiFi icon from the desktop bar and some green dots in a circle around it appear to count down then it dissapears. I know the driver isn't running because the WiFi keeps stopping then disconnecting.
 
Tried going through Administration>windows wireless drivers but comes up as an invalid driver when added to the list.

---

### Post by qamelian on 2012-06-20
Nothing is supposed to appear. Just type in the password and hit Enter. The password is supposed to be "invisible" when respomnding to sudo in a terminal.

---

### Post by soulresonence on 2012-06-20
Thanks,
When I enter the second line of command get
 
Error:
ther is no such archive
 
Does the driver need to be in a specific location?

---

### Post by kanikilu on 2012-06-20
> **soulresonence said:**
> Thanks,
When I enter the second line of command get
 
Error:
ther is no such archive
 
Does the driver need to be in a specific location? Were you in the same directory as the .exe file, and did you use the correct file name? Can you copy & paste the terminal output here?

---

### Post by Mark Phelps on 2012-06-21
Sorry, but some .exe files are executables, not self-extracting archives.  HP is infamous for doing just that with recent printer drivers.

---

### Post by soulresonence on 2012-06-22
sorry for my late response, pasted my terminal output here after entering the commands you gave


gareth@gareth-laptop:~$ sudo apt-get install p7zip-rar
[sudo] password for gareth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
p7zip-rar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
gareth@gareth-laptop:~$ 7z e Wireless_15.1.1_dx32.exe

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.utf8,Utf16=on,HugeFiles=on,2 CPUs)


Error:
there is no such archive
gareth@gareth-laptop:~$ 


I'm the only user on this laptop and the driver is on the dektop. Will I have to sort out permissions, I've been reading about it and and not quite there with that yet!

---

### Post by kanikilu on 2012-06-22
> **soulresonence said:**
> Error:
there is no such archive
gareth@gareth-laptop:~$

I'm the only user on this laptop and the driver is on the dektop. Will I have to sort out permissions, I've been reading about it and and not quite there with that yet! If the driver is on your desktop, than you need to change to that directory first. It also doesn't hurt to create a temp "container" directory to extract to. Open a terminal, and then do: ```
cd ~/Desktop
mkdir driver/
mv Wireless_15.1.1_dx32.exe driver/
cd driver/
7z e Wireless_15.1.1_dx32.exe
```

Although, out of curiosity, I googled the driver name you have and downloaded it. When I tried to extract it with 7zip, it didn't give errors, but I also don't see any usable files, like an .inf file, sorry.

---

### Post by kanikilu on 2012-06-22
Sent you a PM...

---

