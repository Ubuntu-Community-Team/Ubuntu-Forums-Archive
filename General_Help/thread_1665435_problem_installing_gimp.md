---
title: "problem installing gimp"
date: 2011-01-12
forum: General Help
---

### Post by elroulade on 2011-01-12
Hello i got a problem with installing gimp.

when i try to install gimp with the terminal command:

sudo apt-get install gimp

I get this Error(yes its in german i know):

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 gimp : Hängt ab von: libpoppler-glib4 (>= 0.12) ist aber nicht installierbar
E: Beschädigte Pakete

it says, that the packet: libpoppler-glib4 is corrupt.

i already tried to reinstall libpoppler-glib4, but it wouldnt let me

i hope you guys can help me :confused:

---

### Post by Quackers on 2011-01-12
Go to System > Admin > Synaptic Package Manager and in the search box enter gimp. It will appear in the main window. Right-click it and select "Mark for installation" then click the green arrow in the toolbar to apply the change, then watch it install :-)
You will then find it in Accessories > Graphics menu

Guten tag :-)

---

### Post by elroulade on 2011-01-12
> **Quackers said:**
> Go to System > Admin > Synaptic Package Manager and in the search box enter gimp. It will appear in the main window. Right-click it and select "Mark for installation" then click the green arrow in the toolbar to apply the change, then watch it install :-)
You will then find it in Accessories > Graphics menu

Guten tag :-)

Hello

I tried what you suggested, but i got the same error as always:

libpoppler-glib4 (>=0.12) but it is not installable

---

### Post by dFlyer on 2011-01-12
from the command line try this:

sudo apt-get -f install

This sometimes fixes dependency problems.

---

### Post by elroulade on 2011-01-12
> **dFlyer said:**
> from the command line try this:

sudo apt-get -f install

This sometimes fixes dependency problems.


I tried your command, and this is all I get:

0 updated, 0 reinstalled, 0 deleted and 0 not updated.

---

### Post by Quackers on 2011-01-12
Have you run the most recent updates?
What version of Ubuntu are you running?

---

### Post by elroulade on 2011-01-12
Im using Ubuntu 10.10 x86

and yes, i make updates every hour

---

### Post by elroulade on 2011-01-12
Im using Ubuntu 10.10 x86

and yes, i make updates every hour

---

### Post by modean987 on 2011-03-04
A new update come down this morning and it removed gimp, gimp-gap, gimp-guttenburg, and others. Now I can't re-install because of the libpoppler-glib4 thing. Looking in /usr/lib, there is no libpoppler-glib4, only version 5 and a symlink for version 3.

libpoppler-glib5 was one of the updates and it seems to have broke the gimp dependencies.

So, I no longer have gimp. Hope they fix it soon.

UPDATE: After reading other threads I did the following, which fixed the problem

1) Unchecked deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
2) Removed libpopplar-glib5 which removed inkscape, okular, and a bunch of python stuff
3) Removed residual gimp stuff
4) Added deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
5) Reinstalled gimp and all gimp packages I wanted
6) Reinstalled inkscape and okular

---

### Post by sbrbot on 2011-03-24
I had similar problem. I was not able to install GIMP because it depends on library **libpoppler-glib4**. I was not able to install **libpoppler-glib4** since I already had newer **libpoppler-glib5** library installed. Then I uninstalled newer library **libpoppler-glib5** with all programs that depended on it and installed **libpoppler-glib4** manually that I found somewhere on internet and GIMP afterwards. After that GIMP was working fine.

Then I needed PDF viewer **evince** or **epdfview** which were uninstalled with **libpoppler-glib5**. I installed **evince** back which pulled **libpoppler-glib5** along and on my machine both **libpoppler-glib4** and **libpoppler-glib5** coexisted in the same time! Yes, but GIMP now stopped to respond regardless of that **libpoppler-glib4** library were still installed on my machine along with **libpoppler-glib5**. After restarting machine everything was fine; now GIMP works with old library, evince with new one! Happyend.

I don't know, this is strange situation with these two libraries **libpoppler-glib4** and **libpoppler-glib5**. Should I wait for new GIMP release which will use news **libpoppler-glib5** instead insisting on **libpoppler-glib4**!?

---

### Post by travlemon on 2011-04-04
> **sbrbot said:**
> I had similar problem. I was not able to install GIMP because it depends on library **libpoppler-glib4**. I was not able to install **libpoppler-glib4** since I already had newer **libpoppler-glib5** library installed. Then I uninstalled newer library **libpoppler-glib5** with all programs that depended on it and installed **libpoppler-glib4** manually that I found somewhere on internet and GIMP afterwards. After that GIMP was working fine.

Then I needed PDF viewer **evince** or **epdfview** which were uninstalled with **libpoppler-glib5**. I installed **evince** back which pulled **libpoppler-glib5** along and on my machine both **libpoppler-glib4** and **libpoppler-glib5** coexisted in the same time! Yes, but GIMP now stopped to respond regardless of that **libpoppler-glib4** library were still installed on my machine along with **libpoppler-glib5**. After restarting machine everything was fine; now GIMP works with old library, evince with new one! Happyend.

I don't know, this is strange situation with these two libraries **libpoppler-glib4** and **libpoppler-glib5**. Should I wait for new GIMP release which will use news **libpoppler-glib5** instead insisting on **libpoppler-glib4**!?

Hey,

I had the same problem with Gimp reporting that it couldn't install the **libpoppler-glib4** dependency.  The fix was really simple for me.  After searching the problem and seeing your post, I decided to go ahead and download and install** libpoppler-glib4** without removing **libpoppler-glib5**.

This proved successful and the system didn't ever ask me to remove **libpoppler-glib**.

The files are very easy to find via Google, but I will link you to the download page below.  Also, there's a list of dependencies that you may also need to download in order to install the package.  Luckily, it's a short list and I only was missing one of them.

[http://packages.ubuntu.com/lucid/libpoppler-glib4](http://packages.ubuntu.com/lucid/libpoppler-glib4)

I hope this helps!

---

