---
title: "xdotool/xautolock keycombinations."
date: 2011-11-14
forum: General Help
---

### Post by dzon65 on 2011-11-14
I've added a show desktop entry in my openbox menu using: xdotool key super+d
However, I'd like to toggle the desktop with an edgebinding using xautolock. For instance,I use the left bottom corner to launch skippy, like so autolock -locker  "xte 'key F5'" -corners 00+0  -cornerdelay 0 &
Here's the prob. I can't seem to add keycombinations ( in this case W-d, or Super+d...) to either xdotool or xautolocker.
Neither adding the keycombination works in a bash. It only works with a single key. For example:#!/bin/sh
xte 'key F5'
What am I missing here?

---

### Post by dzon65 on 2011-11-14
Okay, found a solution. Replacing "xte 'key F5" with "xdotool key super+d" does the trick.
I added a launcher to my tint2 panel cause xautolock seems a bit slow.
If someone's intrested, add something like this script to the openbox autostart file:


#!/usr/bin/env python

# Show desktop system tray launcher for use with Openbox & tint2 (or other panels)

import gtk
import os

class StatusIcon:
    def __init__(self):
        self.statusicon = gtk.StatusIcon()
        self.statusicon.set_from_file("/home/john/.icons/Fbicons/1.png")
        self.statusicon.set_tooltip("Desktop") 
    
        self.statusicon.connect("activate", self.left_click_event)
        self.statusicon.connect("popup-menu", self.right_click_event)
        
    def right_click_event(self, icon, button, time):
        menu = gtk.Menu()
        about = gtk.ImageMenuItem(gtk.STOCK_ABOUT)
        quit = gtk.ImageMenuItem(gtk.STOCK_QUIT)
        
        about.connect("activate", self.show_about_dialog)
        quit.connect("activate", gtk.main_quit)
        
        menu.append(about)
        menu.append(quit)
        
        menu.show_all()
        
        menu.popup(None, None, gtk.status_icon_position_menu, button, time, self.statusicon)
    
    def left_click_event(self, event):
        os.system('xdotool key super+d')
    
    def show_about_dialog(self, widget):
        about_dialog = gtk.AboutDialog()

        about_dialog.set_destroy_with_parent(True)
        about_dialog.set_program_name(" Show Desktop Icon")
        about_dialog.set_version("0.1")
        about_dialog.set_comments('A simple system tray icon so that you can show the desktop and iconify all open windows.\n\nDesigned specifically for tint2 and Openbox.\n\nYou will need the keybinding Super+D set up to ToggleShowDesktop in your Openbox rc.xml, but this is the default.')
        about_dialog.set_authors(["richjack, 2010 \nReleased under GPL v2 or later"])
                
        about_dialog.run()
        about_dialog.destroy()

StatusIcon()
gtk.main()

And point towards it in the openbox autostart file.

You can add anything you want to tint with this.

---

