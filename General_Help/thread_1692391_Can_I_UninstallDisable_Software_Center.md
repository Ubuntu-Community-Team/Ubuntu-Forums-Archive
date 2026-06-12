---
title: "Can I Uninstall/Disable Software Center ?"
date: 2011-02-21
forum: General Help
---

### Post by Pirschjaeger on 2011-02-21
Hi All,

although I can see how it can be a benefit to some the Ubuntu Software Center is a disadvantage to me. When I want to download and install software USC interferes with and blocks the installation.

For example, Mobile Media Converter. One or two Ubuntu releases ago it was easy to install but now I cannot due to USC.

Is there someway I can either uninstall (without losing my entire desktop) or simply disable it?

---

### Post by wiggly81 on 2011-02-21
you can remove it using "Synaptic Package Manager"

or maybe typing sudo apt-get remove software-center

---

### Post by thefasterblueone on 2011-02-21
Here is a link to Mobile Media Converter. Download the .deb file and double click to install.

[http://www.miksoft.net/mobileMediaConverterDown.htm]("http://www.miksoft.net/mobileMediaConverterDown.htm")

---

### Post by andymorton on 2011-02-21
It can probably be removed through the Synaptic Package Manager. I've got no idea if getting rid of it will have a detrimental effect on the rest of the system. Have you tried just using the SPM to install software? 

andy

---

### Post by gandaran on 2011-02-21
> **Pirschjaeger said:**
> Hi All,

although I can see how it can be a benefit to some the Ubuntu Software Center is a disadvantage to me. When I want to download and install software USC interferes with and blocks the installation.

For example, Mobile Media Converter. One or two Ubuntu releases ago it was easy to install but now I cannot due to USC.

Is there someway I can either uninstall (without losing my entire desktop) or simply disable it?
you don't want to use USC? install 'gdebi' then remove the USC from the the nautilus 'open with' list (right click the .deb package » go to properties » open with tab » remove the USC and enable gdebi, now your ubuntu works just like the older ubuntu versions.

---

### Post by Pirschjaeger on 2011-02-21
I've already made the mistake of using Synaptic to uninstall. I lose the desktop too.

I've already dloaded the MMC from Miksoft. USC refuses to install it. There used to be a program that automatically installed (Gdeb?). Just before I deleted my desktop I had installed Gdeb (sorry, I forget the name) but USC overrid it anyway.

---

### Post by Pirschjaeger on 2011-02-21
> **gandaran said:**
> you don't want to use USC? install 'gdebi' then remove the USC from the the nautilus 'open with' list (right click the .deb package » go to properties » open with tab » remove the USC and enable gdebi, now your ubuntu works just like the older ubuntu versions.

Ah ha! This sounds about right.

"remove the USC from the the nautilus 'open with' list"

Can you please translate that into noob for me? :)

---

### Post by gandaran on 2011-02-21
> **Pirschjaeger said:**
> Ah ha! This sounds about right.

"remove the USC from the the nautilus 'open with' list"

Can you please translate that into noob for me? :)
just find any .deb package to install first, right click the .deb package » go to properties menu  » open with tab » remove the USC from the list and enable gdebi if its already installed, easy!

---

### Post by Pirschjaeger on 2011-02-21
Nautilus is the name of the file browser. Who'd of thought. :)

I've been using Ubuntu for years now and can fix most things on my own by trial and error. Did I mention I'm at expert at re-installation? :)

Terminology is my greatest weakness. A lack of patience for learning terminology is my second greatest weakness. 

But I found a little trick that works for me. ALT+F2 and then type the term. That's how I figured out what a 'nautilus' was. ;)

Thanks for the advice all.

---

### Post by mihaimm on 2011-02-21
Since you figured that out, try opening a terminal (ALT-F2, gnome-terminal), go to Downloads (cd Downloads), install package (sudo dpkg -i some-file-ending-in.deb). That will bypass the software center.

---

