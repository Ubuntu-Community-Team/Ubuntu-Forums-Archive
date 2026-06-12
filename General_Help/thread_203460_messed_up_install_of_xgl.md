---
title: "messed up install of xgl"
date: 2006-06-25
forum: General Help
---

### Post by aznchong91 on 2006-06-25
I was installing/updating xgl, but accidentally stopped it in the middle. when I tried to install/update it again, it gave me some REALLY annoying errors. Now I can't install anything through apt-get! **please help!**

errors:
Removing xgl ...

ERROR: SuSEconfig or requested SuSEconfig module not present!

dpkg: error processing xgl (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 xgl
E: Sub-process /usr/bin/dpkg returned an error code (1)

PLEASE HELP!

---

### Post by panurge77 on 2006-06-25
Maybe you can try downloading apt-get deb from ubuntu package page and installing it again?
sudo dpkg -i aptwahtever.deb

---

### Post by JoWilly on 2006-06-25
Run synaptic and in the menu select fix broken packages....

---

### Post by aznchong91 on 2006-06-25
thanks for the suggestions. i tried using synaptic... didn't work. 

where could I download the .deb? 

Thanks again! PLEASE HELP!

---

### Post by JoWilly on 2006-06-26
[quote=aznchong91]thanks for the suggestions. i tried using synaptic... didn't work. 

where could I download the .deb? 

Thanks again! PLEASE HELP![/quote] 
The best xgl/compiz packages are in this repo:
[http://www.beerorkid.com/compiz/]("http://www.beerorkid.com/compiz/")

You can download them by hand, but its best to add it to your sources list, then run synaptic, reload packages, fix broken packages and then apply the changes.

It is almost not possible that applying the changes after fixing the broken packages is not working.

Where did you get your debs ? Why do you have suseconfig in them ?

---

### Post by aznchong91 on 2006-06-26
well... i don't really remember... I followed a howto on this forum. I just need to download a .deb, or even a .rpm, of xgl... Please help! thanks!

---

### Post by joshrobinson on 2006-06-26
[QUOTE=aznchong91]well... i don't really remember... I followed a howto on this forum. I just need to download a .deb, or even a .rpm, of xgl... Please help! thanks![/QUOTE]

do what was said above, and add the beeorkid repo's and use synaptic to fix it up.. how did you get a suse error running ubuntu? did you convert a suse .rpm to .deb?

```
First, open your /etc/apt/sources.list in an editor.
sudo nano /etc/apt/sources.list

Then, insert this line
deb http://www.beerorkid.com/compiz dapper main

Then, save and exit the editor and run this command to add my key.
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -

Then, use the repository as usual. The useful packages are compiz, compiz-gnome, and compiz-kde.

```

---

### Post by aznchong91 on 2006-06-26
actually... i think i did convert a suse .rpm to a .deb... :/ any way to fix that?

---

### Post by aznchong91 on 2006-06-27
anyone else able to help? :/

---

### Post by aznchong91 on 2006-06-27
bumpity bump... i need help!

---

### Post by joshrobinson on 2006-06-27
[QUOTE=aznchong91]bumpity bump... i need help![/QUOTE]

did you do what i posted? to add the line to your sources?

next to sudo apt-get update
sudo apt-get upgrade
sudo apt-get install compiz

---

