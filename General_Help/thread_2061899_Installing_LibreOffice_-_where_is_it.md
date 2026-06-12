---
title: "Installing LibreOffice - where is it?"
date: 2012-09-23
forum: General Help
---

### Post by jamieE on 2012-09-23
I installed Ubuntu 12.04 32-bit on a Windows 7 VM (using VMPlayer).

That went fine, but I'm having a hard time installing the latest version of LibreOffice. I noticed that Ubuntu was running LO 3.4, and I want to run 3.6. 

I uninstalled LO through the Software Center, and then downloaded the 3.6 files from LO and installed those using the README instructions.

After doing that, I couldn't find LO, and it didn't appear to be in the Software Center.

So, I found some other instructions online and did this:

sudo add-apt-repository ppa:libreoffice/libreoffice-prereleases
sudo apt-get update && sudo apt-get dist-upgrade

Those commands completed successfully, but again, I don't see that LO is installed anywhere.  If I run this:

sudo apt-get install libreoffice

It says, "LibreOffice is already the newest version."

I'm sure I'm missing something obvious.

Thanks.

---

### Post by Dennis N on 2012-09-23
Just type libreoffice in the Dash search bar and the libreoffice icons will show up. Click on an icon and it will start that application. 

Help > About will give you the version.

---

### Post by MutantJohn on 2012-09-23
I know this is of no aid to the OP but adding the ppa and upgrading worked for me so I must say thank you, OP, thank you.

---

### Post by claracc on 2012-09-24
> **jamieE said:**
> I installed Ubuntu 12.04 32-bit on a Windows 7 VM (using VMPlayer).

That went fine, but I'm having a hard time installing the latest version of LibreOffice. I noticed that Ubuntu was running LO 3.4, and I want to run 3.6. 

I uninstalled LO through the Software Center, and then downloaded the 3.6 files from LO and installed those using the README instructions.

After doing that, I couldn't find LO, and it didn't appear to be in the Software Center.

So, I found some other instructions online and did this:

sudo add-apt-repository ppa:libreoffice/libreoffice-prereleases
sudo apt-get update && sudo apt-get dist-upgrade

Those commands completed successfully, but again, I don't see that LO is installed anywhere.  If I run this:

sudo apt-get install libreoffice

It says, "LibreOffice is already the newest version."

I'm sure I'm missing something obvious.

Thanks.

It seems you have just installed libreoffice, so you have to uninstall libreoffice again .

I think you can run in a xterm:

sudo apt-get remove --purge libreoffice-core 

[http://ubuntuforums.org/showthread.php?t=1945019](http://ubuntuforums.org/showthread.php?t=1945019)

And as you have installed the ppa for the last libreoffice, simply run again in xterm: sudo apt-get update

---

### Post by Peter Maunder on 2012-09-24
I have both LibreOffice 3.5 and 3.6 installed on my 12.04 system. I installed 3.6 directly from the LibO site. The two packages are installed in the 

  /opt/libreoffice 3.5 and /opt/libreoffice 3.6 folders.

On the software centre the only entries on my machine are shown when I type
   libreoffice 3.6
typing libreoffice or libreoffice 3.5 does not show any installed packages. A design feature / error ?

synaptic shows all the installed packages under libreoffice and the relevant packages under libreoffice 3.5 or libreoffice 3.6.

When launching a package make certain that the properties point to the correct version. if you have two versions installed.

---

