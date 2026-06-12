---
title: "Several wallpapers and Screenlets not minimizing"
date: 2009-11-24
forum: General Help
---

### Post by Raff1 on 2009-11-24
Hello! Today I have been working on getting my compiz cube to display individual wallpapers for the different workspaces. As a result I needed to add Screenlets to my desktop in order to make it show its contents again (due nautilus not drawing it, see below). And I needed to set them up to _*not*_ minimize when I click the *show desktop* button (Ctrl + Alt + D).

I have gathered the information I needed in all sorts of threads and I am *_nearly_* finished with configuring this now. (I still need some details at stage 3 below!) The threads dealing with both the several wallpapers issue and the minimizing screenlets issue were both numerous and often not satisfactory or seemed fragmented to me. I therefore made this thread in an attempt to collect the information I have used in one place and showing how I finally did it.

This had been tested on my Ubuntu 9.04 Jaunty and I would welcome any feedback on how this works on 9.10 Karmic as well as I might upgrade (fresh) at some point.

I will break this down in several stages since you might be interested in only parts of the issues I will be dealing with. Feel free to try jump to the stage that is in your interest. I really hope this will be of any help! :D

Stage 1: Getting several wallpapers to work
Stage 2: Adding screenlets to the desktop (displaying desktop contents again)
Stage 3: Preventing screenlets from minimizing
Needs to be fixed: Things yet to be done

**Stage 1:** *Getting several wallpapers to work*

_NOTE: This stage will make desktop icons and interactions disappear!_ A suggested workaround is given in stage 2.

In order to do this you must get the CompizConfig Settings Manager (CCSM). This can be found under (Applications > Add/Remove...) and then search for "compiz".
Alternatively: ```
sudo apt-get install compizconfig-settings-manager
```The rest of this stage is basically taken from [here]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/") or [here]("http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu"),  so feel free to follow one of those instead and jump stright to stage 2. 

Now you need to launch CCSM (System > Preferences > CompizConfig Settings Manager) and under the catergory "Utility" you will find "Wallpaper". Make sure this is ticked/activated and click on it to set up its options.

Under the "General" tab navigate to "Backgrounds" and add all the images you want to use with "_N_ew". If you have fewer images than workspaces it will reuse the images from the beginning.

Now you need to make nautilus stop drawing the the pre-existing background (together with the rest of your stuff at the desktop(!!) See Stage 2 for a solution) in order to make the backgrounds you set in CCSM appear:

Open a terminal (or you can press Alt+F2) and type:
```
gconf-editor
```Navigate to (apps > nautilus > preference) and deselect "Show Desktop".

**Stage 2:** *Adding screenlets to the desktop (displaying desktop contents again)*

The problem introduced from Stage 1 is that your shortcuts and folders arent drawn on the desktop by nautilus any longer. My solution to this was to add a screenlet to my desktop displaying the contents of the desktop folder. You can actually show the contents of several folders side by side this way, and whichever folders you want. _This made my desktop get the KDE-look_ (which I like!). But it was possible to change the theme making everything _look_ just like before. (Some degree of interaction is lost, see bottom of this stage below.)

You need to add the Screenlets application
(Applications > Add/Remove...) and search for "screenlets".

Now you need to get the FolderView screenlet which can be found as a tar-ball [here]("http://www.gnome-look.org/content/show.php/Folderview+Screenlet?content=102890")

From the Screenlets Manager (Applications > Accesories > Screenlets) you select "Install" and "Install Screenlet" and browse the FolderView tar-ball.

Now you can add FolderView screenlets from the Screenlets Manager which will appear on your desktop. Make sure you tick/select the "Auto start on login" for FolderView. You might also want to select the "keep below" option for FolderView under "Options", so that it will always be under your other documents and stuff.

Now right-click FolderView screenlet propably showing you home-folder contents and select (Properties > Options > Folder) and set "Folder Path" to your desktop folder.

Under "Theme" you can select 1280x800_d_esktop to make it look more similar to before (at least with my resolution). However, I like it better the default (KDE-looking) way.

Under "Window" you can select "Sticky" to make the folder appear on every workspace.
However, I dont know how to make this Sticky option to be remembered next time I log in, so I have to tick it every time. I found a thread regarding it here.

A drawback as far as I can see is that _you will not be able to interact with the icons in your folder the same way as usual_. You will only be able to open files and folders, not creating new one or renaming them. This can still be done from the ~/Desktop folder.

As you might notice, any screenlets will be minimized along with all your windows then you show desktop (Crtl + Alt + D). That is no good when you need to minimize your stuff too get to the desktop contents in the first place! So I found a fix that worked for me in the next stage.


**Stage 3:** *Preventing screenlets from minimizing*

I found out how to resolve this problem [here]("https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/217507"), and I haven't experienced drawbacks from it yet, even thought the fix is a bit dirty. There are also other ways to achieve this effect, including stuff like the Compiz widget layer and setting your screenlets as widgets, but I never really got the result I wanted and the approach was rather messy anyways. (I am not saying my suggested approach is not messy, it is, but the results were at least neat.)

Localize __init__.py for screenlets.
I found it in /usr/lib/python2.6/dist-packages/screenlets/__init__.py and opened it with gedit:
```
sudo gedit /usr/lib/python2.6/dist-packages/screenlets/__init__.py
```Change the line (ln 814 for me) saying
```
            self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_TOOLBAR)
```to 
```
            #self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_TOOLBAR)
            #Workaround. Swich comments to undo:            
            self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
```Save and restart. (Log out and in might do.) Now you should be able to minimize everything but your screenlets!

**Needs to be fixed:** *Things yet to be done*

I have not been able to fix everything so far. I have a setting I can live with, but some details needs to be fixed before I can be satisfied. *I really hope someone can help me with this*. Those issues are:

My Screenlet settings, like the "sticky" option keeps reseting themselves on startup, so that I need to tick the options every time I log in in order to keep my "desktop" present in every workspace.

I want to make the New Screenlet Attributes (Screenlets Manager > Options) set to "keep below" for *all* screenlets as default. It remembers this option for any screenlets I have used, but I still have to set it individually for every new screenlet I use.

When I close a couple of screenlets like sticky notes and log out and in again, the ones I closed still appear! I have selected "Auto start at login" for these, but I would only like it to start what was actually present when i logged out (obviously).

Any help with these issues will be accepted with many thanks!

Regards,
Raff1

---

### Post by Raff1 on 2009-11-24
> **Raff1 said:**
> 
A drawback as far as I can see is that _you will not be able to interact with the icons in your folder the same way as usual_. You will only be able to open files and folders, not creating new one or renaming them. This can still be done from the ~/Desktop folder.


If someone knows a way to achieve this (Stage 2) without this obvious drawback I would be happy to know about it! An alternative screenlet with more of the features from nautilus perhaps?

---

### Post by Raff1 on 2009-11-25
> **Raff1 said:**
> 

When I close a couple of screenlets like sticky notes and log out and in again, the ones I closed still appear! I have selected "Auto start at login" for these, but I would only like it to start what was actually present when i logged out (obviously).


I had to disable the "auto start at login" option for those screenlets to make them stop reappearing. Does anyone know whats wrong?

---

### Post by Raff1 on 2009-11-25
B/u_m\p

---

### Post by mastaowen on 2011-07-26
just do this:
[B]from terminal-> gconf-editor
next:  

apps->compiz->general->allscreens->options->hide_skip_taskbar_windows (unmark)
and will be all right.
[/B]

---

