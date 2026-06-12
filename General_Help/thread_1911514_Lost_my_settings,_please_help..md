---
title: "Lost my settings, please help."
date: 2012-01-19
forum: General Help
---

### Post by fallofshadows on 2012-01-19
Hey guys,

I'm running Ubuntu 11.10. Normally I use the Gnome shell (I can't stand Unity) and I was trying to update it to the most recent version (3.2). I ran a script a tutorial on a website suggested, and it downloaded and loaded *something* into my gnome shell. Now I can't change my desktop background, I've lost all my settings (I can no longer launch the terminal using the "right click" key on my Dell keyboard, etc) and overall I'm very not happy. Is there a way to revert Gnome back to how it normally ships with Ubuntu 11.10? I'm assuming that would restore my settings.

The commands I followed were:

sudo apt-get install -f

sudo apt-get install gnome-shell gnome-tweak-tool

The second command is when it downloaded a bunch of stuff and everything borked.

Thanks for your help, I'm pretty upset about this : P
fall

PS: What does the "-f" tag on the end of the command even do, anyways?

---

### Post by jerrrys on 2012-01-20
[B]apt-get install -f 
 apt-get upgrade -f 
 apt-get dist-upgrade -f[/B]  Attempt to fix dependencies while doing one of the above. Note that [FONT=FIXED]apt-get install -f[/FONT] does not require a <package> argument.

sudo apt-get install gnome-shell gnome-tweak-tool
This command downloaded gnome-shell (yes, a big package), but you say thats already installed.  Gnome-tweak-tool from what I understand (I run gnome-classic), is a must have.  If you are not using unity3d then you could remove compiz (sudo apt-get remove compiz-core).  This will replace unity 3d with unity2d.  Gnome-shell will not run under compiz.

---

