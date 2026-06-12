---
title: "Xubuntu - No Manual?"
date: 2006-02-26
forum: General Help
---

### Post by fishmorg909 on 2006-02-26
I just installed the Xubuntu desktop on my old Dell Optiplex, and it really cooks! A very nice increase in speed. But the manual won't come up. When I click on the 'Manual' button, I get an error message:

Unable to execute browser.
Online help is not available.

Is there a fix for this?

---

### Post by xequence on 2006-02-26
Maybe it is trying to take you to a web site, but you dont have a browser?

Or im wrong if you are posting from that computer, which means you have a browser on it :P

---

### Post by fishmorg909 on 2006-02-26
Hmm -- on the taskbar, there's a launcher for Mozilla browser... but I don't have Mozilla, I'm using Firefox 1.5 -- could the Manual be set for Mozilla? If so, how can I correct this?

---

### Post by stuporglue on 2006-02-26
Right click the help button, and you can see/edit the command it runs.

---

### Post by 5-HT on 2006-02-26
[QUOTE=fishmorg909]
Is there a fix for this?[/QUOTE]

Hi, the documentation should be stored in: /usr/share/xfce4/doc//C/index.html

So, you can either:

1) Open up any browser and read the file by entering its path.

2) Go to: XFCE menu > Settings > XFCE4 Menu Editor

Find the 'Help' and edit that command to something like:

<browser> /usr/share/xfce4/doc//C/index.html

Where <browser> is the executable to the browser you'd like to use and have installed.

For me with FireFox, it would look like this for example:

firefox /usr/share/xfce4/doc//C/index.html.



Looks like for whatever reason, the help docs aren't getting passed to your browser. Mine opens up in FireFox, but I did select FireFox 1.5 as the default browser in GNOME (not sure if there is a similar function in pure XFCE).

Hopefully, 2) should fix it so it seems integrated.

Hope that helps.

---

### Post by fishmorg909 on 2006-02-26
In Properties for the Help launcher, it just says "xfhelp4" -- sounds like the help files should be on my computer, but it can't find them.

As an aside, I was looking at ways to sped up the desktop, I got Openbox, then was wondering how to get XCFE... then I realized that Xubuntu was sitting ther right in front of me, for the asking! (Duh.) ;)

---

### Post by 5-HT on 2006-02-26
[QUOTE=fishmorg909]In Properties for the Help launcher, it just says "xfhelp4" -- sounds like the help files should be on my computer, but it can't find them.
[/QUOTE]

From my last post, something seems amiss with XFCE recognizing your default browser.
The help files should be there (double check the path I gave...are they there?), its just that we need to let XFCE know how and where to read them.

If you've got a symlink to FireFox in /usr/bin or have its executable in your path (i.e., if typing 'firefox' at a prompt opens up the program), then if you edit the command for xfhelp4 to read ```
firefox /usr/share/xfce4/doc//C/index.html 
``` (within XFCE Menu Editor, my last post gives instructions) you should have a nice, integrated help menu.

HTH

---

### Post by fishmorg909 on 2006-02-26
I just missed seeing your previous answer, 5-HT, and your path to the help is right on the money. I just made links to it in FF, and also made Dillo browser the default app for the help files. What a difference from Gnome on this ol' box... had to wait and wait for help, but with XCFE/Dillo, zoom! The help appears right away. :D 

(Dillo is very light browser available in Synaptic.)

---

### Post by 5-HT on 2006-02-26
Glad you got it working.
Sorry, didn't know if you saw the first post at all.
Yeah, Dillo and XFCE should make a nice combo.:p 

Also, if you haven't looked around too much at the XFCE panel items, there are a bunch of relatively lightweight helpful ones in there.

---

