---
title: "Please help me to make my personal ubuntu OS"
date: 2010-08-09
forum: General Help
---

### Post by fremantle on 2010-08-09
I am trying to make a customized lightweight ubuntu based os for my netbook. im like in the transition period between n00b and a linux guru :P so guys i need a lot of help.. so first of all i installed ubuntu lucid minimal and trying to build on that. from the command line ,, so first i am trying to choose unity as the default display manager. how can i do that>??

---

### Post by JustinR on 2010-08-09
Hi!

Try using a script called 'PerfectMinimal', its specifically meant for minimal Ubuntu installations and will give you choices to install applications up to the point it will look like a normal installation. It gives you multiple options for Desktop Environments and other apps.

[http://andyduffell.com/techblog/?page_id=396](http://andyduffell.com/techblog/?page_id=396)

I recommend it, its very nice!

---

### Post by fremantle on 2010-08-09
> Ubuntu desktop
Gnome core
Kubuntu desktop
KDE4 minimal
Xubuntu desktop
XFCE4
Lubuntu desktop
LXDE
Myth TV
no unity

besides i wana do it myself to learn

---

### Post by JustinR on 2010-08-09
> **fremantle said:**
> no unity

besides i wana do it myself to learn

Look in the comment section for a solution if I recall correctly.

Also - it'll most likely be hard to a linux new user to install an unsupported DE, like Unity - it will most likely be overwhelming and unnecessary.

You could examine the script to see how it works if you want to learn more.

**Edit:** Oops, the comment section is on this page: [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by JustinR on 2010-08-09
If you really want to learn,

(if you're willing to use the PerfectMinimal script),

when it asks you about the desktop environment, select 'Keep Current Desktop Environment', in your case none is installed - which is good. Follow this guide when the PerfectMinimal script is finished to install Unity:

[http://digitizor.com/2010/05/10/how-to-install-unity-in-ubuntu-10-04-lucid-lynx/](http://digitizor.com/2010/05/10/how-to-install-unity-in-ubuntu-10-04-lucid-lynx/)

---

### Post by fremantle on 2010-08-09
hmm...i only installed gdm and now theres no terminal .. oops...how can i get into the grub2 boot menu>>??

---

### Post by fremantle on 2010-08-09
got it. but now running this > sudo apt-get install gnome-core gdm network-manager-gnome indicator-applet-session notify-osd


the guide you showed describes how to install unity on a gnome environment i want JUST unity.. nothin else

---

### Post by JustinR on 2010-08-09
> **fremantle said:**
> got it. but now running this 


the guide you showed describes how to install unity on a gnome environment i want JUST unity.. nothin else

Okay, well what do you mean by 'Unity'? Unity as in E17 Enlightenment or Unity as in the Ubuntu Netbook Edition interface, Unity?

---

### Post by fremantle on 2010-08-09
:P misunderstanding



unity the new desktop for ubuntu netbook

---

### Post by JustinR on 2010-08-09
> **fremantle said:**
> :P misunderstanding



unity the new desktop for ubuntu netbook

Okay,

```

sudo add-apt-repository ppa:canonical-dx-team/une
sudo apt-get update && sudo apt-get install unity

```

---

### Post by fremantle on 2010-08-09
ok. but the problem is, i did it before. you have to use it in gnome terminal. then select it as a "session" is gdm. what i would like is select is as a default. only unity, no gnome.

---

### Post by JustinR on 2010-08-09
> **fremantle said:**
> ok. but the problem is, i did it before. you have to use it in gnome terminal. then select it as a "session" is gdm. what i would like is select is as a default. only unity, no gnome.

If you select 'Unity' (I think the newest version says, 'Ubuntu Netbook Edition Unity') if will be default on reboot.

---

### Post by fremantle on 2010-08-09
unity was a bad idea, totally unstable.


moving on...

---

### Post by fremantle on 2010-08-09
xnoise for music
vlc (d'oh)
ubuntu soft cntr (latest maverick)

---

### Post by ubunterooster on 2010-08-09
**[B]Repo for xnoise:**

ppa:shkn/xnoise[/B]

---

### Post by fremantle on 2010-08-09
any lightweight presentation app? (like kpresentation)

---

### Post by ubunterooster on 2010-08-09
BTW: for finding alternative apps try osalt 
[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by cariboo on 2010-08-09
You do realize that unity isn't even close to being done yet, Alpha 3 just came out Aug 5th. Considering Unity has only been around for a little over 3 months, it works pretty well. I've been running it since the ppa was opened up and have found it to be quite stable. Unity is now in the Maverick repos, so you no longer have to use the pre-alpha version from the ppa.

---

