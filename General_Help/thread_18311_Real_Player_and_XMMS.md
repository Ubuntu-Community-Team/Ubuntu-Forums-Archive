---
title: "Real Player and XMMS"
date: 2005-03-05
forum: General Help
---

### Post by dqsis on 2005-03-05
Hello Ubuntu-Friends!

Just today, I installed RealPlayer10! 

But when I was asked to give the installation directory, I put
/usr/local instead of /usr/local/RealPlayer.

Now everyting lies not in a Real Player folder but free inside the /usr/local directory and it looks quite a mess. 

Do you know how can I fix this? I don;t even mind uninstalling the RealPlayer (not actually a big fan). 

Can also someone tell me how can I install the xmms-skins???

Thanks in advance!  :!:

---

### Post by landotter on 2005-03-05
sure, why don't you just make a directory called /usr/local/Realplayer and throw all those loose files in--you should be able to distinguish which belong to RP by looking at the "modified" date.

Then symlink /usr/local/Realplayer/realplay to /usr/bin/.

I do this with a GUI by running nautilus the file manager as root, then dragging the file with the middle mouse button, releasing and choosing "link".

It's like a shortcut in windows.

Since the symlink is in /usr/bin, it's considered "in your path" and can be run simply by typing the name "realplay" at a run prompt (alt + f2) or in a terminal. Also, when you create launchers on the taskbar or desktop, you just have to tell them to use "realplay" instead of /usr/bin/realplay...

Thinking about uninstalling? Try the BBC online media player and you'll quickly become realplayer addicted. :P

---

### Post by kassetra on 2005-03-06
[QUOTE=dqsis]Can also someone tell me how can I install the xmms-skins???[/QUOTE]

To install the skins that are in Warty's universe (make sure you have the repositories for universe enabled, if you don't know how to do that, ask me):
1. Open Synaptic (Computer->System Configuration->Synaptic Package Manager)
2. Click the Search button.
3. Type xmms-skins and press enter.
4. Right click on xmms-skins and then left click on Mark for Installation...
5. Click Apply.

Also, you might want to look at beep-media-player, it's essentially xmms for gnome 2+  It uses all the same skins and plugins.

---

