---
title: "LibreOffice 3.4 Doesn't work with Unity"
date: 2011-06-04
forum: General Help
---

### Post by CoolJohnB on 2011-06-04
Having installed Libreoffice 3.4 which is supposed to have better integration with Unity I find it doesn't work!  I started Libreoffice and clicked "Keep in launcher"  which it does for that session it also has quick list, but none of the programs start!  They work fine from applications menu but not from Unity.

Anyone else had a similar problem?   Does anyone know of a solution?

Thanks in advance for any help.

---

### Post by dFlyer on 2011-06-04
I had a simular problem with lightzone. I ended up creating a launcher for it on the desktop. Moved it to .local/share/applications in my home folder and dragged and dropped it into the dock. That fixed lightzone it might work for libreoffice 3.4.

---

### Post by locluca on 2011-06-07
I have a similar problem: LibreOffice 3.4 works fine but there's no integration with unity as you can see from the attached image. Any guess? Thank you

---

### Post by El Viejo on 2011-06-07
I found a much easier solution.
 
Using the home/start/windows (sorry!) key open the dashboard and search for LibreOffice programme you want i.e. Calc
 
When the LibreOffice 3.4 Calc icon appears drag and drop it onto the Unity Launcher.
 
Repeat from Writer etc.

---

### Post by CoolJohnB on 2011-06-08
> **El Viejo said:**
> I found a much easier solution.
 
Using the home/start/windows (sorry!) key open the dashboard and search for LibreOffice programme you want i.e. Calc
 
When the LibreOffice 3.4 Calc icon appears drag and drop it onto the Unity Launcher.
 
Repeat from Writer etc.

That works!   Thank you very much.  :p

---

### Post by Matyy on 2011-06-08
Does the Unity menu integration work for you? Did I misunderstand something about that? I saw screenshots, so I thought it should work.

---

### Post by CoolJohnB on 2011-06-08
> **Matyy said:**
> Does the Unity menu integration work for you? Did I misunderstand something about that? I saw screenshots, so I thought it should work.

No Unity integration does NOT work!

Although it is supposed to and supposed to be better integrated with unity menu, but sadly Libreoffice 3.4 does not do that!!  At least not in my experience, in fact 3.3 was better for integration.

---

### Post by El Viejo on 2011-06-10
I have come across the following, which suggests a solution to the global menu issue.

"To install Global Menu support for LibreOffice.

Install lo-menubar from Ubuntu Software Centre

or

Use in Terminal use the command: sudo apt-get install lo-menubar"

Have not had the opportunity to try myself as yet so fingers crossed!

---

### Post by CoolJohnB on 2011-06-10
> **El Viejo said:**
> I have come across the following, which suggests a solution to the global menu issue.

"To install Global Menu support for LibreOffice.

Install lo-menubar from Ubuntu Software Centre

or

Use in Terminal use the command: sudo apt-get install lo-menubar"

Have not had the opportunity to try myself as yet so fingers crossed!

Tried it, do not install Libreoffice stops working all together! As it takes out the desktop-installer, stick to the suggestion above.

---

### Post by Penguin360 on 2011-06-24
> **El Viejo said:**
> I found a much easier solution.
 
Using the home/start/windows (sorry!) key open the dashboard and search for LibreOffice programme you want i.e. Calc
 
When the LibreOffice 3.4 Calc icon appears drag and drop it onto the Unity Launcher.
 
Repeat from Writer etc.

Worked like a charm! Thank you!

---

### Post by bonfire89 on 2011-06-26
I can't get the global menu to work either.

definitely do not install lo-menubar that breaks libreoffice3.4

---

### Post by bcollier on 2011-07-15
In case people hadn't seen this, I fixed this on my machine using the suggestions below from [http://linuxforums.org.uk/ubuntu/upgrading-libreoffice-to-3-4-1-in-ubuntu-11-04/](http://linuxforums.org.uk/ubuntu/upgrading-libreoffice-to-3-4-1-in-ubuntu-11-04/)

This works fine now in 3.4.  I  had the same bad experience installing the old lo-menubar and having to reinstall LibreOffice 3.4 again when it disappeared.
------------------------------------------------------------------------------------
***Global Menu Support***
If you want LibreOffice 3.4.1 integrated into the Ubuntu 11.04 "Global Menu", **don't** use the lo-menubar package from Synaptic... instead download the lo-menubar.oxt LibreOffice extension from here:
[https://bugs.freedesktop.org/attachment.cgi?id=47502](https://bugs.freedesktop.org/attachment.cgi?id=47502)
or here:
[http://dl.dropbox.com/u/11876059/lo-menubar.oxt](http://dl.dropbox.com/u/11876059/lo-menubar.oxt)
and just double-click it to install

---

### Post by zzarko on 2012-01-09
> **El Viejo said:**
> I found a much easier solution.

Using the home/start/windows (sorry!) key open the dashboard and search for LibreOffice programme you want i.e. Calc
 
When the LibreOffice 3.4 Calc icon appears drag and drop it onto the Unity Launcher.
 
Repeat from Writer etc.
Unfortunately, this doesn't work if I open LO documents from other programs, only if I start it from the launcher.

---

