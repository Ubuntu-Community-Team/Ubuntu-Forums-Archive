---
title: "Running internet explorer in wine?"
date: 2006-06-24
forum: General Help
---

### Post by DR_K13 on 2006-06-24
So I have been trying to swich my mom over to ubuntu. She used it for a while and really likes it, but I had to put her back on windows.  
She needs to run a Secure Citrix client that will only run emedded on internet explorer. I tried the stand alone client and it will not connect. I guess it knows that its not running in IE.  What really suck is her work only supports windows, alot of her friends run Macs , and they had to switch back to windows in order to run the client. 

So- if I install ubuntu, can I install windows and use IE via wine or some other emulator? That is the only reason that she keeps windows around. 


Thanks

---

### Post by Winblowz on 2006-06-24
You can try using it in WINE, and it very well may work. There's no guarantee that it will work though.

---

### Post by lamego on 2006-06-24
I found some instructions for it at [http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html) .
Your other option is to install the free vmware player and do a virtual windows xp install just to run IE, I am more familiar with this approach.
There is a nice page on how to use vmware player on ubuntu on the [wiki]("https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO") .

---

### Post by matrooswolf on 2006-06-24
You can try installing Windows XP in vmware, for me it works like a charm:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by bollix47 on 2006-06-24
Have a look at [ies4linux]("http://www.ubuntuforums.org/showthread.php?t=132508&highlight=HOWTO+wine") too.

btw the cabextract that is talked about in the HowTO is available thru synaptic.

---

### Post by nix4me on 2006-06-24
Try the opera browser too.  Sometimes things run in opera that wont run in firefox.  I have to use opera to take my online exams for school.

nix4me

---

### Post by flargen on 2006-06-24
If you are just looking for Internet Explorer and no other windows features, then I definately recommend ies4linux (someone posted a howto link earlier). Doing a virtual machine install is more complicated and installs the whole of Windows, which you probably do not want.
[QUOTE=nix4me]
Try the opera browser too. Sometimes things run in opera that wont run in firefox. I have to use opera to take my online exams for school.[/QUOTE]
The problem sounds like an IE only plugin, not that firefox is unsupported. Correct me if I'm wrong.

---

### Post by DR_K13 on 2006-06-24
[QUOTE=bollix47]Have a look at [ies4linux]("http://www.ubuntuforums.org/showthread.php?t=132508&highlight=HOWTO+wine") too.

btw the cabextract that is talked about in the HowTO is available thru synaptic.[/QUOTE]


freaking amazing,  works great!

---

