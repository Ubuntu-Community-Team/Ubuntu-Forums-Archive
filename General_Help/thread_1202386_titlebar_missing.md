---
title: "titlebar missing"
date: 2009-07-02
forum: General Help
---

### Post by marean on 2009-07-02
Hello, I'm very new to ubuntu so I'm not even sure how to explain my problem. I just installed 9.04 netebook remix which looks superb but after a few days the top bar which contains the clock date and opened applications and the title bar from the windows don't appear when I reboot. I found away arround it by going into classic desktop and back but I'm hoping you guys might have a permanent soultions. I made 2 printscreens so you can see the problem[IMG]http://ubuntuforums.org/home/marian/Desktop/Screenshot.png[/IMG][IMG]http://ubuntuforums.org/home/marian/Desktop/Screenshot1.png[/IMG]

---

### Post by tvtech on 2009-07-02
I'm not sure what you mean by title bar?   I think you are referring to your window border, or decoration? This is something that can be turned on or off in compiz.  If you have compiz fusion make sure it's not turning it off.  Some older or insufficient video cards won't allow compiz to render the window borders.  I had on older laptop that compiz fusion worked great on except I lost all my window borders because it didn't have enough gas to re-render them. 

under compizconfig settings  >  check window decoration  and make sure it's working. 

whatever window manager you have running will control the window decoration, whether it's compiz metacity or something else. It sounds like it's been turned off.  

This should at least give you a point to start searching for a solution.

at any rate I'm not sure why but that "title bar"  is referred to as "window decoration" in some areas or "window border"  in others.  if you right click on your desktop background and customize your theme it's called "window border"

---

### Post by marean on 2009-07-02
I don't think its the graphics card since if I change the desktop mode from netbook to classic everything is fine adn even if I change back to netbook it works perfect. It's just at startup.
Look at the printscreens to see what's missing, I didn't know what to call them

---

### Post by adit on 2009-07-02
> Look at the printscreens to see what's missing, I didn't know what to call them
I agree.  Title bar is missing.

---

### Post by tvtech on 2009-07-02
> **adit said:**
> I agree.  Title bar is missing.

I understand what your saying. it's not referred to as a title bar in ubuntu I get that it's missing.  The reason it is missing is the window manager in ubuntu remix has either disabled it or.... your graphics card can't handle it.  the window manager is different in default ubuntu.  it's simple and doesn't do any special FX and is called metacity.  

check out what the windows manager is and how to configure it in netbook remix.  this will probably solve your problem.

---

### Post by LankyJames on 2009-09-22
Sorry to revive this old thread, only I have this exact problem currently.

It occurs having freshly installed UNR, then changing to classic desktop using desktop switching tool, then restarting.

Weirdly the title-bar is missing in either classic or UNR desktop 'mode', however switching to either one then back resolves the problem, it's just annoying that i have to do this each time i start up now just to have the title bar back!

---

### Post by Agent Smith on 2009-09-22
Hi, this is the fix you require to stop the missing title bars when switching between classic and remix desktops. I ran it whilst in classic mode and it fixed it fine. Now i can switch between desktops without problems.
 
[http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb)

Hope this helps Jon.

---

### Post by thefuturism on 2009-09-23
I had this exact problem earlier today. My bar with the time wasn't loading up, and I had no borders around my open applications.

I successfully fixed this problem by adding "gnome-panel" and "metacity --replace" commands to the startup applications.

---

### Post by TDK800 on 2009-09-23
same problem.... but can't type anything except ctrl+alt+del for restart... how can i add gnome-panel and metacity --replace to startup, copied gnome-panel to /etc/init.d/ but that didn't help

---

### Post by thefuturism on 2009-09-23
> **TDK800 said:**
> same problem.... but can't type anything except ctrl+alt+del for restart... how can i add gnome-panel and metacity --replace to startup, copied gnome-panel to /etc/init.d/ but that didn't help

I just found the "Startup Applications" in either Preferences, or Administration (I can't remember). Enter them both separately. "gnome-panel" as the code (and the name too if you like), and do the same with "metacity --replace"

---

### Post by Andysan on 2010-05-02
Hi,

I have the problem of window borders not appearing in lucid netbook remix when using classic desktop.

If I click and drag the window whilst holding down ALT the window borders reappear though when the window is resized.  I've tried all fixes suggested to no avail.  Metacity is listed as my window manager in gconf-editor under desktop>gnome>applications>window_manager.

Many thanks in advance.

---

