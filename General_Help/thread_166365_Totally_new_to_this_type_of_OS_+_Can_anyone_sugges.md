---
title: "Totally new to this type of OS + Can anyone suggest a good FTP client?"
date: 2006-04-26
forum: General Help
---

### Post by Raavea on 2006-04-26
Well, I've been oogling at the Ubuntu site for a long time now, and last night I finally snapped - I removed XP and installed Ubuntu. (Miraculously, my graphics card suddenly works right, my desktop no longer crashes twice before starting, and I can right click!)

 Anyway - I am a complete beginner with this style of OS - I love it, but I have no idea what to do to get certain results. I grew up on windows - been using them since I was two! And so, this is wierd to me. I'm going to have a lot of questions whilst I learn all the little qwirks and twists, and I hope that you can all put up with it. 

 My current question is: I am a webdesigner. I used to use WSFTP on windows, and I should like a similar program. Can anyone suggest something similar, and tell me how to install it?

 Again, sorry for being so ignorant.

---

### Post by mjm115 on 2006-04-26
[gFTP]("http://gftp.seul.org/") is by far the best FTP client.  You can find it in Synaptic.

You can also try [kasablanca]("http://kasablanca.berlios.de/"), but it doesn't have as many features as WSFTP or gFTP

To install, take a look at [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html).  This is a well written article on how to install software.

---

### Post by Raavea on 2006-04-26
Thanks a bundle, mjm. ^_^


 Edit: *blink* :-k 

 Okay. how on earth do I install this? Treat me like I'm six...

 It told me to see config.log for more information, as it failed. Config.log says a load of stuff, none of which means anythign to me. I think it failed because;
 > configure:2136: error: no acceptable C compiler found in $PATH
 But.. o.O Wow I feel so stupid. I guess I need to install a C Compiler, but where from, and what kind..? I'm not much on C (all I've done is mess around with Dink Smallwood a few years back..) so I don't really know what to go for.. :???:

---

### Post by mjm115 on 2006-04-26
No problem

---

### Post by Raavea on 2006-04-26
Well, I found this;
[http://packages.ubuntulinux.org/breezy/devel/gcc](http://packages.ubuntulinux.org/breezy/devel/gcc)

 Checking the applications as I'm sure I saw something in there I could install...
 Yuppers, but now it needs GLIB 1.2.3 or higher.. I love figuring things out like this... XD

  Hmms. Okay. So..

Edit: Muah. I installed it using Synaptic. Now I'm trying to find it...   o....o

  Yey. Thanks for the help mim. I took a look at that article, but couldn't find the debian menu thing... So I remembered that something in my right-click menu says make launcher... So I did. And it works. Thanks so much! ^_^

---

### Post by OffHand on 2006-04-26
> **Raavea]Well, I found this said:**
> http://packages.ubuntulinux.org/breezy/devel/gcc[/url]

 Checking the applications as I'm sure I saw something in there I could install...
 Yuppers, but now it needs GLIB 1.2.3 or higher.. I love figuring things out like this... XD

  Hmms. Okay. So..

Edit: Muah. I installed it using Synaptic. Now I'm trying to find it...   o....o

  Yey. Thanks for the help mim. I took a look at that article, but couldn't find the debian menu thing... So I remembered that something in my right-click menu says make launcher... So I did. And it works. Thanks so much! ^_^GFTP should be under Applications > Internet. If not open a Terminal and type: ```
killall gnome-panel
```

---

### Post by FizDev on 2006-04-26
[QUOTE=Raavea]
 Okay. how on earth do I install this? Treat me like I'm six...
[/QUOTE]

Just type in a terminal
```
sudo apt-get install gftp
```

---

### Post by nanotube on 2006-04-26
for the future, you will want to know that most applications can be installed simply from the ubuntu repositories, without having to go and look for stuff to download. that is done through commandline with apt-get, or with a gui, through the "synaptic package manager". in the case of gftp, like the previous poster said, you can install it from the repositories.

you may want to go to the absolute beginners section, and read the sticky post titled "how do i install software". 

also for the future, if you do need to install some stuff from outside the repositories and have no compile, you will need to first install package called "build-essential". that package installs make, some compilers, etc, all the stuff that will enable you to build software without any trouble. ;)

---

### Post by Raavea on 2006-04-27
Yeah in the end I never did figure out how to do it with the download - the article mim linked me to led me to synaptic, which I searched within and found gftp.
 Very handy little program, though I can't seem to find a refresh button..

 Thanks for the tips. I have other questions, but gonna go hunt through the help first.

---

### Post by advntr on 2006-04-27
Raavea,

Up on your tool bar, click "Local" and the very last option on the bottom of the drop-down list should be "refresh".

Welcome to Linux!   :-D

---

### Post by frup on 2006-04-27
always check synaptic first... if not there then check the wiki or forums to see if theres a guide to installing something... some awesome information on getting stuff to work which otherwise would be really hard... eg wine, java, codecs and blaah blaah

terminal becomes fun after a while

---

