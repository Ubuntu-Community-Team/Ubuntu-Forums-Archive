---
title: "Unable to open display error"
date: 2006-04-17
forum: General Help
---

### Post by PsychStats on 2006-04-17
I have been running Ubuntu Breezy Badger for about 5 months now with no problems. On Thursday of last week, I upgraded the packages that were listed to be upgraded as well as installed a package from Canon to allow me access to the office copy machine and I installed hamachi.

The software from Canon required that i have libGtk1.2-common, libgtk1.2, and libgtk1.2-bin. The packages that were upgraded I cannot remember and not sure where to check on this. Hamachi was fairly straight forward and required the install of a gcc package. 

I first installed hamachi and restarted the computer several times with no problems.

I then installed the software from Canon without a restart and a before I left for the weekend I installed the updates using apt-get. When I came back today I get only the console no gui. 

I logged in and tried to open a web browser and all I get is a error message like this:
(firefox-bin:7530): Gtk-WARNING **: cannot open Display:

I tried reinstalling libgtk2.0.0-2 with libgtk2-common and libgtk2-perl and libgtk2-bin.

I get no dice on this. Any ideas what may be the problem? I am relatively new to Linux. I have played around for the last four years but just now started to really modify and add packages manually. Any information will be helpful.

---

### Post by PsychStats on 2006-04-18
I solved my problem. Found that I had to use the command[COLOR="Red"] startx[/COLOR]. Now I need to figure out why X does not start up. If anyone knows why this is I would greatly appreciate the help on what to alter to get it up and running at startup.

---

### Post by PsychStats on 2006-04-20
I reply to my own messages because, I work in a psychiatry department and figure I should fit in with those that come in for help.:p 

I figured out why I lost display, or rather why the system was going directly to the terminal for login rather than a gui. One of the items I tried to install was the gnome-audio package. For some reason this package uninstalled the ubuntu-audio as well as the gdm, gnome desktop manager. Not sure why until I found some posts on other sites of people trying to get to terminal to login and a the discussion centered around gdm, kdm, or some others. I thought I would look at my installed packages and found that I had no desktop manager installed. Easy enough. I installed gdm and found that it was dependent on ubuntu-audio. I am not sure why you can't use gnome-audio with gdm. 

I got it working and with little fuss, and on my own. I am a little impressed, but then I am disappointed that I took several days to figure out a tiny problem that could have been solved had I paid better attention.

---

