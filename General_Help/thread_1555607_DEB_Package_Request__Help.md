---
title: "DEB Package Request / Help"
date: 2010-08-18
forum: General Help
---

### Post by Cango on 2010-08-18
Hello,

  I just registered because this site is at the top of almost every Google search I did. Although I am quite newcomer to Linux, somehow handle things but this time I unfortunately need help.

  There is a source file I have to compile. Not to mention that I have never compiled any source, I have to compile it on a HP5725 Thin client.

  As HP has only 512mb disk and 40mb free space is left, I have a serious freespace problem and embedded Linux (Debian + Gnome) doesn't have even 'make' package, so I am stuck at a certain point. Also embedded system is sarge but source seems to be needing lenny (I managed to overcome this by upgrading packages partially)

  So I would ask if someone could create a DEB package for me which would help me a lot.

  Source file is here : [http://www.arabatopla.com/acr38_src.zip](http://www.arabatopla.com/acr38_src.zip)

---

### Post by realzippy on 2010-08-18
Rename the file from .zip to .deb
and see if it works..

---

### Post by Cango on 2010-08-18
[QUOTE=realzippy;9734657]Rename the file from .zip to .deb
and see if it works..

<snip>

Thank you but file is named as AMD64 but this is x86, would it be a problem?

---

### Post by realzippy on 2010-08-18
Edit.
see post #6

---

### Post by Cilph on 2010-08-18
-

---

### Post by realzippy on 2010-08-18
Here is one in 32 bit:




Note:

made with checkinstall,means you might have to install dependencies manually...

Again,rename from .zip to .deb
for some reason I cannot upload file as .deb

---

### Post by Cango on 2010-08-18
> **realzippy said:**
> Here is one in 32 bit:




Note:

made with checkinstall,means you might have to install dependencies manually...

Again,rename from .zip to .deb
for some reason I cannot upload file as .deb

Thank you but if I may ask one last favor,

Do you have any idea what are dependencies or will it warn me about them?

---

### Post by realzippy on 2010-08-18
It will not complain since it has no infos about the dependencies.
Could not find those in the source package (no control file?),ran checkinstall
with the *--requires* option,what did not work.

Since it is a driver for a card reader (?),those might be interesting (if it does not work):

**libacr38u libacr38ucontrol0 libacr38ucontrol-dev** pcscd libpcsclite-dev libusb-dev libpcsclite-dev

---

### Post by Cango on 2010-08-18
> **realzippy said:**
> It will not complain since it has no infos about the dependencies.
Could not find those in the source package (no control file?),ran checkinstall
with the *--requires* option,what did not work.

Since it is a driver for a card reader (?),those might be interesting (if it does not work):

**libacr38u libacr38ucontrol0 libacr38ucontrol-dev** pcscd libpcsclite-dev libusb-dev libpcsclite-dev

I had already installed libusb-0.1-4 , pcscd,  pcsc-tools with apt so probably installed needed dependencies as it worked like a charm.

Thank you once again.

There are two things I wonder but I doubt if I should ask since I already asked too much.

 Yet still, (using Gnome)

a - I created a desktop link for gscriptor (found in pcsc-tools) , but probably because it is a PERL script it always ask "display , run , cancel, view" options. Is there anyway to run it without asking anything?

b - After installing pcsc-tools and pcscd (which I am suspected as it is a daemon) it opens a terminal maximized and docked at upper left of screen and it takes time to start. It also changed behaviour of windows, they are all docked and there is no title bar.

---

### Post by realzippy on 2010-08-18
Sorry cannot help you since I don't have a card reader to test the
gscriptor/pcsc stuff.What is your shortcut for *gscriptor*?

Better make a new thread for a new problem...
btw.,mark this thread as solved (Threadtools) please.



EDIT:
Going to remove the link to the deb file

---

### Post by Cango on 2010-08-18
> **realzippy said:**
> Sorry cannot help you since I don't have a card reader to test the
gscriptor/pcsc stuff.What is your shortcut for *gscriptor*?

shortcut problem is no longer important but 

I must fix window manager problem.

google search suggests metacity but there is no metacity executable (to --replace) but metacity-common is installed.

I think while installing pcsc-tools one of 45 lenny dependencies made sarge based system ruined.

---

### Post by Cango on 2010-08-18
I have found the reason pcsc-tools package removes gtk2-engines and metacity. I have reinstalled and then voila


Thank you.

---

