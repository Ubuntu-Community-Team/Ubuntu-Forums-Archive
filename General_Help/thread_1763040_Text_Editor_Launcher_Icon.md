---
title: "Text Editor Launcher Icon??"
date: 2011-05-19
forum: General Help
---

### Post by .psd on 2011-05-19
Ubuntu 11.04

Dragging the Text Editor launcher into the Unity dock will create a blank space with a blank label which launches Text Editor. How can I choose an icon for it?

Also, how can I make it so middle clicking on the icon (or other ways of opening multiple instances) will open more instances of Text Editor instead of doing exactly nothing (does nothing if Text Editor is already open, otherwise it opens "Untitled Document 1")?

EDIT: it doesn't "launch text editor" per se. instead it opens "Untitled Document 1". maybe this is why you can't middle click it to open multiple instances?

---

### Post by jerome1232 on 2011-05-19
gedit doesn't allow multiple instances of gedit open since some version in the past that I barely recall.

As for the icon, dragging it to the launcher produces the icon I'd expect, see screenshot. Is yours different? You can change the icon by making you own .desktop file and dragging it into the launcher.

---

### Post by hulkman on 2011-05-19
To get gedit to open new windows each time you click on the icon.

1. Open an instance of gedit.
2. Cut and paste the following into "Untitled Document 1"

[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit --new-window
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;

3. Save the file to the Desktop as "Text Editor 2"
4. Right click the "Text Editor 2.desktop" file and select properties.
5. Under the Permissions tab check the "Allow executing file as program box' and click close.

Your new icon should now allow you to open multiple windows every time you double click on it.

-------------------
Check out the deb packages available at [http://www.dotdeb.com]("http://www.dotdeb.com/")

---

### Post by wildmanne39 on 2011-05-19
> **.psd said:**
> Ubuntu 11.04

Dragging the Text Editor launcher into the Unity dock will create a blank space with a blank label which launches Text Editor. How can I choose an icon for it?

Also, how can I make it so middle clicking on the icon (or other ways of opening multiple instances) will open more instances of Text Editor instead of doing exactly nothing (does nothing if Text Editor is already open, otherwise it opens "Untitled Document 1")?

EDIT: it doesn't "launch text editor" per se. instead it opens "Untitled Document 1". maybe this is why you can't middle click it to open multiple instances?
Hi, that is the text editor, but you have not told it what page you want to edit so you get a blank one,in the menu of the window you can open a file to edit.

---

### Post by .psd on 2011-05-20
That was a neat trick Hulkman, except once I get it to the launcher and delete the file from the desktop, it also deletes it from the dock.

Also, after having deleted the original blank icon then following Hulkman's instructions (then deleting the resulting file from the desktop and launcher from the dock), now dragging Text Editor into the dock does NOTHING. It doesn't even make a blank launcher any more.

What is a working way to add Text Editor to the dock (without having redundant files on my desktop, a la Hulkman's instructions)? Forget about allowing multiple instances for now.

---

### Post by jerome1232 on 2011-05-20
Put the .desktop file somewhere else, that won't bug you. So that you don't feel the need to delete it.

I have some at ~/.local/share/applications

---

### Post by .psd on 2011-05-20
> **jerome1232 said:**
> Put the .desktop file somewhere else, that won't bug you. So that you don't feel the need to delete it.

I have some at ~/.local/share/applications

I was just starting to come to that exact conclusion based on some other stuff I'm reading. Gonna do that.

Still, any reason why simply dragging and dropping Text Editor from the applications list (in the Ubuntu button) should create a blank icon with a blank name at first, and then after deleting that launcher you can't drag Text Editor to the dock *at all*?

---

### Post by jerome1232 on 2011-05-20
I'm not sure, based on someone troubleshooting an issue I had previously I believe unity pulls it's default icons from ~/.local/share/applications and /usr/share/applications


Do you have a gedit.desktop file at either of these locations, both? What are it's contents?

This is the contents of mine at /usr/share/applications, I don't have one at ~/.local/share/applications

This is a stock version, that won't initiate new windows when middle-clicking it. (unity needs more customization options!!!! Like maybe a different command to be executed when a launcher is middle clicked)
```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.4
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit-2/gedit-bugreport
X-Ubuntu-Gettext-Domain=gedit

```

---

### Post by linuxinstalledfromhdd on 2011-05-20
Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

---

### Post by .psd on 2011-05-20
OK Seriously noob question, but I'm not ashamed. I have been able to sudo cp files with about 1/100 success rate. Literally, I think I copied the libflashplayer.so file when I first installed Ubuntu, and it took plenty of trial and error and research.

What do I have to put in the terminal to copy this new gedit file (called 'gedit' not 'gedit.desktop' for some reason) from <ANY location> to <ANY restricted location>?
Specifically, from the desktop to the usr/shared/applications directory.

On a further note, my computer is open, just me and my wife. How can I disable all this stuff that forces me hack my computer for basic operations? In Android, there's a superuser app that remembers your superuser allowances. What does an Ubuntu user have to do in order to gain permanent root/superuser acess? I want the kind of freedom with my files I'm used to on every other computer/OS I've ever used. I understand Ubuntu does this "for my safety", but I'm a big boy now, I don't need Ubuntu to tell me what I can and can't access. I'll be fine, Ubuntu. I promise. Is this even possible?

---

### Post by .psd on 2011-05-20
ngrlvr@ngrlvr-EX58-UD3R:~$ sudo cp ~/Desktop/gedit.desktop usr/share/applications/gedit.desktop
[sudo] password for ngrlvr: 
cp: cannot stat `/home/ngrlvr/Desktop/gedit.desktop': No such file or directory

I can assure you the file is most certainly right here on the desktop. What am I doing wrong?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Unless you have a netbook why are bothering with Unity?  Just use Ubuntu Classic environment.

---

### Post by .psd on 2011-05-20
Hulkman or Jerome or someone, can you provide the code to copy said file from the desktop to, say, /usr/shared/applications/?

---

### Post by .psd on 2011-05-20
Solved :)

Dunno why it was blank to begin with, but Hulkman's instructions allowed me to create a launcher that allows multiple instances of Text Editor (aka gedit). I never did have to check the box allowing it to be executed as a program or whatever, I guess it does that automatically when you copy it to the applications folder.

I was able to cp the file after re-creating it without spaces (before learning how to cp files with spaces). Copied it to /usr/share/applications. Works like a charm.

Thanks hulkman and jerome and everyone!

---

