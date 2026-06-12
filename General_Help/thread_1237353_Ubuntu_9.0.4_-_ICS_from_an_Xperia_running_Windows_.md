---
title: "Ubuntu 9.0.4 - ICS from an Xperia running Windows Mobile 6.1"
date: 2009-08-11
forum: General Help
---

### Post by n_s_simpson on 2009-08-11
Hi, I have just installed Ubuntu and I have to say Linux has come a long way since I last tried Mandrake and Red Hat about 10 years ago.
 
I didn't expect Internet Sharing to work from my Xperia but thought I'd try it.
 
Firstly one thing that needs to be set is ActiveSync on the phone (I haven't selected "Enable advanced network functionality" since on Vista that option stopped ICS from working).
 
Simply plugging in the phone via USB makes Ubuntu report that the network is active and it assigns an IP address via DHCP.
 
When I ping a web address such as yahoo.co.uk from the terminal I get replies so it's resolving IP addresses.
 
Unfortunately that's as far as it gets...
 
Running Firefox it gets the title of the webpage but the actual page won't load. It only seems to accept the first couple of bytes of data.
 
Any ideas?
 
Thanks
 
Nick

---

### Post by n_s_simpson on 2009-08-11
To make things worse installing Ubuntu has knocked out Vista even though I installed Ubuntu correctly on a seperate partition. I need to find my Vista CD as it's reporting a missing file.
 
I can't use normal broadband as it's temporarily down at home. Therefore without having ICS I can't use my computer.
 
I've read various fixes but they seem to revolve around WM6 and/or different versions of Ubuntu. One Xperia owner commented that it worked straight away without any messing around on 9.0.4.
 
I'm wondering whether some of the updates are required before it'll work. Unfortunately I can't do any updates :(
 
I hope someone can shed some light on this issue.

---

### Post by n_s_simpson on 2009-08-11
I'm just leaving work now but will be checking this thread on my Sony Ericsson Xperia X1 phone.
 
Any help would be appreciated as to why it's connecting but not allowing Firefox to download the webpage.
 
As an aside, when I tried to ping a larger amount of data within the terminal it didn't like that either.

---

### Post by commodoor on 2009-08-11
> **n_s_simpson said:**
> I'm just leaving work now but will be checking this thread on my Sony Ericsson Xperia X1 phone.
 
Any help would be appreciated as to why it's connecting but not allowing Firefox to download the webpage.
 
As an aside, when I tried to ping a larger amount of data within the terminal it didn't like that either.

hi 

i have an xperia also and I'm using wm for years now. i also tried to share the internet with my laptop but i didn't succeed it very hard to get it working. you can try Wi-fi router you can get it from xda-developers I'm not sure if that works but you can give it a try.

there are some tutorials on the net to get PAN working(bleuthoot internet sharing) but it didn't work for me.

good luck with it. if you are able to share internet please let me know

---

### Post by n_s_simpson on 2009-08-11
it's so annoying that one person said he simply plugged it in. i am now wondering if it's an update that's needed. problem is i don't have normal broadband at the minute.

it's so close to working i can taste is!

---

### Post by n_s_simpson on 2009-08-11
set mtu to 1394 and it works.

can't understand why auto doesn't work and i'm sure it's 1500 in windows but in ubuntu you need to override to 1394.

can anyone explain why??

---

### Post by n_s_simpson on 2009-08-11
I can confirm that after doing all the updates it still requires you to override the automatic setting to 1394.

Mind you got a problem with one of the updates but I'm just going to start a new thread about that one...

Thanks

Nick

---

### Post by commodoor on 2009-08-12
Ok ik tried what you did, i was able to ping but wilt 25% Loss of packages and i wasn't able to go to google. i hope it will fully work and automatic

---

### Post by n_s_simpson on 2009-08-12
You need to enable ActiveSync on your phone.
 
I've also got advanced networking enabled but don't think this is necessary.

---

### Post by n_s_simpson on 2009-08-12
If it doesn't work it might be worth checking your settings in a terminal by typing ifconfig.
 
 
Does anyone have an idea why Ubuntu doesn't set MTU to 1394 automatically if that is the limit?

---

### Post by n_s_simpson on 2009-11-29
Just to confirm it's the same situation with Ubuntu 9.10 when you first install it.

---

