---
title: "Atlantis plugin for 64 bit Ubuntu"
date: 2010-05-14
forum: General Help
---

### Post by draks on 2010-05-14
Hi Guys!

This is my first time for a lot of things Linux related. Lucid Lynx is the first version I have installed on a desktop at home so bear with me as I am quite the noob. This is also my first time posting here, and I have all ready learned a ton from browsing this forum.

I have Compiz settings manager installed. It seems that all the effects are working as it should, but I can't find or figure out how to install the Atlantis plugin. Can this plugin work on 10.4 with a 64 bit system? If it can, please let me know, and keep in mind that I am a Linux Beginner.

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
An easy way to search for things in the repos that you want in the terminal would be to use ```
apt-cache search package  (eg. apt-cache search compiz
``` Or you can just open Synaptic Package Manager and type compiz in the search box. Using the former command I found compiz-fusion-plugins-extra which I have installed and I do have the Atlantis plugin... so I assume it's part of that package. You can ```
sudo apt-get install compiz-fusion-plugins-extra
``` or click the check mark box in synaptic. Should be in compiz settings manager thereafter.

---

### Post by draks on 2010-05-14
Thanks for the tip! I was able to install the plugins extra package using Terminal, but I still don't see the plugin in my Compiz Settings area. I see other plugins, but not Atlantis.

Any help is much appreciated.

As a new member I am all ready impressed with response time, and I am starting to love Linux!

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
Hmm... came with mine but I'm not sure which version you have. Do the compiz search again and see if there's another plugins package to install.

Edit: Sorry... I am using the compiz svn repo. [https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

---

### Post by draks on 2010-05-14
When I look in the Ubuntu software center it has this listed as the Compiz version: 1:0.8.4

I searched in Syanptic for any extra plugin packages and didn't find anything. Both the plugin packages I found were all ready installed. I tried re-installing them with no luck

---

