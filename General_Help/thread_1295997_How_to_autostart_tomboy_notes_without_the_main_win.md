---
title: "How to autostart tomboy notes without the main window opening when computer starts"
date: 2009-10-20
forum: General Help
---

### Post by dj-toonz on 2009-10-20
Hi all, I'm trying to get Tomboy notes to autostart on system start up & place a icon next to the network-manager icon like it does under Fedora, I've gone into the System , Preferences, Startup Applications & added tomboy into there, but when I reboot the desktop, the main window for Tomboy notes opens up & when I click on the X to close the window. tomboy shuts down :-(. how can I get tomboy notes to open without the main window & just place a icon in the Notification Area? as I use tomboy notes a lot, to add, system commands & other things what I find out during the course of the day. cheers

---

### Post by stinkeye on 2009-10-20
> **dj-toonz said:**
> Hi all, I'm trying to get Tomboy notes to autostart on system start up & place a icon next to the network-manager icon like it does under Fedora, I've gone into the System , Preferences, Startup Applications & added tomboy into there, but when I reboot the desktop, the main window for Tomboy notes opens up & when I click on the X to close the window. tomboy shuts down :-(. how can I get tomboy notes to open without the main window & just place a icon in the Notification Area? as I use tomboy notes a lot, to add, system commands & other things what I find out during the course of the day. cheers
Don't autostart. Just add it to the panel as an applet.

---

### Post by dj-toonz on 2009-10-20
I didn't think of that cheers, but not really want I wanted to do :-( I wanted it to go into the notification area as when I now click on the Icon in the panel, it's not the proper note, only a little white box & i can't add html code, but if I open it from the Applications menu, it opens the full version of tomboy notes (which is the one I want to use) not the light-weight version of notes :-(, funny how on Fedora it starts as default with out the main window on start up but the main window shows up under Ubuntu. If somebody else can think of a way for Tomboy Notes to start in the Notification area *without the main window open* i would be most grateful

---

### Post by Lars Noodén on 2009-10-20
> **stinkeye said:**
> Don't autostart. Just add it to the panel as an applet.

Also, take [Gnote](http://live.gnome.org/Gnote) for a spin.  The performance is much better and there are other improvements.

There are also other projects which are worth looking at:
[list]
[*][BasKet](http://live.gnome.org/Gnote) is very nice.  
[*][Knotes](http://pim.kde.org/components/knotes.php) is simple and to the point.
[*][Zim](http://zim-wiki.org/) is a desktop wiki.  So if you like wikis, zim rocks.
[/list]

---

### Post by stinkeye on 2009-10-20
> **dj-toonz said:**
> I didn't think of that cheers, but not really want I wanted to do :-( I wanted it to go into the notification area as when I now click on the Icon in the panel, it's not the proper note, only a little white box & i can't add html code, but if I open it from the Applications menu, it opens the full version of tomboy notes (which is the one I want to use) not the light-weight version of notes :-(, funny how on Fedora it starts as default with out the main window on start up but the main window shows up under Ubuntu. If somebody else can think of a way for Tomboy Notes to start in the Notification area *without the main window open* i would be most grateful
Did you add tomboy or sticky notes to the panel?

---

### Post by dj-toonz on 2009-10-20
Both ways, I added sticky notes first to try that & was rubbish then I dragged Tomboy Notes from the application menu to the panel & clicked on it, then it went into the notification area & the main window opened, then i closed the main window (stayed in the notification area, but on system startup it doesn't start the program :-(. I want it like it used to do when I was using fedora 11. Start in the notification area **without the main window popping up every time I start gnome** It can be done as when I first installed fedora, tomboy notes was in the notification area without the main window with all the notes showing up & even re-starting gnome, the main window didn't show up, that's what I'm trying to figure out how to do, but in ubuntu I can get tomboy to start up with gnome, but the main window opens up aswell, if that makes sense. I've posted in the fedora forums aswell to see if somebody can have a look in the start up applications for the right command,cheers

---

### Post by stinkeye on 2009-10-20
> **dj-toonz said:**
> Both ways, I added sticky notes first to try that & was rubbish then I dragged Tomboy Notes from the application menu to the panel & clicked on it, then it went into the notification area & the main window opened, then i closed the main window (stayed in the notification area, but on system startup it doesn't start the program :-(. I want it like it used to do when I was using fedora 11. Start in the notification area **without the main window popping up every time I start gnome** It can be done as when I first installed fedora, tomboy notes was in the notification area without the main window with all the notes showing up & even re-starting gnome, the main window didn't show up, that's what I'm trying to figure out how to do, but in ubuntu I can get tomboy to start up with gnome, but the main window opens up aswell, if that makes sense. I've posted in the fedora forums aswell to see if somebody can have a look in the start up applications for the right command,cheers
What I mean is not drag to panel but right click on panel > add to panel
and add the Tomboy [COLOR="DarkRed"]applet[/COLOR].I know it wont be in the notification area but you can sit it next to it.
The applet starts tomboy at startup and has all the normal functions.

---

### Post by dj-toonz on 2009-10-20
> **stinkeye said:**
> What I mean is not drag to panel but right click on panel > add to panel
and add the Tomboy [COLOR="DarkRed"]applet[/COLOR].I know it wont be in the notification area but you can sit it next to it.
The applet starts tomboy at startup and has all the normal functions.

Cheers for that, I've found Tomboy notes now. It was right at the bottom :(. I don't know if it was in the panel or notification area in fedora but It was always showing up like it is now. I've got the Create new note & all the other icons for it on left click so I'm happier now cheers. I didn't think to check for that as I was still thinking fedora ways & why ubuntu didn't just add it like fedora did :(. cheers, so It's [SOLVED] now thx again

---

### Post by stinkeye on 2009-10-20
> **dj-toonz said:**
> Cheers for that, I've found Tomboy notes now. It was right at the bottom :(. I don't know if it was in the panel or notification area in fedora but It was always showing up like it is now. I've got the Create new note & all the other icons for it on left click so I'm happier now cheers. I didn't think to check for that as I was still thinking fedora ways & why ubuntu didn't just add it like fedora did :(. cheers, so It's [SOLVED] now thx again
I think it used to start in the way you described before they brought out the applet option.
Anyway we got there.](*,):mrgreen:
Good luck.

---

### Post by fbianconi on 2010-08-05
I've been looking for this for a while now, so I'll post here what I've found, don't know if it was like this when this thread started, but in lastest ubuntu (10.04) goes like this:
Open an instance of startup applications, then drag the tomboy launch item from the applications menu, and then edit the launcher inside startup programs. Where it says command: "tomboy --search" should say just "tomboy" and voila. Now the icon will be in notification area in grey, not yellow.

---

