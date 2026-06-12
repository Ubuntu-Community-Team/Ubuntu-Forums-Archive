---
title: "copy and paste"
date: 2010-11-23
forum: General Help
---

### Post by TonyDiF on 2010-11-23
I am running Ubuntu 10.10 and I connect from my windows XP with TightVnc. I can not copy and paste from my XP sytem to my Ubuntu system or form Ubuntu to my windows XP. Is this something that does not work, or do I need a setting for this to work ?
 
thanks
TonyD

---

### Post by sikander3786 on 2010-11-23
> **TonyDiF said:**
> I am running Ubuntu 10.10 and I connect from my windows XP with TightVnc. I can not copy and paste from my XP sytem to my Ubuntu system or form Ubuntu to my windows XP. Is this something that does not work, or do I need a setting for this to work ?
 
thanks
TonyD
What do you intend to copy? Text or files/folders?

---

### Post by pricetech on 2010-11-23
Samba will let you do windows file sharing on your Ubuntu box.  system-config-samba in Synaptic Package Manager will give you Samba plus a handy configuration tool.  You'll also find the RDP support under Ubuntu to be quite solid.

SSH can be used under windows with a client like WinSCP for file copy or Putty if you just want a command line.  NX from nomachine dot com will give you a GUI to work with.

---

### Post by TonyDiF on 2010-11-29
> **sikander3786 said:**
> What do you intend to copy? Text or files/folders?

I'm looking to copy form a email message from my XP to a terminal window on my Ubuntu and the same in the other direction from my Ubuntu terminal window to my XP system email or notepad

thanks
TonyD

---

### Post by TonyDiF on 2010-11-30
> **TonyDiF said:**
> I'm looking to copy form a email message from my XP to a terminal window on my Ubuntu and the same in the other direction from my Ubuntu terminal window to my XP system email or notepad

thanks
TonyD

I'm not looking for file sharing bewteen my windows vista system and my Ubuntu box. What I would like to do is copy a line of text from an email or a document on my windows vista system and paste it to a terminal window on my Ubunu system. and then I would like to copy the output from my Ubuntu system back to my windows vista system. 

thanks
TonyD

---

### Post by BlueSpecial on 2010-11-30
Usually the VNC softwares (I use UltraVNC) have an option to "Sync Clipboards". Search for it. Probably you have that option disabled.

---

### Post by lukeiamyourfather on 2010-11-30
> **BlueSpecial said:**
> Usually the VNC softwares (I use UltraVNC) have an option to "Sync Clipboards". Search for it. Probably you have that option disabled.

This is both a client and server option if I remember correctly. If disabled on either end it won't work.

---

### Post by TonyDiF on 2010-11-30
> **BlueSpecial said:**
> Usually the VNC softwares (I use UltraVNC) have an option to "Sync Clipboards". Search for it. Probably you have that option disabled.
 
I'm running TightVnc with disbable clipboard transfer unchecked. If I run vncconfig my three options are all checked... I do not see anything for sync clipboard.
 
thanks
TonyD

---

### Post by sikander3786 on 2010-11-30
From the VNC FAQs page,

> Can I cut and paste between the viewer and the server?

    VNC supports copying and pasting of ASCII text in both directions, provided the viewer and server allow it. When the clipboard changes on the machine running the viewer, the changes are copied to the server and vice versa. Some notable exceptions:

        * X has more than one method of using the clipboard and different applications do it different ways. Emacs and xterm should just work. If you find that your X application doesn't work via VNC, you can generally use the xcutsel program to copy the clipboard between the different X methods. VNC uses Cut_Buffer0, so if you select text in Unix Netscape, for example, you may need to click 'Copy PRIMARY to 0' before it is accessible at the other end of the VNC link. You can use X resources to make the button labels more meaningful. For example, here's a script:

          #!/bin/sh
          exec xcutsel \
              -xrm '*quit.borderWidth:0' \
              -xrm '*quit.height: 1' \
              -xrm '*quit.label:' \
              -xrm '*sel-cut.label: Clipboard: out of netscape' \
              -xrm '*cut-sel.label: Clipboard: into netscape' \
                  -xrm '*font: -*-helvetica-*-r-*-*-*-*-*-*-*-*-*-*'

          Michael Witrant has written a program to do the transfer automatically. He writes:

          I'm glad to announce autocutsel version 0.1.

          People using xcutsel to copy/cut and paste between VNC and an X desktop might be interested with it. I was bored clicking on xcutsel's buttons to copy/paste between GTK apps on my VNC desktop and the Windows system running vncviewer.

          This tool regularly scans the primary selection and the cutbuffer 0. If one of them is changed, it updates the other one.

          I don't need xcutsel anymore and have a working cut and paste between GTK (through VNC) and Windows.

          You can get it there: [http://www.lepton.fr/tools/autocutsel](http://www.lepton.fr/tools/autocutsel)
        * Java applets running in the browser cannot access the clipboard of the machine on which they are running, so the Java viewer has a clipboard button. This pops up a window displaying the contents of the remote clipboard, which should allow you to manipulate it locally.


---

### Post by TonyDiF on 2010-12-01
> **sikander3786 said:**
> From the VNC FAQs page,
 
I installed autocutsel...  typed "autocutsel -s PRIMARY &" and I still can not copy and paste from my Ubuntu system to my windows XP system.  On my Ubuntu system I am on display 1 not display 0 if that makes a difference
 
thanks
TonyD

---

### Post by TonyDiF on 2010-12-02
> **TonyDiF said:**
> I installed autocutsel... typed "autocutsel -s PRIMARY &" and I still can not copy and paste from my Ubuntu system to my windows XP system. On my Ubuntu system I am on display 1 not display 0 if that makes a difference
 
thanks
TonyD
 
The solution is vncconfig needs to be running in the background so I added 
vncconfig -iconic & to my xstartup file

---

### Post by Habitual on 2010-12-02
gnome-rdp supports clipboard usage to and from the target.

---

### Post by TonyDiF on 2010-12-16
I found my solution... I need to add vncconfig -iconic  & to xstartup

---

