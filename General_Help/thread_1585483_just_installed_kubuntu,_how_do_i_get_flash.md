---
title: "just installed kubuntu, how do i get flash?"
date: 2010-09-30
forum: General Help
---

### Post by rajohns08 on 2010-09-30
when i had ubuntu i could find it in the software center, but i can't find it in this software center.

---

### Post by searchfgold6789 on 2010-09-30
I think you can get it from the adobe website, and also synaptic. Kubuntu comes with synaptic, right?

---

### Post by rajohns08 on 2010-09-30
> **searchfgold6789 said:**
> I think you can get it from the adobe website, and also synaptic. Kubuntu comes with synaptic, right?

i have no clue what synaptic is or if i have it all i know is i cant watch videos on youtube. brand new linux user here ha. which file do i pick from the adobe website though? targz, yum, rpm, etc...

---

### Post by rajohns08 on 2010-09-30
also, how do i know if im running on 32 bit or 64 bit in kubuntu?

---

### Post by searchfgold6789 on 2010-09-30
[[SIZE=3]You can download the file here.[/SIZE]]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.deb%29")
To find out if you're running 64 or 32:
open up a terminal and type:
```
uname -a
```If you see a 64 somewhere in there, you're running a 64 bit system. Otherwise it's 32 bit.
All 32 bit programs will work on a 64 bit computer :)
welcome to linux :) :) :) :) :)

---

### Post by rajohns08 on 2010-09-30
> **searchfgold6789 said:**
> [[SIZE=3]You can download the file here.[/SIZE]]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.deb%29")
To find out if you're running 64 or 32:
open up a terminal and type:
```
uname -a
```If you see a 64 somewhere in there, you're running a 64 bit system. Otherwise it's 32 bit.
All 32 bit programs will work on a 64 bit computer :)
welcome to linux :) :) :) :) :)


the link for flash player gave an error: wrong architecture i386

---

### Post by Cavsfan on 2010-09-30
Or ```
file /sbin/init
```
or ```
uname -m
```

---

### Post by Cavsfan on 2010-09-30
> **rajohns08 said:**
> the link for flash player gave an error: wrong architecture i386

That means your 64 bit get the latest here: [http://labs.adobe.com/downloads/flashplayer10.html]("http://%3Cu%3Ehttp://labs.adobe.com/downloads/flashplayer10.html%3C/u%3E")

---

### Post by rajohns08 on 2010-09-30
> **Cavsfan said:**
> That means your 64 bit get the latest here: _[http://labs.adobe.com/downloads/flashplayer10.html]("http://%3Cu%3Ehttp://labs.adobe.com/downloads/flashplayer10.html%3C/u%3E")_

that link didnt work but now when i try to download it says "Your Google Chrome browser already includes the latest Adobe® Flash® Player built-in."

however i still cannot watch youtube videos because it says i need to upgrade flash...

---

### Post by Cavsfan on 2010-09-30
I fixed the link above, but I didn't know you were using Google Chrome. I have never messed with that. I use FireFox.

---

### Post by Cavsfan on 2010-09-30
Here is a good site to check the version of Flash:
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by swagatmishra on 2010-09-30
you could also use the synaptic package manager to install flash.But i guess it wont install the latest verson.
just search for flash in synaptic and install flashplugin-installer from the resulting search list

---

### Post by itahmid on 2010-10-01
Hello, I am new to linux and i just installed ubuntu 7.10 but i am unable to work on most of the commands for installing and updating softwares on this OS, while installing "pyload" (a python based download manager) i am getting this error "
Please click to see the screen shot : [http://www.picscrazy.com/view/Screenshot18R](http://www.picscrazy.com/view/Screenshot18R)

And while installing "install_flash_player_10_linux.deb" i get this error:
[http://www.picscrazy.com/view/Screenshot24](http://www.picscrazy.com/view/Screenshot24)

Please help me to solve it,

Thanks

---

### Post by Glaucous on 2010-10-01
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Go there, download the correct zip, the unpack it to /usr/lib/chromium-browser/plugins (requires sudo).
You can make sure it is loaded by going to about: plugins (without whitespace) in chromium, and check for Shockwave Flash.

Or, if you're using Mozilla Firefox, unpack it to:
/home/<user>/.mozilla/plugins

---

### Post by andrewthomas on 2010-10-01
If you are having a problem with the sound in flash this will work great.

[http://ubuntuforums.org/showpost.php?p=9889479&postcount=3](http://ubuntuforums.org/showpost.php?p=9889479&postcount=3)

---

### Post by gandaran on 2010-10-01
> **rajohns08 said:**
> that link didnt work but now when i try to download it says "Your Google Chrome browser already includes the latest Adobe® Flash® Player built-in."

however i still cannot watch youtube videos because it says i need to upgrade flash...
which version of google chrome?  is it 32-bits or 64-bits chrome?
and ubuntu is 32-bits or 64-bits?

---

### Post by cek on 2010-10-01
I suppose you already tried the easiest option?  You need to enable the multiverse repo, which can be done in KPackageKit by selecting the correct source.  Then, from a terminal:

sudo apt-get install flashplugin-nonfree

---

### Post by Dyegov on 2010-10-01
Wait so it says your Chrome already has flash installed (which it does indeed by default) but you still can't play youtube videos? If it's indeed already installed it won't let you install again. You may have to find a way to uninstall the current one and install again.

---

