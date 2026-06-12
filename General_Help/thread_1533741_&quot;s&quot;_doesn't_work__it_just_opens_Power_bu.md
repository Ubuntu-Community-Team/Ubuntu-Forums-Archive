---
title: "&quot;s&quot; doesn't work  it just opens Power button.."
date: 2010-07-18
forum: General Help
---

### Post by mr epic on 2010-07-18
[[IMG]http://img708.imageshack.us/img708/8725/sisntworking.png[/IMG]]("http://img708.imageshack.us/i/sisntworking.png/")
 
Please help me.

---

### Post by dino99 on 2010-07-18
into a console, one by one:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

metacity --replace

---

### Post by mr epic on 2010-07-18
> **dino99 said:**
> into a console, one by one:
 
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
 
metacity --replace
what should i do with the metacity --replace?
 
and what next?

---

### Post by mr epic on 2010-07-18
[[IMG]http://img708.imageshack.us/img708/8725/sisntworking.png[/IMG]]("http://img708.imageshack.us/i/sisntworking.png/")

---

### Post by valvegrid on 2010-07-18
Have you tried another keyboard in case the one that one is faulty?

---

### Post by ajgreeny on 2010-07-18
Presumably you have looked in System ->Preferences ->Keyboard Shortcuts?  I can't imagine why it should be set there as a shortcut, but it is the first place to look.

---

### Post by Iowan on 2010-07-18
Threads merged

---

### Post by mr epic on 2010-07-18
> **ajgreeny said:**
> Presumably you have looked in System ->Preferences ->Keyboard Shortcuts? I can't imagine why it should be set there as a shortcut, but it is the first place to look.
 
Yes i've looked through the keyboard Shortcut from top to bottom and nothing do to with "S" key as a keyboard shortcut even though it is :(, it only shows Alt/Ctrl keyboard shortcuts.
 
Please help me with this, as my brand new vps is wasted.
Thanks..

---

### Post by RJARRRPCGP on 2010-07-18
Probably a bad keyboard. Sorry. :(

---

### Post by mr epic on 2010-07-19
> **RJARRRPCGP said:**
> Probably a bad keyboard. Sorry. :(
No, because my friend was also expercing this problem and we both use the same vnc, but when we used Linux before the "S" key wasn't a problem.
 
EDIT: do you rekcon it depends on which version I get? do others experience this problem? if so tell me what version to get.

---

### Post by arsenic23 on 2010-07-19
You are going to have to be a little more verbose in explaining your issue.  You are using VNC?  How is it setup?  Does the problem persist outside of VNC?  What version of Ubuntu do you have installed.  What language?  Is the keyboard special in any way?  Are you sure you have the keyboard layout set correctly?

---

### Post by mr epic on 2010-07-19
> **arsenic23 said:**
> You are going to have to be a little more verbose in explaining your issue. You are using VNC? How is it setup? Does the problem persist outside of VNC? What version of Ubuntu do you have installed. What language? Is the keyboard special in any way? Are you sure you have the keyboard layout set correctly?
 
1. I can't change the keyboard layout for some reason :(
 
2. Yes i'm using VNC
 
3. No the problem is only on the Ubuntu OS nothing else.
 
4. My version is: [SIZE=2]Ubuntu 10.04 lamp 64 bit[/SIZE]

---

### Post by mr epic on 2010-07-19
Oh yea, i followed this guide on how to install it:
[http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/](http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/)
Hope it helps...

---

