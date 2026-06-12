---
title: "How to add thunderbird to the indicator applet instead of Evolution mail?"
date: 2009-12-12
forum: General Help
---

### Post by mahela007 on 2009-12-12
How do I add thunderbird to the indicator applet on the gnome panel so that it will show new messages when they are received by Tbird?

---

### Post by fancypiper on 2009-12-13
Set what you want for notification in the firefox preferences. It's on the General tab.

---

### Post by mahela007 on 2009-12-13
I'm talking about the applet in the menu bar of the desktop.. the gnome panel.. Is this applet based on firefox?

---

### Post by Wardje on 2009-12-13
This is not (yet) possible, see these:

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/367175](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/367175)
[https://bugs.launchpad.net/libnotify-mozilla/+bug/429395](https://bugs.launchpad.net/libnotify-mozilla/+bug/429395)

---

### Post by davidpuzey on 2009-12-22
I've been doing a little research into the indicator applet and I havn't got a complete solution but what I have found might help you on your quest. First of all you can easily add programmes to the indicator applet list.
The programs on the list seem to be stored in /usr/share/indicators/messages/applications
The contents of the file is the location to the desktop file (to be completely honest I'm not sure of the proper name, but that'll do for now) which seem to be in /usr/share/applications

To show this type
```
cat /usr/share/indicators/messages/applications/empathy
```
into a terminal and you should get the output:
/usr/share/applications/empathy.desktop

The following should add Thunderbird to the menu
```
echo /usr/share/applications/thunderbird.desktop > ~/thunderbird
sudo cp ~/thunderbird /usr/share/indicators/messages/applications/thunderbird
rm ~/thunderbird
```

You may have to wait for a few seconds before you can see the change (possibly even restart for the menu not to add random extra lines in), it's not perfect by its a start.

I haven't, as of yet, found how to fully integrate it (removing any icons from the notification area and just using the indicator applet) however I'm sure that a plugin could be created to do this. As for the notifications (which is probably closer to what you want), I noticed a plugin in pidgin, which I'm guessing is linked to the notifications, called Libnotify Popups so I'm guessing that the notifications are linked to this libnotify thing. I haven't had a proper look yet, but this might be of some help: [http://ubuntuforums.org/showthread.php?t=824809]("http://ubuntuforums.org/showthread.php?t=824809").

It's not a complete solution but I hope that this helps someone somewhere. I'll keep looking into it, and if I find out anything more useful I'll let you know :)

---

### Post by StuartN on 2009-12-22
You can open a menu, find the application that you want, and then click-and-drag that application onto the panel. This makes a copy and does not delete the menu item.

Just delete the Evolution item and set Thunderbird as your email application in System->Preferences->Preferred Applications.

---

### Post by mahela007 on 2009-12-23
thanks davidPuzey.. I'll see what I can do on my end.

---

### Post by mahela007 on 2009-12-23
> **StuartN said:**
> You can open a menu, find the application that you want, and then click-and-drag that application onto the panel. This makes a copy and does not delete the menu item.

Just delete the Evolution item and set Thunderbird as your email application in System->Preferences->Preferred Applications.
does that make the indicator applet show mail in thunderbird?

---

### Post by lockesilver on 2010-02-09
> **mahela007 said:**
> does that make the indicator applet show mail in thunderbird?

No, it doesn't. That will only make a shortcut to Thunderbird insead of Evolution on the panel, which is entirely not the point.;)

Anyway, any new ideas?

---

### Post by mahela007 on 2010-02-10
Nope.. I haven't made any progress.

---

### Post by mr0no on 2010-05-02
Have you tried this: [http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

---

### Post by FkJ on 2010-05-19
> **mr0no said:**
> Have you tried this: [http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

Didn't worked for me. Thunderbird is at the menu, but the icon doesn't changes when I get a new mail.

---

### Post by stoffe on 2010-05-21
This worked for me, including message count and changed icon etc: [http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/](http://www.theopensourcerer.com/2010/02/09/indicator-applet-libnotify-support-for-thunderbird/)

Now I really would like to know how I get rid of the "Setup" entries that never will be used (not gonna use Evolution, nor Empathy).

---

### Post by LarryMi on 2010-05-23
I'm sure there are many ways to do this, but this is the one what worked for me (after rebooting):

[Desktop Entry]
Name=Thunderbird
GenericName=Mail Client
X-GNOME-FullName=Mozilla Thunderbird Mail/News
Comment=Read/Write Mail/News with Mozilla Thunderbird
Exec=thunderbird %u
Icon=thunderbird
Terminal=false
Type=Application
Categories=Application;Network;Email;
StartupNotify=true

X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=Thunderbird
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.04.x
X-GNOME-Bugzilla-OtherBinaries=notify-osd
X-Ubuntu-Gettext-Domain=thunderbird-3.04

X-Ayatana-Desktop-Shortcuts=Compose;Contacts

[Compose Shortcut Group]
Name=New Message
Exec=thunderbird mailto:
OnlyShowIn=Messaging Menu

[Contacts Shortcut Group]
Name=Contacts
Exec=thunderbird -addressbook
OnlyShowIn=Messaging Menu

---

### Post by piggyslasher on 2010-10-26
Outlined in detail here:

[Replace Evolution completely with Thunderbird]("http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/")

Works like a charm if you have 10.04 Lucid. Having trouble with Maverick though.

---

