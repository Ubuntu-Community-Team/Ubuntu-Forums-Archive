---
title: "What am I doing wrong?  Finding file in nautilus"
date: 2011-05-14
forum: General Help
---

### Post by ianc1 on 2011-05-14
Following my installation of 11.04 I thought it would be nice to add some Quicklists to the Launcher’s Lenses - see [http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html).

I went to nautilus to find the file /usr/share/applications/nautilus-home.desktop.  Easy I thought.  However as you can see from the screen shot attached it's not there in nautilus.

I then went to the terminal and tried ```
locate nautilus-home.desktop
```Guess what its in the directory I just looked in.  I can even use nano to view and edit the file.

Why doesn't it show in nautilus?

Any help to solve this would be much appreciated.  I'm sure that somehow I'm doing something stupid.

---

### Post by SavageWolf on 2011-05-14
View -> Show hidden files?

---

### Post by ianc1 on 2011-05-14
Sorry forgot to add that I had already done that.  The directory has 151 items whether showing hidden files or not.

I assume if it was a hidden file it would start with ".".

Cheers

---

### Post by TeoBigusGeekus on 2011-05-14
Finding the file is irrelevant, as the tutorial says that you will replace its contents. So, fire up gedit (geany, vim, kate, emacs, or whatever), add these lines in it
```
[Desktop Entry]

Name=Home Folder
Comment=Open your personal folder
TryExec=nautilus
Exec=nautilus --no-desktop
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;Unity;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=nautilus

X-Ayatana-Desktop-Shortcuts=Videos;Documents;Music;Pictures;Downloads
[Videos Shortcut Group]
Name=Videos
Exec=nautilus Videos
TargetEnvironment=Unity


[Documents Shortcut Group]
Name=Documents
Exec=nautilus Documents
TargetEnvironment=Unity

[Music Shortcut Group]
Name=Music
Exec=nautilus Music
TargetEnvironment=Unity

[Pictures Shortcut Group]
Name=Pictures
Exec=nautilus Pictures
TargetEnvironment=Unity

[Downloads Shortcut Group]
Name=Downloads
Exec=nautilus Downloads
TargetEnvironment=Unity
```
and save it as nautilus-home.desktop in your ~/.local/share/applications/ folder.

---

### Post by ianc1 on 2011-05-14
Thanks BeoBigusGeekus.  I understand that there is no need for me to find the file but I am confused why it does not show in nautilus, it bugs me purely because I don't understand why.  Is this a bug for example.

Additionally, although on unrelated, I am unsure why I need to save the file in the ~/.local/share/applications/ folder.  Why can't I edit it in place, ie in the /usr/share/applications/ folder?

Thanks

---

### Post by AlphaLexman on 2011-05-14
It should be the icon labeled 'Home Folder'

Do you not have that icon, I couldn't see it in your screenshot

EDIT: the first line in the file is:
```
Name=Home Folder
```
Because nautilus also controls the desktop, it does not display the actual filename.

---

### Post by TeoBigusGeekus on 2011-05-14
IMO, Natty as a whole is a bug, but that's another story...

I guess you could create/edit the file in the /usr/share/applications folder; the change then would be global, ie. for all users of the pc, and not just for you.

---

### Post by ianc1 on 2011-05-14
Thanks.  I will edit it in place then.  Still if anyone can explain the absence of the file in nautilus I would be very grateful.

I too am unsure about Unity?  I originally used the Classic Gnome after upgrade but decided to give Unity a fair go and have been using it for a 2 weeks.  I am now finding I "like" it more than anticipated.  I still prefer the standard Gnome desktop and will give a live version of Gnome 3 a try when Fedora 15 is released.

Cheers

---

### Post by TeoBigusGeekus on 2011-05-14
Unity will be awesome... eventually.
For now, it's a beta product that's waiting users to report its bugs.
If you're willing to do it, go for it.
I have an small ubuntu partition with unity installed just to keep up to things ubuntu wise, so I can help people in the forums, but for a product machine... no thanks!

---

