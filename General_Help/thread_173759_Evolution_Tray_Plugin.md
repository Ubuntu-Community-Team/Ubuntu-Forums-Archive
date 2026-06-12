---
title: "Evolution Tray Plugin"
date: 2006-05-10
forum: General Help
---

### Post by Gray. on 2006-05-10
Just wondering if anyone knows how to get Evolution to be able to minimize to the system tray (not unlike Rhythmbox). I tried to search the forums but I've never been too good at that (on any forum for that matter). Any help would be greatly appreciated.

---

### Post by byen on 2006-05-10
There are two ways to do this...

1.Install the  Mail Notification program  that sits on the taskbar and notifies and opens evolution when mail arrives. 
Code: sudo apt-get install mail-notification

OR

2. You can Install the program called Alltray that lets you make any program dock in the system tray. ( I just tried it on evolution and it docks alright)
Link for deb: [http://alltray.sourceforge.net/downloads.html](http://alltray.sourceforge.net/downloads.html)
Please scroll down for the Ubuntu package and install.

Here is something that might help too ..
[QUOTE=Shikai]Then just edit the launcher (or create a new one), that loads the following command:
> alltray "evolution"
This will load evolution, with an icon in the notification area. When you close evolution, it will act just like azureus, and minimize to the notification area instead, then you just click the icon to bring it back. To close, you'll need to do a File --> Quit.[/QUOTE]
Hope that helps.Goodluck!
~byen

---

### Post by Gray. on 2006-05-10
Thanks for that! Works a charm. Though if anyone knows where the icon for the default link of Evolution (the small white envelope icon, to the right of the blue globe that launches Firefox) is, I'd be very grateful.

---

### Post by WildPenguin on 2006-05-10
Is this the one you mean?
/usr/share/icons/hicolor/scalable/apps/evolution.svg

---

### Post by Gray. on 2006-05-11
Theres no evolution.svg in that folder, yet all other user accounts on this PC still have the icon, and when I checked what icon their shortcut was using, it comes up as no icon, yet it clearly has one. Weird.

---

### Post by RedMedic on 2007-05-14
It says no icon, because no icon *file* is selected.  It is probably using a theme icon or something.

My icon for evolution is in:
```

/usr/share/icons/Human/scalable/apps/evolution.svg
```

Which is also obviously theme dependent.

I have attached it here for you and others:

---

### Post by Raval on 2008-05-26
[https://answers.launchpad.net/ubuntu/+source/evolution/+question/8692](https://answers.launchpad.net/ubuntu/+source/evolution/+question/8692)

> You need to install the package "mail-notification-evolution" via Add/Remove..., Synaptic or command line (sudo apt-get install mail-notification-evolution).
 You'll now find a small configuration tool at System->Preferences->Mail notification, where you're able to specify how it will inform you and which accounts it should check. You may now safely close evolution and you'll still be informed on incoming mail.


I think we can call this one solved.

---

### Post by ace007 on 2008-07-15
Hate to bring up an old thread, but for anyone who stumbles upon this...

The package "mail-notification-evolution" will not update with evolution emails unless evolution is open.  And if evolution is open then it has its own system tray notification icon.  

If you close evolution the mail-notifcation icon will not function.

EDIT: I'm running Hardy

---

### Post by RuleMaker on 2008-07-17
I have just the same problem as ace007, notification works only if evolution is running.

---

