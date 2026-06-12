---
title: "How to build a task panel in Kubuntu"
date: 2012-04-07
forum: General Help
---

### Post by Ralph L on 2012-04-07
Because of the limitations of Unity and Gnome 3, I am thinking of switching to another linux distribution.  Currently I am looking at Kubuntu.  

Under Gnome 2 I could easily build a "task" panel consisting of a Main Menu button, a few application launchers (Nautilus, T-Bird, Firefox, Search), a Windows List (all the open windows), and a "tray" (Indicator Applet in gnome 2).  These were added by right-clicking an empty spot in the panel, selecting "add to panel", a picking the correct item from a fairly large list.

Under KDE when I right-click a panel I see "Add Widgets" and a few items pop up, but not nearly the number that pop up in Gnome 2.  In particular, I do not see a "Windows List", nor an "Indicator Applet" (tray).  However, I know that KDE has these items, because they were on a panel before I started fiddling with things, and accidentally removed them.

Would somebody please explain to me how to build a "Task Panel" in Kubuntu, and in particular add a Windows List and an Indicator Applet (tray) to the panel.

Any help very much appreciated!!

Ralph

---

### Post by SeijiSensei on 2012-04-07
If I click on the "cashew" at the right-hand end of the panel and choose Add Widgets, one of them is called "Window List".  Is that not what you want?  Maybe you're looking for the Task Manager widget instead?

I suggest you start over with a clean, default KDE desktop.  You can do this by renaming $HOME/.kde to something else like $HOME/.kde.old, then logging out and logging in again.  You'll get a default panel with the Task Manager and the System Tray widgets already installed.

I'm using 12.04b2 at the moment, but these features have been part of KDE4 for quite a while now.

---

### Post by Zorael on 2012-04-08
Something akin to this?

[img]http://i.imgur.com/oYZxh.png[/img]

As SeijiSensei said, the easy way to manage panels is by clicking the cashew, which is only visible if widgets are unlocked. Going from the left of that screenshot, the widgets are:
[list][*]Application Launcher Menu (classic)
[*]Quick Access (closest equavilent to Places that I could find in the repos)
[*]Amarok and Chromium launchers added by right-clicking their entries in the Application Launcher and choosing Add to Panel
[*]Task Manager
[*]Pager
[*]System Tray
[*]Digital Clock
[*]Fast user switch[/list]
These are (all?) part of the [**plasma-widgets-workspace**](apt://plasma-widgets-workspace) package, so they should be available unless you somehow managed to remove that one.

If you think the widget list is lacking, note that there are a few extras available in the repositories that aren't installed by default. List of every package beginning with **plasma-widget** (admittedly from 12.04 repos);
```
plasma-widget-activitymanager        plasma-widget-lancelot               plasma-widget-simplemonitor
plasma-widget-adjustableclock        plasma-widget-lastmoid               plasma-widget-stockquote
plasma-widget-bkodama                plasma-widget-mail                   plasma-widgets-workspace
plasma-widget-cpuload                plasma-widget-makestatus             plasma-widget-teacooker
plasma-widget-cwp                    plasma-widget-memusage               plasma-widget-telepathy-contact
plasma-widget-drop2ftp               plasma-widget-menubar                plasma-widget-telepathy-contact-dbg
plasma-widget-facebook               plasma-widget-message-indicator      plasma-widget-telepathy-presence
plasma-widget-fastuserswitch         plasma-widget-networkmanagement      plasma-widget-tictactoe
plasma-widget-flickr                 plasma-widget-networkmanagement-dbg  plasma-widget-toggle-compositing
plasma-widget-folderview             plasma-widget-nextwallpaper          plasma-widget-translatoid
plasma-widget-fortunoid              plasma-widget-on-off-switch          plasma-widget-tvprogramme
plasma-widget-googlecalendar         plasma-widget-pgame                  plasma-widget-uim
plasma-widget-kbstate                plasma-widget-plasma-netgraph        plasma-widget-veromix
plasma-widget-kdeobservatory         plasma-widget-playwolf               plasma-widget-weatherforecast
plasma-widget-kepas                  plasma-widget-quickaccess            plasma-widget-wifi
plasma-widget-kimpanel               plasma-widget-runcommand             plasma-widget-yawp
plasma-widget-kimpanel-backend-ibus  plasma-widgets-active                plasma-widget-yawp-dbg
plasma-widget-ktorrent               plasma-widgets-addons                
plasma-widget-kubuntu-feedback       plasma-widget-searchmoid
```
Some of these may come from the kubuntu ppas, I'm not sure.

Another thing worthy of mention is the [Plasma Panels Collection](http://kde-look.org/content/show.php/Plasma+Panels+Collection+?content=147589) addon, which contain several presets for different kinds of panel types. See [this youtube clip](https://www.youtube.com/watch?v=LYzEty1TYAE). Sadly it needs to be installed manually and cannot be just chosen from the Get New Widgets menu. (Which you also shouldn't miss!)

---

