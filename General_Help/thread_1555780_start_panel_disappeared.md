---
title: "start panel disappeared"
date: 2010-08-18
forum: General Help
---

### Post by markMDW on 2010-08-18
Hi, had installed Xubuntu 9.10 on a Dell laptop that's at least a few years old.  There are several users with different logins on this machine.  On just one login the start panel disappeared along with all the little start applets on that bar such as the Network Manager that allows selection of which wireless router to connect to.  That login can't access the internet.   I can still right click in the desktop area and get menus that allow for most of the functionality of the start panel but I still haven't figured out how to reinstall it or access the internet.  Can someone please advise me on how to set that login back up with a start menu?  Thanks

NEW EDIT:  I was thinking that I might not be very clear in describing what's happening and that I might not be using the right names such as "Start Panel".   To reiterate, The main panel doesn't show up anymore.  ["The Panel is part of the Xfce Desktop Environment and features program launchers, panel menus, a clock, a desktop switcher and more." -- Not there]  ALSO, the Settings Manager program for xubuntu has a section for Panel Settings.  When I click on that it doesn't activate the Panel Settings dialog.  But on the other logins with the Start Panel in place, the Panel Settings work just fine.  I hope someone can make a guess as to what's going on.  Thanks very much for any help or ideas at all!

---

### Post by markMDW on 2010-08-21
I researched and solved the problem with the missing starting Panel in Xubuntu.  If it ever inadvertently gets deleted then just do the following to get it back permanently:

Right click in the empty desktop area> Create Launcher
[the Create Launcher dialog box opens]

type into the empty "Command:" text field the command below:
xfce4-panel

type into the empty "Name:" text field whatever suits your fancy:
Xubuntu Panel

Under "Options" check this box:
[x] Use Startup Notification

Under "Icon" keep the field at default for no icon:
[No icon]

then create the launcher by pressing the create button at the bottom of the dialog box:
[Create]

all done!   you can create an icon if you like but it pops up on the desktop, which is unnecessary since you want this Panel to start every time you login without clicking the icon on the desktop.

I'm relatively new to Linux so pardon me if I posted something too elementary.  I guess some may have thought I had an incurable case of ignorance and didn't bother to posts.  ):PHave a great day!

---

