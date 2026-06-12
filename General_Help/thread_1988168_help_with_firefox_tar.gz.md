---
title: "help with firefox tar.gz"
date: 2012-05-27
forum: General Help
---

### Post by realflow100 on 2012-05-27
what the crap do i do with tar.gz files i just want to install them! using the latest version of ubuntu i dont want to use a terminal i just want to do something as simple as clicking the install button its riduculous!! i dont even try using terminals i just want to install the program!! i extracted the software firefox 3.0 to a folder i see a bunch of files inside the folder and a few more folders in there but there is nothing to execute! i just want to open or install the darn program! HELP!!!

---

### Post by Vaphell on 2012-05-27
if you want to do something as simple as clicking, why do you download an archive (.tar.gz) with the source code? You should be looking for .deb file (which is an equivalent of .msi or setup.exe in linux distros derived from debian) or for a 3rd party repository (ppa - personal package archive) that would add the packages to the list in software center.

always go along this path and move further if you can't find what you need
official repos > ppa > deb > source

besides, why do you need firefox 3.0? it's ancient (considering how fast the web standards evolve).

---

### Post by 3rdalbum on 2012-05-27
Welcome to Linux. You actually seem to be in a bit of a Windows mindset here, so let me help you out.

On Linux, we don't download programs using our web browsers. Instead we use the package manager that's available on our system. On Ubuntu, your package manager is Ubuntu Software Center. If you look in that program, you'll find that Firefox 11 is available to download and install with just one click. In fact, Firefox 11 is already installed on Ubuntu.

If the package manager doesn't have the program you want, then you need to find another "repository" or "PPA" that contains the program you want. Doing a quick search for "<programname> PPA" should help; then you just copy and paste two quick terminal commands to add the repository/PPA to your system so you can install the program. You can do this with the GUI as well, actually, but it's a lot quicker just to copy and paste it into the terminal.

If there's no repository or PPA, you need to find a .deb package for the program you want. It's getting rare these days to find a .deb and NOT a PPA, but you might still find a few examples out there. To install a .deb, just double-click it and click the "install" button.

Tarballs, such as the one you've downloaded, usually contain only the source code for the program. You don't want a tarball if you can avoid it as they're not usually for end-users.

Mozilla programs, such as Firefox, actually have precompiled programs in their tarballs. Inside the tarball that you've just decompressed, you'll find a file that simply says "firefox". Drag this to a terminal window and it will run. Note: It will not install, it will simply run in-place.

It hasn't escaped my attention that you're trying to use Firefox 3 - a very old version of Firefox. Basically, don't do this. I'm not even sure that such an old version will still run on modern Linux, but if it does it will not have had security patches for years. Why bother when you have Firefox 11 already?

---

### Post by Jimmyfj on 2012-05-27
I'm on Ubuntu 12.04 and have Firefox 12 installed. Why the need for Firefox 3 ?

---

### Post by oldos2er on 2012-05-27
Changed thread title to something more appropriate.

---

### Post by Frogs Hair on 2012-05-27
[http://www.mozilla.org/security/known-vulnerabilities/firefox30.html](http://www.mozilla.org/security/known-vulnerabilities/firefox30.html)

---

### Post by realflow100 on 2012-05-27
i want firefox 3 because no other version supports feather_beta on youtube and my computer lags without using feather_beta i finally got firefox 3 working  but now i cant seem to figure out how to get flash player 9 to work on it or any version of flash player for that matter. how do i get flash player to work with firefox 3?
i dont like firefox 11 or 12 in fact they lag terribly im using firefox 3 and its 10 times faster than ff11 or ff12 i dont care what security viruses or whatever there is. i just want to go on youtube to watch a video with feather beta! but it doesnt work with ff11 or ff12 i cant seem to get flash player to work whatsoever

---

### Post by Haneef Mubarak on 2012-05-27
Would you like to give us a description of your computer (specs)? It would really help... Besides, if your computer lags with Firefox, have you tried Chromium from the Software Center or Google Chrome from google.com/chrome? Lastly, if the plugin hasn't been usable on versions >3, perhaps there is a reason for that.

---

### Post by realflow100 on 2012-05-27
i was able to get flash working with firefox on windows xp in a virtual machine but i cant stand using a virtual machine it lags too much. and i have MORE than enough power to run ubuntu and crysis if i needed to. but firefox just LAGS even on 240p youtube videos it lags like NUTS and i have another problem... i cant find the grub boot menu i have no way to select windows xp or windows vista if they had been installed. i got it working one time by holding shift but windows vista and windows xp didnt show up as a boot menu entry.
I searched on google someone found a way to install windows 7 by copying an iso files extracting them to a 4GB partion or something but i dont know how to do that with windows xp and ubuntu 12.04 i just want to get rid of linux for now it lags so bad its just horrible and i cant open hardly any compatible programs i want to install windows xp or windows vista! something other than linux but my pc doesnt have a cd drive and i dont have money to buy a usb flash drive i wanted to install windows from a .iso file that has been extacted to a partion or something i could go on and on all day about this i just want windows xp installed! i have over 2GB physical ram and 1.6Ghz processor with ati radeon HD 4xxx series 2Gb video memory i have WAY more than enough disk space but ubuntu just doesnt run good! i want windows xp!!!! how to i install windows xp from an iso without burning to a cd and without using a flash drive cuz i dont have money to buy one. and i dont own a car either im only 14 years old i dont know much about ubuntu i just want windows xp back please someone help me

---

