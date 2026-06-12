---
title: "Problems getting run ability  with .sh shell file"
date: 2011-09-29
forum: General Help
---

### Post by RHBlakeman on 2011-09-29
Running Natty Narwhal 11.04 with Ubuntu Classic (turned off Unity) and trying to install a package that lets me change the way Ubuntu looks, to make it look and feel like Windows 7 but of course without the BS of Microsloth's OS running. Unpacked the archive into it's own folder and there is a GUIInstall.sh file I need to run in terminal to install it. I have read where I go to the file's property tab and click the box to allow the file to "run" but if I click the checkmark comes on then goes off. I am at administrator level as well. Any ideas here why it's not letting me make the .sh file a run file? 

Package is called something like Win2-7. I have noob level experience in Linux but have been using MS operating systems since DOS 1.25 so very computer experienced but novice with Linux OS's. 

Help is appreciated in advance and if this does work out I will likely be de-Microsoft'd by year's end and go total Ubuntu. Right now this Acer Aspire 7520 is dual boot with Win7 as main OS and also Natty Narwhal as secondary on the boot menu.

---

### Post by MG&amp;TL on 2011-09-29
Well, you could try:

```
cd <folder>
chmod +x GUIinstall.sh
./GUIinstall.sh
```

or simply:

```
cd <folder>
sh GUIinstall.sh
```

---

