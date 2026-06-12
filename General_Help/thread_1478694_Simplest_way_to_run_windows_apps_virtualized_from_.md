---
title: "Simplest way to run windows apps virtualized from an existing XP install?"
date: 2010-05-10
forum: General Help
---

### Post by Ubuntiac on 2010-05-10
Howdy ho all,

After convincing my wife to try Kubuntu and over the last few years getting used to it, she now needs to run a particular windows only app. It's already installed on XP on another partition.

I'd really rather it wasn't locked to a virtualisation window, but if needs be, then that's ok.

After Googling many outdated Vmware / Virtualbox / Qemu / KVM tutorials I thought I'd ask here.

What's the easiest way of doing this? Thanks!

---

### Post by WorMzy on 2010-05-10
Have you looked into [Wine]("http://www.winehq.org/") and/or [Mono]("http://www.mono-project.com/Main_Page")? Depending on the complexity of the program, you may need to reinstall the application on Ubuntu for it to run correctly; even then it may not perform as required.

---

### Post by steverexon on 2010-05-10
If you are planing to run windows as virtual OS, u can go for Virtualbox, its a good one, user friendly and very stable one . . .

---

### Post by Ubuntiac on 2010-05-10
> **WorMzy said:**
> Have you looked into [Wine]("http://www.winehq.org/") and/or [Mono]("http://www.mono-project.com/Main_Page")?

Yeah. I tried both the stable and dev versions of wine. Didn't even get through the installer. :( I don't quite understand where mono would come into this...

> If you are planing to run windows as virtual OS, u can go for Virtualbox
Is it still necessary to convert my whole Windows partition to a separate VM disk image to do this? I saw this in a few tutorials, but it seemed kind of extreme and came with dire warnings about making the original partiton unusable. That's what kind of scared me into asking here first...

---

### Post by rasmus91 on 2010-05-10
Else, installing Virtual Box isn't difficult installing, nor is it difficult using. 

Id reccomend downloading it from [The VB site]("http://www.virtualbox.org/")

There is a open source version available through the software center, how ever, this lacks some crucial stuff like USB support.

Anyway, Good luck with it.

---

### Post by dino99 on 2010-05-10
i really dont know many apps not able to directly be used with wine 

(winehq, need to add the ppa to the repo into synaptic: [COLOR="Blue"]ppa:ubuntu-wine/ppa  [/COLOR] 
( [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa))

some apps need we use winetricks too: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by WorMzy on 2010-05-10
You can use Mono for running .NET applications, but if Wine isn't getting past the installation then there's not much point considering Mono.

---

