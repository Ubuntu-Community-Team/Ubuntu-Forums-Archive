---
title: "New launchers in Unity"
date: 2011-05-02
forum: General Help
---

### Post by hojjat on 2011-05-02
I just installed Ubuntu 11.04 and this is my first experience with Unity. I have managed to create launchers in .local/share/applications and drag them to the launcher to add desired shortcuts. Here are two questions I have:

1) I am adding many shortcuts to various directories I frequently use; the shortcut's have commands like *nautilus /home/user/some/dir*. Despite the fact that I change their icons, when I drag them to the launcher they all use the Nautilus icon. Is there a way to fix this?

2) Is there a way to group the launchers? For example, having a group for office applications, and a group for directory launchers?


Please advise

---

### Post by mc4man on 2011-05-02
> **hojjat said:**
> I just installed Ubuntu 11.04 and this is my first experience with Unity. I have managed to create launchers in .local/share/applications and drag them to the launcher to add desired shortcuts. Here are two questions I have:

1) I am adding many shortcuts to various directories I frequently use; the shortcut's have commands like *nautilus /home/user/some/dir*. Despite the fact that I change their icons, when I drag them to the launcher they all use the Nautilus icon. Is there a way to fix this?
I don't believe so - you're still using nautilus, better to dump those launchers and add as a group to quicklists in the default 'home-folder' icon.

> **hojjat said:**
> 
2) Is there a way to group the launchers? For example, having a group for office applications, and a group for directory launchers? Please advise


As mentioned you can add any number of new quicklist entries  - see here for an ex.
Note that when using this method dir.'s in the home folder only need the name, for dir.s elsewhere you likely need to path

Also take note of this _existing line_ in the nautilus-home.desktop - the linked Ex. adds the blue, so do that or delete the line
> OnlyShowIn=GNOME;[COLOR="Blue"]Unity; [/COLOR]


[http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity](http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity)

Edit - the link above has you copy the nautilus-home.desktop to you ~/.local/share/blah, blah folder - you can do that or just edit the one in /usr/share, advantages to either way, your choice

If you decide to try, after editing a .desktop do a log out/in, if any issues post the complete edited or created .desktop

As side note - one can also create 'group' icons in the launcher where the quicklist entries are a group of different application - small example here of a 'music player' group

[http://ubuntuforums.org/showthread.php?p=10741859#post10741859](http://ubuntuforums.org/showthread.php?p=10741859#post10741859)

---

### Post by hojjat on 2011-05-02
Thanks for your reply.  I didn't have a home-folder.desktop file, but I had a nautilus.desktop file which I copied to the local directory and modified to this:

```

[Desktop Entry]
Name=File Manager
Exec=nautilus
Icon=system-file-manager
Terminal=false
Type=Application
StartupNotify=true
NoDisplay=true
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.32.2.1
X-GNOME-Autostart-Phase=Desktop
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-GNOME-Provides=filemanager
X-Ubuntu-Gettext-Domain=nautilus

X-Ayatana-Desktop-Shortcuts=Dropbox;Documents;Downloads
[Dropbox Shortcut Group]
Name=Dropbox
Exec=nautilus Dropbox/@@/
TargetEnvironment=Unity

[Documents Shortcut Group]
Name=Documents
Exec=nautilus Documents
TargetEnvironment=Unity

[Downloads Shortcut Group]
Name=Downloads
Exec=nautilus Downloads
TargetEnvironment=Unity

```

However, after logout and login doesn't add the quicklist. Can you figure out where I went wrong?

---

### Post by mc4man on 2011-05-02
One thing wrong is you didn't edit the _existing_ OnlyShowIn=GNOME; line as shown and mentioned previously

Not sure why you don't have the Home Folder .desktop   - (see screen 1) no matter, the nautilus.desktop is ok
(I mistakenly was calling it home-folder.desktop, meant the home folder .desktop - sorry - actual name is nautilus-home.desktop, the display name is Home Folder

Took your posted .desktop and edited mine, (the one highlighted in screen 1),using your posted code, then  edited the OnlyShowIn=GNOME; line as shown in screen 2

Works fine here, both as a launcher for nautilus and the quicklists (screen 3

Make that edit - if still not completely right then remove the  icon from your launcher,  log out/in and then re add

Added an ex. of nautilus-home.desktop with your edits that works fine

---

### Post by hojjat on 2011-05-02
I used the file you attached, and removed and readded the launcher item and it is now working smoothly.

I'm still confused how this nautilus launcher can have a custom icon (the home icon), while other nautilus launchers I created always had the nautilus icon (the one which looks like a shell). But it doesn't matter any more because I'm fine with the quicklist solution.

---

### Post by mc4man on 2011-05-02
> I'm still confused how this nautilus launcher can have a custom icon (the home icon), while other nautilus launchers I created always had the nautilus icon
If you look  in your  custom launcher, (open it in a text editor), it may have 1 or 2 Icon= lines. It's likely that they said Icon=nautilus which will give you the shell.

If you used any of the ones used in the 4 default nautilus desktop files as seen in above screen then you'd get the home folder icon

Ex.'s  - Icon=user-home or Icon=system-file-manager

Any way it's better to just quicklist them as desired, only uses 1 launcher, easier to access. ect.

---

