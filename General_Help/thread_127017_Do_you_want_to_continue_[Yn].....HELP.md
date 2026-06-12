---
title: "Do you want to continue [Y/n]?.....HELP"
date: 2006-02-07
forum: General Help
---

### Post by lambertrj on 2006-02-07
I am geting stuck when ever this question pops up 

"Do you want to continue [Y/n]?" 

I have tryed     y...Y....yes...Yes....YES....and die #%$#$## ](*,) 

none of thoes seem to work. the answer is yes but I do not know how to tell it so....


Its simple smug reply is  " Abort."

pls HELP

this is in the terminal BTW..

Thankyou.

---

### Post by kingsidy on 2006-02-07
more detail would help. Plus what program are you trying to install?
also have you tried just hitting ENTER. often times, Yes is the default.

---

### Post by goatflyer on 2006-02-07
It would help a whole lot if we could see the message or warning that appears before the 'Do you wish to continue' prompt.

---

### Post by earobinson on 2006-02-07
copy and paste the context! (lol 3 people all witht eh same thing)

---

### Post by lambertrj on 2006-02-08
robert@hellco:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  aalib1 gcc-3.3-base gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd
  gstreamer0.8-caca gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad
  gstreamer0.8-mikmod gstreamer0.8-mpeg2dec gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0
  libmikmod2 libmpeg2-4 liboil0.2 libsidplay1-c102 libstdc++5 libswfdec0.3
  slang1
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  aalib1 gcc-3.3-base gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd
  gstreamer0.8-caca gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad
  gstreamer0.8-mikmod gstreamer0.8-mpeg2dec gstreamer0.8-plugins
  gstreamer0.8-sid gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0
  libjack0.80.0-0 libmad0 libmikmod2 libmpeg2-4 liboil0.2 libsidplay1-c102
  libstdc++5 libswfdec0.3 slang1
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 1403kB/1848kB of archives.
After unpacking 5095kB of additional disk space will be used.
Do you want to continue [Y/n]?
Abort.
robert@hellco:~$




This time i tryed just hiting Enter......did not work


oh and its a 60g HD no chance of not enough space

---

### Post by Zeroangel on 2006-02-08
Unless you have Adobe Reader installed ;)

---

### Post by lambertrj on 2006-02-08
[QUOTE=Zeroangel]Unless you have Adobe Reader installed ;)[/QUOTE]


hehe Sry? is it huge?

---

### Post by earobinson on 2006-02-08
ya Y then enter should do it, works for me

try this sudo apt-get install gstreamer0.8-plugins -y (y forces yess)

---

### Post by lambertrj on 2006-02-08
The forced -Y work....But now it is telling me a new problem?

Setting up gstreamer0.8-plugins (0.8.8-1ubuntu4) ...
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
robert@hellco:~$




I may want to do what .....does this mean i have to run "sudo apt-get update"

and start over again?

---

### Post by RAOF on 2006-02-08
[QUOTE=lambertrj]The forced -Y work....But now it is telling me a new problem?

Setting up gstreamer0.8-plugins (0.8.8-1ubuntu4) ...
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
robert@hellco:~$

I may want to do what .....does this mean i have to run "sudo apt-get update"

and start over again?[/QUOTE]
Those mirromax backports repositories are no longer up - you should remove them from your sources.list.  Furthermore, since those correspond to the hoary backport repositories, you should remove them anyway, even if the repositories still existed ;)

Edit your sources.list, then run sudo apt-get update

---

### Post by lambertrj on 2006-02-08
wooot .... thx bro

---

### Post by earobinson on 2006-02-08
glad it works now!

---

