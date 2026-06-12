---
title: "Minimal Gnome Shell installation"
date: 2011-11-29
forum: General Help
---

### Post by Blasphemous on 2011-11-29
I'd like to do **the most lightweight** Kernel **3.2**(previous ones gave me problems) + **Gnome Shell** installation. 

 With Gnome 2.X I used to use Ubuntu mini CD and then apt-get install gnome-core gdm xorg. Doing that, I was able to have a minimal desktop where I could install what I wanted.

 Now with Gnome shell the only options are Linux Mint, Fedora or Opensuse, but they have too many useless programs in their default installation...

---

### Post by BC59 on 2011-11-29
> **Blasphemous said:**
> I'd like to do **the most lightweight** Kernel **3.2**(previous ones gave me problems) + **Gnome Shell** installation. 

 With Gnome 2.X I used to use Ubuntu mini CD and then apt-get install gnome-core gdm xorg. Doing that, I was able to have a minimal desktop where I could install what I wanted.

 Now with Gnome shell the only options are Linux Mint, Fedora or Opensuse, but they have too many useless programs in their default installation...

There is an Ubuntu Minimal Installation

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Bucky Ball on 2011-11-29
> **BC59 said:**
> There is an Ubuntu Minimal Installation

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Yea, just type 'cli' at the cursor and you're away. You need to make a list of what you need to 'sudo apt-get install ...' before you start, then just type that in, hit enter and you're rolling. My minimal hits the login screen in 12 seconds!

---

### Post by Blasphemous on 2011-11-29
> There is an Ubuntu Minimal Installation

[https://help.ubuntu.com/community/In...tion/MinimalCD](https://help.ubuntu.com/community/In...tion/MinimalCD)

Ubuntu uses Kernel 3.0, not 3.2, is it right? 

> Yea, just type 'cli' at the cursor and you're away. You need to make a list of what you need to 'sudo apt-get install ...' before you start, then just type that in, hit enter and you're rolling. My minimal hits the login screen in 12 seconds!

I'm not an expert, and i really do not know the exact packeges I need in order to run the system.

With *apt-get install gnome-core gdm xorg* I was able to have the DE with nothing inside (exept terminal, gedit and other basic stuff), and then, with synaptic, I could add what Iwanted.
Now with Gnome shell I don't know how to install that basic desktop!

Maybe the correct question should be:
What is the Gnome Shell command for Gnome 2.x *apt-get install gnome-core gdm xorg*?

---

### Post by BC59 on 2011-11-29
> **Blasphemous said:**
> Ubuntu uses Kernel 3.0, not 3.2, is it right? 

Well you can always use another kernel if you like, but you are going to deal with an avalanche of monster bugs.

I'm not sure but I think OpenSUSE only uses kernel 3.2

---

### Post by Blasphemous on 2011-11-29
> I'm not sure but I think OpenSUSE only uses kernel 3.2

Also the new Linux Mint uses it, but it is full of bloatware and useless software (like mono, cups since I don't use a printer...) and that's why I'd like to do a minimal install...
But it seems like a full installation is the only answer...

---

### Post by Bucky Ball on 2011-11-29
Best bet. 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Psychocat may even chime in with a tip, and;

[http://www.google.com.au/#sclient=psy-ab&hl=en&source=hp&q=ubuntu+minimal+install+guide&pbx=1&oq=ubuntu+minimal+instal&aq=1&aqi=g4&aql=&gs_sm=c&gs_upl=0l0l1l1954l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=3f8100aad673ee8e&biw=1366&bih=596](http://www.google.com.au/#sclient=psy-ab&hl=en&source=hp&q=ubuntu+minimal+install+guide&pbx=1&oq=ubuntu+minimal+instal&aq=1&aqi=g4&aql=&gs_sm=c&gs_upl=0l0l1l1954l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=3f8100aad673ee8e&biw=1366&bih=596)

The sudo apt-get line is the one you're after. There are some *essential* things you need here but stuff like web browsers, email clients and the like are up to you. I found a neat page which guided me through it but while ago and haven't time to hunt it down right now. Good luck ... ;)

---

### Post by BC59 on 2011-11-29
> **Bucky Ball said:**
> Best bet. 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)



Excellent solution for old computers!

---

### Post by Bucky Ball on 2011-11-29
> **BC59 said:**
> Excellent solution for old computers!

... also new ones that I want sleek and speedy. My 4Gb i3 runs like a rocket.

---

