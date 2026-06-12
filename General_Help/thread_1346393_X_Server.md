---
title: "X Server ?"
date: 2009-12-05
forum: General Help
---

### Post by mikeody on 2009-12-05
Just logged [Karmic] and found VERY big text everywhere !
Am getting the message :

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server". 

I am sure I was using the correct nVidia driver but it seems to have vanished !

Can someone help a nearly newbie please ?

Where do I find the config file - running 'nvidia-xconfig' in a terminal as root doesnt seem to work ! ? 
Presumably I use gedit to edit it - when I have found it ?
What exactly do I edit/ insert ?
And how do I restart the X server ?

Thanks.

---

### Post by Silent Warrior on 2009-12-05
Those might be antiquated instructions - I believe the version of X11 in current releases autodetects about everything, so manual editing shouldn't be necessary. And never having done that with an Nvidia-card, I'd feel most irresponsible pointing you to the system internals right now.
But if you get a graphical desktop, see if you can find a menu-entry for Hardware Drivers (or run this command from a terminal: 'gksu jockey' or 'gksu jockey-gtk'). That's a utility to download proprietary drivers, just so you know. Otherwise, you can try 'apt search nvidia' to find out the names of the Nvidia driver-packages, and sudo apt-get install a likely candidate - or better yet, do it through Synaptic for a better overview.

---

### Post by mikeody on 2009-12-05
Thanks for that.
I have found and download the correct nVidia driver but when I try to install it I get a message that I have 'X Server' running. It tells me to edit the X Server config file and restart X Server.
Any thoughts ?

---

### Post by avik on 2009-12-05
First of all, how did you install the Nvidia drivers before?  I'm assuming you used the Hardware Drivers program in Ubuntu.  If not, you definitely want to install the drivers in Ubuntu's repositories, just like Silent Warrior said, even if they are not the absolute latest.  I don't recommend downloading and installing manually from the Nvidia website because you'll have to stop the GUI completely and work solely with the terminal.

What does running nvidia-xconfig tell you?  The exact output might be helpful.

I'm not sure if logging out and back in would restart the X server, but it's worth a shot.  Otherwise, go to System->Preferences->Keyboard->Layouts->Layout Options.  Under "Key sequence to kill the X server", enable Control+Alt+Backspace.  Now you can use that key sequence to restart the X Server.

---

