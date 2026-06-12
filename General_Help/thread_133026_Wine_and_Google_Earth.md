---
title: "Wine and Google Earth"
date: 2006-02-19
forum: General Help
---

### Post by cbudden on 2006-02-19
Hello.

I have Picasa and Google Earth working in wine, Picasa flawlessly and Earth with a couple of hitches.  When I use Earth I want to be able to use the "virtual desktop" feature of wine, but not with Picasa.  Is there a way of controlling it per application with a command line argument?  Also, with Earth when it starts, the main window is quite small and needs resizing, which I do.  When I close and open the program again the window is back to it's small size.  How can I fix this?


Thanks for your help.

---

### Post by nalmeth on 2006-02-19
All i can think of is running winecfg, maybe you can make some settings individually for each app

---

### Post by cbudden on 2006-02-19
Ah ha.  I didn't realise that as well as defining the OS a application uses, you can define everything else aswell.  I added earth to the application list on the first winecfg screen and changed that to virtual desktop, and changing default back to normal.  Thanks.

---

### Post by emuman on 2006-02-20
Which wine version runs Google Earth?

---

### Post by cbudden on 2006-02-20
I know 0.9.8 does with a couple of tweaks.  Howto is here - [https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29%7C%28earth%29](https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29%7C%28earth%29)

---

### Post by Kensey on 2006-02-22
I have been trying to get Google Earth running under Wine for a couple of days now.  I think the first problem is when I install DCOM98.  The installer starts and appears to copy files (the progress bar runs, at least) but as it exits the following errors pop up on the controlling terminal window:

kensey@azazel:~$ wine DCOM98.EXE
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\install.exe" -> "c:\\windows\\system\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\system\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\eula98.txt" -> "c:\\windows\\system\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\relnt98.txt" -> "c:\\windows\\system\\dcom98\\relnotes.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\inf\\dcom98.inf"

I have properly set the Windows version in Wine to Windows 98.  How do I get past this?  I have Wine 0.9.8 from the Wine HQ repository.

---

### Post by muted on 2006-03-13
[QUOTE=Kensey]I have been trying to get Google Earth running under Wine for a couple of days now.  I think the first problem is when I install DCOM98.  The installer starts and appears to copy files (the progress bar runs, at least) but as it exits the following errors pop up on the controlling terminal window:

kensey@azazel:~$ wine DCOM98.EXE
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\install.exe" -> "c:\\windows\\system\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\system\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\eula98.txt" -> "c:\\windows\\system\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\relnt98.txt" -> "c:\\windows\\system\\dcom98\\relnotes.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\inf\\dcom98.inf"

I have properly set the Windows version in Wine to Windows 98.  How do I get past this?  I have Wine 0.9.8 from the Wine HQ repository.[/QUOTE]at first i forgot to set the version in winecfg to win98, and that made it work.... later (since something else went wrong) i went back and tried setting the version to win98 and it gave the same error you are seeing, so...

Put it back on autodetect or winXP and i think it will work

EDIT: Wait, nope, I get the same no matter what. Never mind...

Help anyone?

---

