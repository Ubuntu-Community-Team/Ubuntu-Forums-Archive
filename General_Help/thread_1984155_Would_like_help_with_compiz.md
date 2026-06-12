---
title: "Would like help with compiz"
date: 2012-05-21
forum: General Help
---

### Post by kendelcasper on 2012-05-21
hello everyone,

I know there is a lot of information regarding this on the internet but none of which has been helpful to me.

ok I only started using linux ubuntu like 2 or 3 weeks ago, i love it, its soooo cool, and I'm learning more and more. i came across some videos of some cool effects that you can do like with compiz.

however, i have installed the ccsm and changed the settings to what is "supposed to be", but nothing works, i drag the windows they don't wobble, i can't seem to 3D cube, I'm pressing all the buttons that it says. (what is button 3,4,5,6 etc on the mouse) when i press the combo it gives me which is ctrl alt down, it just switches work spaces.

also i remember reading on a site about a command that shows if compiz should work, something about all the things that come up should have a yes next to them or they won't work or something, i was bale to do this after like 5 hours of messing around and found that some of which said no in red, i forget the command hope somebody knows what I'm on about.

also i should mention I'm using a MAC parallels 7 and ubuntu 11.10.

there are some youtube tutorials but there CCSM is different has options i don't. or when people say go to system preferneces and check this box that box. Im not seeing the same options.

PLEASE SOMEBODY help me, I would be very grateful, and hope to be a long time user and find out more and help people just like me.

thank you :)

---

### Post by zombifier25 on 2012-05-21
1. Are you sure you're using Compiz? type this command in the terminal:
```
ps x | grep compiz
```
and post the output.

2. Did you install Compiz extras plugins, like compiz-plugins-extra? Get into Synaptic or whatever and search for compiz-plugins and see if they're installed.

NOTE: Mouse button 1 is left click, 2 is middle click, 3 is right click, 4 is scroll up, 5 is scroll down.

---

### Post by kendelcasper on 2012-05-21
2260 pts/0    S+     0:00 grep --color=auto compiz

this is what it says when i typed the command. I have also been to synaptic and had a few plugins installed, i now have a few extras that i can supposedly do, thanks for that, i did want the 3d windows option. (i thought i had installed them through terminal with such (sudo apt-get install compiz-fusion-plugin-extra) turns out must not have worked cos i did what you said zombifier25 and now have the newer options)

still can't get anything to happen though

also I'm using a trackpad, forgot to mention macbook pro

also i have unity and gnome and have tried to use in both with no effect

---

### Post by zombifier25 on 2012-05-21
> **kendelcasper said:**
> 2260 pts/0    S+     0:00 grep --color=auto compiz


That means Compiz is not enabled. So there's your problem. What Ubuntu are you using?

---

### Post by kendelcasper on 2012-05-21
I'm using Ubuntu 11.10 

wow if that is the case then i still have a lot to learn

how to I enable it my friend

---

### Post by kendelcasper on 2012-05-21
ok i found some thing on the net to see whether compiz should work or not on my linux

i ran the command
/usr/lib/nux/unity_support_test -p

and the result should be
You will get the similar output, all “yes” means it works perfectly.

Not software rendered: yes
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes
Unity 3D supported: yes

but i what i get is 


Not software rendered: **NO**
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: **NO**
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes
Unity 3D supported: **NO**

any one have any answers or know what to do, i just want the 3d cube. it shouldn't be this difficult should it

---

### Post by zombifier25 on 2012-05-21
What graphic card are you using? You may need to install the proprietary driver for your card. Get into the Dash and search for "Additional Drivers"

---

### Post by kendelcasper on 2012-05-21
the graphics card I'm using is 

NVIDIA GeForce 9400M 256 MB (MAC BOOK PRO/PARALLELS)


i click on additional drivers, it only says i have parallels toolgate drivers installed

doesn't give me the option to download anything extra

---

### Post by kendelcasper on 2012-05-21
do you think it might have anything to do with the fact that I'm running ubuntu on my MAC and that the shortcut keys might be interfering with each other

---

### Post by Cheesemill on 2012-05-21
Your problem is you are running Ubuntu in a Parallels VM.

VM's don't support 3D graphics acceleration so you are never going to be able to get compiz working.

---

### Post by RJ12 on 2012-05-21
You can run Compiz on Unity...? I've been missing out then -_-

Edit: Silly me... Unity runs on compiz, totally forgot about that.

---

### Post by kendelcasper on 2012-05-21
i thought as much, thanks peeps

---

### Post by wildmanne39 on 2012-05-21
Hi, I know you can run the cube and effects in vm's in virtualbox because I have setup over 25 of them for testing.

You do need to enable 3d support in virtualbox when you set it up and use there driver that is installed when yoou install guest additions, but the last I had heard it is still not possible in other vm programs.
Thanks

---

