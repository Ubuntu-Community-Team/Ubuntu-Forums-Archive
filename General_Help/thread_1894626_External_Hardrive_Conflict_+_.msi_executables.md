---
title: "External Hardrive Conflict + .msi executables"
date: 2011-12-13
forum: General Help
---

### Post by Fitmotanlamosko on 2011-12-13
Okay, so I'm trying to install steam for Ubuntu (I've read tuts on doing so), and I've been generally stumped on one particular area...

running the SteamInstaller.msi.

With that said, I've used msiexec /i SteamInstaller.msi, but...........

I get the message: err:msi:copy_package_to_temp failed to copy package L"fileinstaller.msi" to L"C:\\users\\ubuntu\\Temp\\msi6ac7.tmp" (2)

Obviously this is an issue, and I believe it could do with the fact that I'm running Ubuntu off an external usb drive, and perhaps it doesn't recognize that as C:


Info about the hardrive issue, and the Steaminstaller.msi issue would be much appreciated. 

-Fitmotanlamosko

---

### Post by oldtimer7777 on 2011-12-13
You can easily install Steam from within PlayOnLinux in Ubuntu:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/3rd the way down the new user checklist.  Works great on my Ubuntu system too. No issues. 

> **Fitmotanlamosko said:**
> Okay, so I'm trying to install steam for Ubuntu (I've read tuts on doing so), and I've been generally stumped on one particular area...

running the SteamInstaller.msi.

With that said, I've used msiexec /i SteamInstaller.msi, but...........

I get the message: err:msi:copy_package_to_temp failed to copy package L"fileinstaller.msi" to L"C:\\users\\ubuntu\\Temp\\msi6ac7.tmp" (2)

Obviously this is an issue, and I believe it could do with the fact that I'm running Ubuntu off an external usb drive, and perhaps it doesn't recognize that as C:


Info about the hardrive issue, and the Steaminstaller.msi issue would be much appreciated. 

-Fitmotanlamosko

---

### Post by Fitmotanlamosko on 2011-12-13
Quick response time, and helpful -- do I reward you with beans or something?

In other words, how do I exchange my thanks?

Also, does having an external usb hardrive have any negative effects as far as software goes?

---

### Post by oldtimer7777 on 2011-12-13
Good question. No, USBs don't work in Wine.  You can force it, and you will get corrupt data. I personally tried that about 3 years ago for the same purpose. It will work (kind-of) and really upset you when it messes up your Wine applications that access it and corrupt the USB external in the process.   Your external will read, and even write to itself occationally and the forced installation of USB in wine will probably ruin the external drive eventually/over time. 

It would be best to migrate your data into the native linux directory structure if you going to use Wine.  

Hey you are welcome too.  Don't forget to mark this thread solved by clicking on Thread Tools above. Don't forget to bookmark that link.

> **Fitmotanlamosko said:**
> Quick response time, and helpful -- do I reward you with beans or something?

In other words, how do I exchange my thanks?

Also, does having an external usb hardrive have any negative effects as far as software goes?

---

