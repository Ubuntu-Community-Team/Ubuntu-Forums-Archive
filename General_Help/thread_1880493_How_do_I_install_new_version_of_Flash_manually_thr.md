---
title: "How do I install new version of Flash manually through terminal?"
date: 2011-11-13
forum: General Help
---

### Post by iridemybike on 2011-11-13
I'm new to Ubuntu in general and running 11.10. I'm trying to manually update Flash to the newest version. I went to the adobe site and downloaded the correct version for Linux there doesn't seem to be a way to install through gui so I figured there must be a way to install through terminal(seems to be a way for most everything else) but I'm new and don't know the terminal commands very well...er...at all! Can somebody help me out with this?

---

### Post by Derek Karpinski on 2011-11-14
Install 'flash-aid' in firefox.

If you're interested in the script, there is an option to export the script that flash-aid creates.

---

### Post by iridemybike on 2011-11-14
Installed flash-aid...pretty much every wizard and advanced manual combination I could find didn't get flash working at all. I temporarily went back to the "Adobe Flash Plugin 10" in the software center that gets flash working for the most part. I still can't get the chat window in gmail to ding like it's supposed to though. I figured it was probably a flash issue but since I can't seem to get flash player 11 installed I may never know.

---

### Post by eltonw on 2011-11-14
**[COLOR=Sienna]GDebi[/COLOR] Package Installer** is a utility that would have been installed by default on your ubuntu system. It's the GUI version for installing debian packages. OR _from the console_ use *either* of these commands:
sudo **dpkg** -i *packagename* sudo **dpkg** --install [I]packagename

[/I]HOWEVER,[I]
[COLOR=DarkRed]If you open the [/COLOR][/I][COLOR=DarkRed]_Ubuntu Software Center_[/COLOR]*[COLOR=DarkRed] (or have installed [/COLOR]*[COLOR=DarkRed]**Synaptic**[/COLOR][I][COLOR=DarkRed]), you would simply [COLOR=Black]do a search for 'flash'[/COLOR] and install with either utility.[/COLOR]
[/I]

---

### Post by philinux on 2011-11-14
> **iridemybike said:**
> I'm new to Ubuntu in general and running 11.10. I'm trying to manually update Flash to the newest version. I went to the adobe site and downloaded the correct version for Linux there doesn't seem to be a way to install through gui so I figured there must be a way to install through terminal(seems to be a way for most everything else) but I'm new and don't know the terminal commands very well...er...at all! Can somebody help me out with this?

Is this a 64 bit install?

---

### Post by philinux on 2011-11-14
> **eltonw said:**
> **[COLOR=Sienna]GDebi[/COLOR] Package Installer** is a utility that would have been installed by default on your ubuntu system. It's the GUI version for installing debian packages. OR _from the console_ use *either* of these commands:
sudo **dpkg** -i *packagename* sudo **dpkg** --install *packagename *

On 11.10 gdebi is now not installed by default. A deb package would get picked up and installed by the software centre instead.

---

### Post by iridemybike on 2011-11-14
It's a 32bit install. I picked up gdebi from the software center but not really sure what to do with it. I have the tar.gz version of flash 11 for linux from the adobe site and the extracted folder. Not really sure where I'm going with it from there. What would be the package name for it? The zipped version is "install_flash_player_11_linux.i386.tar.gz" it unpacks to a folder with the name name minus the "tar.gz".

---

### Post by iridemybike on 2011-11-14
> **eltonw said:**
> **[COLOR=Sienna][/COLOR]**HOWEVER,[I]
[COLOR=DarkRed]If you open the [/COLOR][/I][COLOR=DarkRed]_Ubuntu Software Center_[/COLOR]*[COLOR=DarkRed] (or have installed [/COLOR]*[COLOR=DarkRed]**Synaptic**[/COLOR][I][COLOR=DarkRed]), you would simply [COLOR=Black]do a search for 'flash'[/COLOR] and install with either utility.[/COLOR]
[/I]

Yeah, I have the version of flash from the software center, actually I've tried both plugins, most flash things seem to work but not everything does so I was hoping the latest official version would solve the issue.

---

### Post by nothingspecial on 2011-11-14
Is there a README file inside the extracted folder?

---

### Post by philinux on 2011-11-14
> **iridemybike said:**
> It's a 32bit install. I picked up gdebi from the software center but not really sure what to do with it. I have the tar.gz version of flash 11 for linux from the adobe site and the extracted folder. Not really sure where I'm going with it from there. What would be the package name for it? The zipped version is "install_flash_player_11_linux.i386.tar.gz" it unpacks to a folder with the name name minus the "tar.gz".

You right click the tar file and choose extract here.

In the folder that gets extract you'll find libflashplayer.so

This needs to be copied to .mozilla/plugins in your home folder.

You will need to creat the plugins folder.

---

### Post by iridemybike on 2011-11-14
No ReadMe anywhere in it. I tried copying the .so file...not sure if it's actually working though. Any way to test what version it's actually using? Also seems to be more than one .so file. There is an "libflashplayer.so" and an "kcm_adobe_flash_player.so".

---

### Post by nothingspecial on 2011-11-14
See post below my last and above yours :)

---

### Post by iridemybike on 2011-11-14
Ah, sorry, dunno how I missed that line! So I got that going and flash seems to be working at least as well as it was before, is there any way to test or see which version of flash is running?

---

### Post by philinux on 2011-11-14
> **iridemybike said:**
> Ah, sorry, dunno how I missed that line! So I got that going and flash seems to be working at least as well as it was before, is there any way to test or see which version of flash is running?

Make sure to restart FireFox. Then right click on any flash vid

---

### Post by iridemybike on 2011-11-14
Got it, Using flash 11.1 now, thanks guys!! I'm learning this stuff, little by little, I keep reading on here though!

---

