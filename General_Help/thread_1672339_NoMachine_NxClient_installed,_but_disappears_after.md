---
title: "NoMachine NxClient installed, but disappears after restart"
date: 2011-01-20
forum: General Help
---

### Post by dunsta on 2011-01-20
I have installed NoMachine NxClient deb, on Ubuntu 11.04, Nx installed and I connected to my uni server fine. The Nx program was originally in the applications drop down menu in "others". After a restart Nx was no longer in the menu, I dl'd again and found in Ubuntu software center that there was an option to reinstall NXClient, so I reinstalled and the icons appeared in applications/internet. After a restart they(the NX icons) disappeared again.
No other programs have disappeared from the app menu like that.
How can i make them stay?
Thanks for any help.

edit: after finding edit menu, I noticed nx client (show) was not "ticked" in internet selection. after a reboot the icon is now available in the app/internet menu.
Previous to this I found what I thought was the application in shell $/usr/NX/bin/nxclient
but it would not run from shell command.
I added to the panel, created an application launcher for /usr/NX/bin/nxclient and it works there, too.

TLDR: solved (i hope)

---

### Post by skthetwo on 2011-04-19
I too had the problem. but no amount of reinstallation would bring the menu entries back. After messing about I read the Gnome documentation and found that there was a menus directory in my local .config directory. This had the NX Client marked as deleted in the xml - must have been some stuff I was doing perhaps Since I don't have personal customised menus I just deleted that stuff from my personal menus directory and hey presto it all shows up. The system wide menus are of course in etc/xdg/

Errrr. maybe not. what's reallly worked has been to copy the links to the desktop configuration files NX* ( Client, Help, Wizard and Session Admin ) out of /usr/share/applications directory into $HOME/.local/share/applications/ . That did the job.

---

### Post by skthetwo on 2011-06-27
There's definitely something to be said for writing up what works for one's own future use !

So I got a new machine -  the NoMachine Client, it added it in the menu structure under Applications->Other-NX Client for Linux.  But after a reboot it disappeared. 

Again the solution I used last time:

[I]Errrr. maybe not. what's reallly worked has been to copy the links to  the desktop configuration files NX* ( Client, Help, Wizard and Session  Admin ) out of /usr/share/applications directory into  $HOME/.local/share/applications/ . That did the job. 	
[/I]
did the job.

---

