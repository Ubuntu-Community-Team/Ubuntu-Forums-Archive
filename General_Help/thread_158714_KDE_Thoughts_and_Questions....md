---
title: "KDE Thoughts and Questions..."
date: 2006-04-11
forum: General Help
---

### Post by LightsOut on 2006-04-11
Recently I installed KDE on a whim because I was looking through the screenshots and I liked what I saw. I had gnome running perfectly and I liked it alot before this. However, KDE seems to be waaaay snappier(faster) than gnome. Gnome seems to have a lag and imo was a resource hog, both of which are non-existant problems in KDE. Only problem i've had with kde is that i've gotten firefox to crash a couple times (if I liked things crashing on my all the time i woulda stayed with windows!). So if any of you guys think that gnome is a little slow then try KDE, you wont be dissapointed. I do have a couple questions however:

1. Sometimes when I try to restore a program from the taskbar by pressing on it's respective box ALL the programs running in the taskbar are restored. This is annoying how can I disable this?

2. Is there a way to make the menu with all the programs (when you click on the K) transparent? 

3. Can i use network manager in KDE? The kwifimanager doesn't work for me so I have to boot up gnome first to get my wifi connection then log out and into KDE. 

4. Is there a way to install superkaramba through YUM? It wasn't in the kde repo and I get an error when I try to ./configure superkaramba.

Thanks alot guys.

---

### Post by Ptero-4 on 2006-04-11
2. To make the kmenu (the menu with the programs on it) transparent you need to enable compositing in x.org (I'm on OSX right now and can't recall what you need to put in the /etc/X11/xorg.conf file), restart X11 and then enable the KDE's built-in compositing manager and set the transparency levels.

3. Yes you can use it. You'll need to know the name of the network manager's executable file to type it in the KDE's run box.

4. Superkaramba is in the universe repository. Open /etc/apt/sources.list (use sudo to gain root access) and uncomment all the repositories in it, then run apt-get update and you'll be able to install superkaramba. And ubuntu doesn't use YUM. It's for YellowDog.

---

### Post by MartinG on 2006-04-11
If it's ONLY the K menu you want to be transparent you can do this without compositing:
System Settings->Panel->Panels->Appearance, and tick the Panel background - Enable transparency box. Use Advanced settings to control it.

---

### Post by jdong on 2006-04-11
The K menu can be made translucent without compositing, but not entire windows.

As far as network manager from KDE, yes, the GNOME network manager works inside KDE (ALT+F2, nm-applet). In Dapper, there is network-manager-kde, which is a proper KDE integrated version of network manager. So, just sit tight for another month and week or so.

---

### Post by ace2005 on 2006-04-11
[QUOTE=LightsOut]2. Is there a way to make the menu with all the programs (when you click on the K) transparent? 

3. Can i use network manager in KDE? The kwifimanager doesn't work for me so I have to boot up gnome first to get my wifi connection then log out and into KDE. 
[/QUOTE]

Well for the transparent menu:

Alt+F2 > Type: kcontrol > Appearence and Themes > Style > Effects (tab at the top) > Menu Effect (4th dropdown box), select "Make Translucent" and then change the settings at the bottom.

As for the network if you know the command run by gnome to start your network you can have it run at KDE startup, i use [http://www.kde-look.org/content/show.php?content=32517](http://www.kde-look.org/content/show.php?content=32517) (Autostart addon for Kcontrol) to manage my startup items.

---

### Post by sendgift2008 on 2006-04-11
[[img]http://www.top22.cn/QQCF_Pic/QQCf_Style12.gif[/img]](http://www.top22.cn/qqcf.asp?46.sendgift2050)

---

### Post by njf on 2006-04-12
I want to ask about the translucent effect of menu. If I click on the menu, then "browse" fast, I can see some artifacts. Is there a way to fix that?
I'm using ati m radeon x700.

---

### Post by incubus on 2006-04-12
I tried to replicate problem #1, but failed to do so. Minimized all, some, and just one, but still clicking on its taskbar box just affects that particular window.

Maybe something's wrong with the config there.

incubus

---

### Post by ace2005 on 2006-04-12
[QUOTE=njf]I want to ask about the translucent effect of menu. If I click on the menu, then "browse" fast, I can see some artifacts. Is there a way to fix that?
I'm using ati m radeon x700.[/QUOTE]

I have that problem too, its a bug in KDE i think.

And about minimizing thing, you wouldn't happen to be in another desktop would you? just to test it, right click on the bottom pannel > Configure Panel > Taskbar > and untick show from all desktops at the top. This might do the trick

---

