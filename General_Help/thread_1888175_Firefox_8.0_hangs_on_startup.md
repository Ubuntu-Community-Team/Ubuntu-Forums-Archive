---
title: "Firefox 8.0 hangs on startup"
date: 2011-11-28
forum: General Help
---

### Post by Myke Greywolf on 2011-11-28
I have a fresh, brand new Xubuntu 11.10 install that seems to be working nicely.

Big problem is, about half the times that I launch Firefox, it hangs on launch with a blank window.

If I open the task manager on that moment, I see that I have two Firefox processes running. If I kill the one that doesn't correspond to the window, the browser unhangs and goes to the home page normally. If I kill the window process, the other process stays in memory.

This happens even when I'm launching Firefox from the terminal. No "firefox" processes, then I type "firefox", and suddenly, there are two processes in memory, and a blank window on my desktop.

Other programs launch normally, including Chromium.

Does anybody have a clue as to why this may be happening?

Thank you in advance.

---

### Post by BC59 on 2011-11-28
I just inform you that when I use Firefox 8 I see only one process running (in Chrome e.g. i see various processes). So there is a problem with that.

Maybe you should reinstall Firefox.

```
sudo apt-get install --reinstall firefox
```

---

### Post by Myke Greywolf on 2011-11-28
Thank you for the suggestion, but no dice. Same thing still happens:

```
vitor@vitor:~$ ps -ef |grep firefox
vitor     7967  7913  0 22:54 pts/1    00:00:00 grep --color=auto firefox
vitor@vitor:~$ firefox &
[1] 7968
vitor@vitor:~$ ps -ef |grep firefox
vitor     7968  7913 15 22:54 pts/1    00:00:00 /usr/lib/firefox-8.0/firefox
vitor     7970  7968  6 22:54 pts/1    00:00:00 /usr/lib/firefox-8.0/firefox
vitor     7988  7913  0 22:54 pts/1    00:00:00 grep --color=auto firefox
vitor@vitor:~$ kill -9 7970
```

Only way to get it running, and this simply won't do. :(

---

### Post by bullfrogbues on 2012-01-22
Hi,

I have the very same issue, virtually identical to yours. I get 2 processes just like you do, and when I kill the one that doesn't correspond to the window, then firefox unhangs.

*Note : the issue persists with or without extensions and with or without plugins enabled. I have also had the same issue with other firefox versions.*

Details:
______________________________________________________________
Ubuntu 11.10 Oneiric (Unity)

[LIST]
[*]Firefox 9.0.1
[/LIST]
[INDENT]
[LIST]
[*]Extensions
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]
[LIST]
[*]NoScript (I don't actually have this installed right now, but did have it installed)
[*]Adblock PLus
[*]Firebug
[*]Firecookie
[*]FirePHP
[*]User Agent Switcher
[*]Web Developer
[*]YSlow
[*]Global Menu Bar Integration (unity)
[/LIST]
 
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]Plugins
[/LIST]
[/INDENT][INDENT][INDENT]
[LIST]
[*]Divx Web Player
[*]Gnome Shell Integration
[*]iTunes Application Detector (don't actually know why that's there)
[*]Shockwave Flash
[*]QuickTime (Totem)
[*]VLC Multimedia Plugin (Totem)
[*]Windows Media Player Plug-in (Totem)
[/LIST]
[/INDENT][/INDENT][INDENT]
[LIST]
[*]Languages
[/LIST]
[/INDENT][INDENT][INDENT]
[LIST]
[*]English (GB)
[*]English (South Africa)
[*]Irish (IE)
[/LIST]
[/INDENT][/INDENT]**ATI/AMD proprietary FGLRX graphics driver**

I mention this because I have a  feeling this might be where the problem is. 

I have just this morning updated this driver to the latest version *(I had an issue updating this before, as have others; on how to update it read  [http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem:](http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem:)  removing the current version, purging it, then installing the  post-release updates worked for me)*. 

After I updated and rebooted firefox hung, it was the first time firefox has ever hung directly after a reboot, though once I rebooted again firefox started fine.

Time will tell if updating this driver fixes this issue.

**Unity**

I've been using unity. I have gnome3 installed, but gnome's font rendering (among other graphic related issues) is dreadfull, I think it's an issue with 3D graphics and the FGLRX  driver, which I don't think is supported by gnome, and so gnome looks ****.

With that said, I am going to start using gnome more regularly to see if firefox hangs with that too.
________________________________________________________

I hope someone can shed some light on this, because I'm really hating firefox.





========= UPDATE ===========

Yes, I've been using gnome3 and firefox has not crashed or hung even once. So, it's either the ATI graphics card, unity or both that is causing the problem.

Dvd playback won't work properly without ATI drivers, but gnome can sometimes crash, freeze, hang when you have those drivers installed. And even if you're lucky enough not have a system crash, the screen flickers and shifts all the time. Gnome support, or ATI support for gnome (depending on which way you look at it) is really crappy. But then again, Gnome is a bit **** too.

Surprisingly, with all of the above said, I'm using gnome. Firefox hanging itself trumps all of gnomes and ATI's faults. I only use unity to watch dvd's.

---

### Post by LiSrt on 2012-02-20
For what it's worth, this is happening to me as well, and I'm using the ati drivers (in XFCE).

---

### Post by LiSrt on 2012-02-23
added report:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/939712](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/939712)

---

