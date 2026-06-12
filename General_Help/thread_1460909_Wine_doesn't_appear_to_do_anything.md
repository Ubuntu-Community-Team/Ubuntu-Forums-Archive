---
title: "Wine doesn't appear to do anything"
date: 2010-04-23
forum: General Help
---

### Post by OriTheEep on 2010-04-23
I've been a 123 user since version 2 and subsequently a user of Smartsuite. There doesn't seem to be any Linux app which will run lotus files, although open office will (sort of) read them.

So, I reluctantly conclude, I need to be able to install and run Smartsuite in some way inside Ubuntu. I decide to try Wine, install it via the Software Centre and then find that it doesn't do anything. It won't even launch it's own Notepad application.

An, admittedly brief, trawl does not show anyone else having had a similar problem fixed. Can anyone, please, help?

Thanks :)

---

### Post by tgm4883 on 2010-04-23
Have you tried right clicking on the setup.exe (or similarly named file) for Smartsuite and selecting to open with Wine

---

### Post by OriTheEep on 2010-04-23
> **tgm4883 said:**
> Have you tried right clicking on the setup.exe (or similarly named file) for Smartsuite and selecting to open with Wine

Nothing happens when I do :(

---

### Post by Monotoko on 2010-04-23
If wine doesn't work, try something stronger (this works in both ways you could take that term)

Run it in a VM :)

---

### Post by dearingj on 2010-04-23
Did you reboot or log out after installing wine? I've sometimes found it to be unresponsive right after installation; logging out and in again fixes that.

---

### Post by kanikilu on 2010-04-23
> **OriTheEep said:**
> Nothing happens when I do :(

Try:

- Open a terminal (Applications > Accessories > Terminal)
- Type:

wine ~/.wine/drive_c/windows/notepad.exe

Any errors should show up in there...

---

### Post by Finalfantasykid on 2010-04-23
Try running the program in a terminal.

```
wine setup.exe
```

Maybe you will get some 'informative' error message.

---

### Post by OriTheEep on 2010-04-23
> **Monotoko said:**
> If wine doesn't work, try something stronger (this works in both ways you could take that term)

Run it in a VM :)

I haven't investigated that option yet but wouldn't it involve installing Windows? The only legit copy I have is 98SEII which I doubt will see the SATA drives on this machine. I certainly have no intention of shelling out more dosh to µsoft for something that is unlikely to perform to expectation. I've done that too many times over the years.

---

### Post by OriTheEep on 2010-04-23
> **dearingj said:**
> Did you reboot or log out after installing wine? I've sometimes found it to be unresponsive right after installation; logging out and in again fixes that.

I take time to do things. I installed Wine some time ago and then got involved with something else. When I tried to install Smartsuite or do anything else with it with no response my first thought was to uninstall then attempt a re-installation. I have no idea how thorough the uninstallation is but it didn't change anything.

---

### Post by OriTheEep on 2010-04-23
> **kanikilu said:**
> Try:

- Open a terminal (Applications > Accessories > Terminal)
- Type:

wine ~/.wine/drive_c/windows/notepad.exe

Any errors should show up in there...

That has thrown something up:

tom@server:~$ wine ~/.wine/drive_c/windows/notepad.exe
wine: cannot find '/home/tom/.wine/drive_c/windows/notepad.exe'
tom@server:~$ 

I have confirmed the absence of notepad.exe with Nautilus.

Why it is not there, given that I uninstalled/installed it just recently in case it had fallen victim to random deletion or similar, I cannot say.

---

### Post by OriTheEep on 2010-04-23
> **Finalfantasykid said:**
> Try running the program in a terminal.

```
wine setup.exe
```Maybe you will get some 'informative' error message.

Pure Hellenic to me but perhaps more meaningful to an expert:


tom@server:~$ wine /media/cdrom0/setup.exe
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  76
  Current serial number in output stream:  76
tom@server:~$

---

### Post by OriTheEep on 2010-04-24
Here: [http://ohioloco.ubuntuforums.org/showthread.php?p=9011424](http://ohioloco.ubuntuforums.org/showthread.php?p=9011424)

Huge thanks to everyone who dropped in with a suggestion. :)

Wine is now working. Unfortunately the Lotus install failed on the first attempt. I'm going to play with the cat for a bit then try again.

---

