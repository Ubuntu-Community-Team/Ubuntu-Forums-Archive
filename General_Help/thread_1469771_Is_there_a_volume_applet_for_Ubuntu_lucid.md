---
title: "Is there a volume applet for Ubuntu lucid?"
date: 2010-05-02
forum: General Help
---

### Post by johann_p on 2010-05-02
I am missing a volume/sound applet for the GNOME panel. The only way to do this I found is the indicator applet, but this also shows an email icon which takes up space and does not seem to be removable. 
I do not want that networking stuff and I use Thunderbird as my email client. 
So, is there a way to just get a volum applet?

---

### Post by garvinrick4 on 2010-05-02
> **johann_p said:**
> I am missing a volume/sound applet for the GNOME panel. The only way to do this I found is the indicator applet, but this also shows an email icon which takes up space and does not seem to be removable. 
I do not want that networking stuff and I use Thunderbird as my email client. 
So, is there a way to just get a volum applet?
System to Preferences to Sound to right click to add this launcher to panal.

Or you can get the whole kit and kaboodle by adding Code.

sudo apt-get install padevchooser

It will show up in Applictions to Sound and Video right click on it and add this to launcher to panel.

---

### Post by m2xtreme on 2010-05-02
garvinrick4, i tried following your instructions but now i get the following error message in my notification area:

An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: ' Unknown Error: '<type 'exceptions.SystemError'>' (E:Opening configuration file /etc/apt/apt.conf.d/99synaptic - ifstream::ifstream (13: Permission denied))'This usually means that your installed packages have unmet dependencies

have any idea on how to fix it?  I can't even run Update Manager now :(

---

### Post by mike555 on 2010-05-02
I found this when I was in search of a resolution to the same problem. And it seems to work:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

---

### Post by m2xtreme on 2010-05-02
mike555, your method worked perfectly, thank you!  Do you think this could be a bug or was it intentionally left out of lucid?

Now if i could only undo the damage done by running: sudo apt-get install padevchooser  :confused:

---

### Post by mike555 on 2010-05-02
I think they did it on purpose , guess they thought everyone wanted an envelope looking icon that does nothing useful and is  connected to the volume icon .....

---

### Post by scouser73 on 2010-05-02
> **m2xtreme said:**
> mike555, your method worked perfectly, thank you!  Do you think this could be a bug or was it intentionally left out of lucid?

Now if i could only undo the damage done by running: sudo apt-get install padevchooser  :confused:

You can either right click and remove the applet or enter this command into Terminal: **> sudo apt-get autoremove padevchooser**

---

### Post by garvinrick4 on 2010-05-02
> **mike555 said:**
> I think they did it on purpose , guess they thought everyone wanted an envelope looking icon that does nothing useful and is  connected to the volume icon .....
I did nothing on purpose "padevchooser is the PulseAudio Device Chooser that allows you
to open all functions and preferences in your Audio. Look it up in Ubuntu Software Center
or Synaptic or even below: Some should Know what they are speaking before they speak.
Giving someone bad code on purpose is a vile action.

rick@rick-laptop:~$ aptitude show padevchooser
Package: padevchooser
State: installed
Automatically installed: no
Version: 0.9.3-2ubuntu4
Priority: optional
Section: universe/sound
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 139k
Depends: avahi-daemon, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>=
         1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>=
         2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0),
         libgtk2.0-0 (>= 2.16.0), libnotify1 (>= 0.4.4), libnotify1-gtk2.10,
         libpango1.0-0 (>= 1.14.0), libpulse-browse0 (>= 0.9.8),
         libpulse-mainloop-glib0, libpulse0 (>= 0.9.14), libx11-6, libxml2 (>=
         2.6.27), gnome-icon-theme, pavumeter, pavucontrol, paman, paprefs
Description: PulseAudio Device Chooser
 PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
 WIN32 systems. It is a drop in replacement for the ESD sound server with much
 better latency, mixing/re-sampling quality and overall architecture. 
 
 This is a simple GTK tool which registers an icon in the tray area and allows
 quick access to some features of the PulseAudio sound server. Specifically it
 can do for you: 
 
 * Notify about new sink/sources becoming available on the LAN 
 * Quickly change the default PulseAudio sink/source/server assigned to the
   current X11 display, selecting devices available on the LAN 
 * Start the auxiliary tools PulseAudio Volume Control, PulseAudio Volume Meter,
   PulseAudio Manager, PulseAudio Preferences

rick@rick-laptop:~$

---

### Post by dl7und on 2010-05-02
> **garvinrick4 said:**
> I did nothing on purpose "padevchooser is the PulseAudio Device Chooser that allows you
to open all functions and preferences in your Audio. Look it up in Ubuntu Software Center
or Synaptic or even below: Some should Know what they are speaking before they speak.
Giving someone bad code on purpose is a vile action.
Garvinrick4, I may be wrong, but I sincerely think that mike555 was not talking about you at all, but was merely referring to Canonical, who made a few changes to Lucid that are not entirely welcome, the indicator applet being one of them.

I too would like to get rid of that envelope and can not understand why my volume control had disappeared. (Which is why I discovered this thread.) Btw, the gnome-volume-control-applet seems to be the old one, the "native" one from Lucid looks slightly different.

---

### Post by garvinrick4 on 2010-05-02
> **mike555 said:**
> I think they did it on purpose , guess they thought everyone wanted an envelope looking icon that does nothing useful and is  connected to the volume icon .....
Sorry Mike, think I stuck my own foot in mouth.

---

### Post by dl7und on 2010-05-03
An update: When I installed the volume control applet, it showed up the old way, but after reboot it became the new one, so the indicator applet seems to "collect" and replace several applets - which lets me hope again that there is a way to eliminate the envelope...

---

### Post by germanix on 2010-05-03
The Ubuntu manual - Getting started with Ubuntu 10.04 has the following to say about the notification area.

The top panel

On the right side of this panel you will find the notification area, which is similar in function to the &#8220;system tray&#8221; in Windows, or the &#8220;menu extras&#8221; area on the Mac OS X menubar. Next to this is the MeMenu, which will display your username (the name you entered during installation) 

"The notification area
Inside the notification area you will find the network indicator, volume adjustment, Bluetooth indicator (if your computer has Bluetooth capability), messaging, and the date and time applets. Some programs will also place an icon in the notification area when you open them.
Left-clicking icons in the notification area will bring up a list of options, and in some cases right-clicking an icon will also perform an action related to that program. For example, to adjust the volume, simply left-click once on the volume icon and a volume slider will appear. Click the date and time applet to open a small calendar, and then click a specific date to add a reminder.
New notifications of emails and instant messages appear in the messaging menu applet. When you have a new message,**_ the envelope icon will turn green_**.
To remove an applet, right click on it and select Remove From Panel. To add a new applet to a panel, right click in a clear area on the panel and select Add to Panel."

So you can see from the above that the envelope icon actually has a function. It does not do nothing as some have suggested.
As I also use Thunderbird I did not want this envelope icon as I assume it only works with the standard mail program so I just deleted it by left click and choosing remove from panel. The volume applet was there on installation and disappeared there after I got rid of the envelope icon but I just re-installed the volume icon and that solved the problem. So I now have volume but no envelope..

---

### Post by D3mon_Spawn on 2010-05-03
> **mike555 said:**
> I found this when I was in search of a resolution to the same problem. And it seems to work:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

had the same problem and this fixed it. thanx :D

---

### Post by dl7und on 2010-05-04
Germanix, I assume most people who want to get rid of the envelope do so for reasons similar to mine: I do not think that it does not do anything, the problem is that it does not do anything **for me**. I do not need it, I do not want it.

One very nice thing about Linux is the freedom to customize, the freedom to choose. Tell a joe user he has to use vi, tell people they can have any desktop background colour they want, as long as they want brown - and can not change it...

Btw, you said it is easy to remove items from the applet: On my netbook all items are locked, and remove and lock selections are greyed out. So I am stuck with the one applet that takes up all space available for applets, because it is locked and does not let me unlock it...

This is why some people are not very happy about this new "feature"...

---

### Post by cub on 2010-05-12
Thanks for this!

---

### Post by anjilslaire on 2010-05-15
To remove the envelope but keep the volume & other icons try:
```
sudo apt-get purge indicator-messages
```

To get the missing volume back:
```
sudo apt-get install indicator-sound
```

and maybe
```
sudo apt-get install indicator-application
```

---

