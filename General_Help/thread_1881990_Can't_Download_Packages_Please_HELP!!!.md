---
title: "Can't Download Packages Please HELP!!!"
date: 2011-11-16
forum: General Help
---

### Post by fnyahoo on 2011-11-16
I have persistent ubuntu created with Unetbootin. I try to download  packages through synaptic or terminal it doesnt find the packages. lets  say i want to download chrome, i search it on synaptic it doesnt work. i  try to download it from terminal i get 

ubuntu@ubuntu:~$ sudo apt-get install chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package chromium
ubuntu@ubuntu:~$ 

ERROR!!! 

Please help because the reason i try to make it Persistent so I could download some packages and keep em.

---

### Post by matt_symes on 2011-11-16
Hi

```
sudo apt-get install chromium-browser
```

Use apt-cache search to find packages with apt.

```
matthew@matthew-Aspire-7540:~$ apt-cache search chromium
<SNIP>
chromium-browser - Chromium browser
chromium-browser-dbg - chromium-browser debug symbols
chromium-browser-l10n - chromium-browser language packages
chromium-bsu - fast paced, arcade-style, scrolling space shooter
chromium-bsu-data - data pack for the Chromium B.S.U. game
chromium-codecs-ffmpeg - Free ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-dbg - chromium-codecs-ffmpeg debug symbols
chromium-codecs-ffmpeg-extra - Extra ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-extra-dbg - chromium-codecs-ffmpeg-extra debug symbols
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by fnyahoo on 2011-11-16
ubuntu@ubuntu:~$ apt-cache search chromium
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package chromium-browser

thats what i get from the code.

could it be because of unetbootin persistent?

---

### Post by fnyahoo on 2011-11-16
never mind got it... sorry to bother you guys, i missed some config settings. SOLVED... thank you

---

### Post by matt_symes on 2011-11-16
Hi

> **Fcukinyahoo said:**
> ubuntu@ubuntu:~$ apt-cache search chromium
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package chromium-browser

thats what i get from the code.

could it be because of unetbootin persistent?

Well that's better in that chromium-browser is the correct package name for chromium.

It looks like it's not persisting your updates. This may be because it's running entirely in memory and you have not created the persistent USB correctly.

But first i should ask, what version of Ubuntu are you using ? 

Let see if you can install anything. From a terminal
```

sudo apt-get update
sudo apt-get install chromium-browser
```

 ```
ls /var/lib/apt/lists/ | wc -l
```

That is a small L above. Post back results of all three commands.

Kind regards

---

