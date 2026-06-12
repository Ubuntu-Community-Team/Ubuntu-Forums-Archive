---
title: "Strange Netbook Remix Window Border Bug"
date: 2010-05-02
forum: General Help
---

### Post by Andysan on 2010-05-02
Hi All,

I've clean installed Lucid Netbook Edition and have been enjoying it until I started having a weird problem with my window borders not appearing for some (most) windows such a nautilus when using classic desktop.  Basically I'm getting my windows appear like the do when Maximus is running in the Netbook UI, but I obviously dont want this for the standard desktop.

Note the lack of a window border with minimize, maximize and close buttons:

[IMG]http://img.photobucket.com/albums/v54/Andysan/Screenshot-6.png[/IMG]

If I click and drag the window whilst holding down ALT the window borders reappear though only when the window is resized - if maximized the border dissapears. I've tried all fixes suggested in the following similar threads but to no avail:

* Calling killall maximus
* Tried calling metacity --replace
* Checked and Metacity is listed as my window manager in gconf-editor under desktop>gnome>applications>window_manager.
* When I check CompizConfig Window Borders are on, however (and this is really odd) when I try and click the screen just scrolls randomly up and down.  If I get lucky I can clear the checkbox to deactivate this but it immediately reticks the box (?).
* Installed desktop-switcher package.

Other similar threads (no one has exactly the same problem as me it would seem):

[http://ubuntuforums.org/showthread.php?t=1202386](http://ubuntuforums.org/showthread.php?t=1202386)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=641962](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=641962)


I dont have a Launchpad account or anything but am considering submitting this as a bug.  Does anyone have any idea how I can resolve this please?  

Many thanks in advance.

EDIT - I've checked in the system monitor and Maximus is indeed running, yet I cannot seem to kill it.  It would seem that this is running in the classic desktop when it shouldnt be.

EDIT - Appears there is already a bug for this :(
[https://bugs.launchpad.net/ubuntu/+source/desktop-switcher/+bug/430158](https://bugs.launchpad.net/ubuntu/+source/desktop-switcher/+bug/430158)

---

### Post by saxuntu on 2010-05-26
I'm not sure which of what I did fixed the problem but I have window borders again.  
I removed the following with synaptic:
netbook-launcher
netbook-remix-default
ubuntu-netbook-default settings
netbook-remix-default-settings

I also reset visual effects (Preferences-> Appearance-> Visual Effects tab) to Normal.  

I prefer to have compiz off, but I also prefer to have a working computer.  I don't know about you but I am really starting to get annoyed with these launch bugs.  Its one thing if its a little annoying issue, but not having window borders and therefore not being able to move windows or run multiple apps is really bad.

---

### Post by kaustik on 2010-05-26
I'm having the same problem but am not using the netbook edition.  It is pretty random and the only way I can get it back is with a logout/in or reboot.

---

### Post by saxuntu on 2010-05-26
After starting the computer back up I had to do the appearance and Normal effects checked.  The window borders popped back up.  I set it back to none and things stayed put.

EDIT: It doesn't have to stay at Normal.  I can click "Use Previous Settings" button and the boarders stay put.

---

### Post by saxuntu on 2010-07-25
So two months later I had a brainstorm and went to startup applications in the preferences menu.  i added compiz --replace as a startup and restart.  It seemed to have worked as a better work around than my previous method.

---

