---
title: "help try run a comand"
date: 2011-08-17
forum: General Help
---

### Post by razadon on 2011-08-17
Hi I try putting in sudo apt-get install build-essential and I get redaing package lists ... Done building depency tree reading state information ... Done E: couldn't find package build essentials what's is dis error ? How can I fix it plz because I've just install a ubuntu 9.04 destop edition and ima new too this and ima not connected too internet is this the problem or is the any way I cn doo it offline if it needs something or what ?? Ima confussed

---

### Post by Topsiho on 2011-08-17
> **razadon said:**
> Hi I try putting in sudo apt-get install build-essential and I get redaing package lists ... Done building depency tree reading state information ... Done E: couldn't find package build essentials what's is dis error ? How can I fix it plz because I've just install a ubuntu 9.04 destop edition and ima new too this and ima not connected too internet is this the problem or is the any way I cn doo it offline if it needs something or what ?? Ima confussed


Doing apt-get instal etc. is trying to find the requested package from the repositories, which are located on computers somewhere on the internet.

So to do this succesfully you just NEED the internet. So that IS a problem if you are not connected to the internet. That perfectly explains your problem.

Why do you need the build-essential anyway, if you are "new to this?"

Topsiho

---

### Post by aeiah on 2011-08-17
> **Topsiho said:**
> 
Why do you need the build-essential anyway, if you are "new to this?"


perhaps because OP needs to compile wireless drivers so as to connect to the internet? :p

you can manually download packages from packages.ubuntu.com, but be warned: once you've got your build-essential packages, there'll probably be many others that are required too. 

if i remember correctly, build-essential is also present on the cd. put the cd in and see if it works then, or try adding it as a repository source in synaptic

you really do need to be connected to the internet to painlessly install software on ubuntu, or to perhaps acquire a new version of the ubuntu DVD. it contains a lot more software than the cd version

---

### Post by seawolf167 on 2011-08-17
Why did you install 9.04? This version hasn't been supported for almost a year. I highly suggest either installing the newest version, 11.04, or the 10.04.3 LTS.

Once you do that, the correct command, as you posted above is:

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by debd on 2011-08-17
I think may be you have the corresponding repository unchecked?

open synaptic package manager and click on "development" on the categories on the left hand side. type "build-essential" in the quick search box.. if it does't show up, goto menu > administration > software sources ; make sure you have all the sources on the 1st tab checked (xcept source code if you dont need it) , close the window and click "reload" on the new dialogue box. and then try to install it again.

---

### Post by oldos2er on 2011-08-17
For offline package installation, try [http://keryxproject.org/](http://keryxproject.org/) or [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by razadon on 2011-08-19
Ryt I've installed 11.04 n connected too internet and its updated it and now I got too kernals when I switch computer on so I chosse the new 1 i fink 2.6.38.10 and ive gt a big problem won't let me make a driver for my usb rt73 chipset 1 I've download rt73 3.0.3 and extracted on desktop and wen I run da comand make it gets an error sayin rt73.ko failed to build!
make: *** [module] Error 1 and ive tryed nearly everyfing I cn fing of even rebootin my computer 4 tyms bt still its sayin dat will not let me make plz cn u help mee

---

### Post by razadon on 2011-08-20
Cn any 1 help?

---

### Post by debd on 2011-08-20
I think this should have your answer: [http://ubuntuforums.org/showthread.php?t=1499012](http://ubuntuforums.org/showthread.php?t=1499012)

also, [here's]("http://ubuntuforums.org/showthread.php?t=1215251") a step by step instruct for installing a version Ralink RT73 USB Wifi Driver which though backdated... may help.

---

### Post by razadon on 2011-08-20
Thanks debd i fixed it by installin 9.04 agen n builded and copyed dat builded file and pt it back into my 11.04 ubuntu and it tryed build and it worked fine and installed too thanks by the for the help plz close thread is solved!!

---

