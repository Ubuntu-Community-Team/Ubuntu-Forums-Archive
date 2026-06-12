---
title: "unity. unity. unity. Show me some examples!"
date: 2012-05-09
forum: General Help
---

### Post by Simon Cropper on 2012-05-09
I am so sick of hearing how good unity is and how many users have been asked to test the interface.

From what I can gleen the interface is designed for the average user trying to access social media, music and on the off chance a few basic tools (word processor, email).

How can this interface be used in a production environment? For example I pertake of the open source world and download and regularly use many many packages to acheive various tasks. For example I have many image manipulation programs or pdf utilities.

If I open dash and type 'pdf' all I get is the most commonly used pdf package (usually a viewer) and a list of recent pdf documents. I want to categorise and tag all my applications so when I type 'pdf' in dash all packages that have anything to do with viewing, editing or maniplutaing pdfs in any way will appear.

In a production environment -- I collect various tools to do various things and I don't always remember what the package is called. In the old system I would place the application in a menu or submenu so I could find them when that task was needed to be done again. How is this done in unity/dash? Can someone post some examples or point me to where this type of customization is explained. 

I work on images, photography, pdf, gis packages and programming and have package collections in each group. I am currently using xfce and menues and have played with the gnome-classic mode in ubuntu 11.10. But I constantly here how unity/dash is so great and I keep going back to try the interface but find I spend an inordinate amount of time finding applications.

I am not trying illicit comments about whether people like or dislike the interface. I presume that the ununtu developers and community developers and power users in general have exactly the same problem as I am explaining -- all I want to know is do they use unity/dash and how do they solve this problem.

Help? Advice?

---

### Post by mc4man on 2012-05-09
Myself use the launcher & quicklists more so then the Dash for applications. So here create category based icons where the left click may be the more often used app of that category or one that is also useful for DnD on.
The quicklists would then open related apps, scripts, commands or locations. The advantage here is it's quicker, 1 or 2 click max,  apps can be opened with an altered launch command or env if desired &the quicklist name can be anything desired. (descriptive, whatever 

So as a real simple example for a basic utility launcher. In this case using the apps straight up, 2 scripts & 1 command. I use synaptic most often so it's the left click on & doesn't open a separate icon when running

These examples are using new 12.04 Desktop Actions format
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=synaptic-pkexec
Name=Utilities
Icon=/usr/share/icons/Humanity/categories/48/applications-other.svg
Actions=CCSM;Dconf;Htop;GetUp;NaTool;Gconf;UM;FQuit;SS;Seach;

[Desktop Action Htop]
Name=Htop
Exec=htop1
TargetEnvironment=Unity

[Desktop Action GetUp]
Name=Update Sources
Exec=update1
TargetEnvironment=Unity

[Desktop Action NaTool]
Name=Nautilus Actions
Exec=nautilus-actions-config-tool
TargetEnvironment=Unity

[Desktop Action CCSM]
Name=Compiz Settings
Exec=ccsm
TargetEnvironment=Unity

[Desktop Action Gconf]
Name=Gconf Editor
Exec=gconf-editor
TargetEnvironment=Unity

[Desktop Action FQuit]
Name=Force Quit
Exec=xkill
TargetEnvironment=Unity

[Desktop Action SS]
Name=Screen Shots
Exec=gnome-screenshot --interactive
TargetEnvironment=Unity

[Desktop Action Seach]
Name=Search For Files
Exec=gnome-search-tool
TargetEnvironment=Unity

[Desktop Action Dconf]
Name=Dconf Editor
Exec=dconf-editor
TargetEnvironment=Unity

[Desktop Action UM]
Name=Update Manager
Exec=/usr/bin/update-manager
TargetEnvironment=Unity

```

If I wish to add something then it's simply add a new Desktop Action section & then add the name to the Actions= line, the postion in the quicklist being determined by position in the Actions= line. 
To Temp remove an entry then it's done simply by removing from the Action= line

Another example would be one here for multimedia, in this case I use vlc the most so it's the left click on icon & DnD of files based on the MimeTypes= line
Here I'm altering the env & returning the menus to the app's window in many cases

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 /usr/local/bin/vlc %U
Name=MultiMedia
Icon=/usr/share/icons/Humanity/categories/48/applications-multimedia.svg
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;audio/amr;audio/amr-wb;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;application/xspf+xml;
Actions=Audacious;Totem;GnomeMplayer;MediaInfo;RubyRipperGui;TotemXine;Audacity;Umplayer;Mini;

[Desktop Action Audacious]
Name=Audacious
Exec=env UBUNTU_MENUPROXY=0 audacious
TargetEnvironment=Unity

[Desktop Action TotemXine]
Name=Totem Xine Media Player
Exec=env UBUNTU_MENUPROXY=0 /usr/local/bin/totem-xine
TargetEnvironment=Unity

[Desktop Action RubyRipperGui]
Name=RubyRipper Gui
Exec=rrip_gui
TargetEnvironment=Unity

[Desktop Action MediaInfo]
Name=MediaInfo
Exec=env UBUNTU_MENUPROXY=0 mediainfo-gui %f 
TargetEnvironment=Unity

[Desktop Action GnomeMplayer]
Name=Gnome Mplayer
Exec=/usr/bin/gnome-mplayer
TargetEnvironment=Unity

[Desktop Action Totem]
Name=Totem
Exec=totem
TargetEnvironment=Unity

[Desktop Action Mini]
Name=MiniTube
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 /usr/bin/minitube
TargetEnvironment=Unity

[Desktop Action Audacity]
Name=Audacity
Exec=env UBUNTU_MENUPROXY=0 audacity
TargetEnvironment=Unity

[Desktop Action Umplayer]
Name=Umplayer
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 umplayer
TargetEnvironment=Unity
```


So basically thru 4 or 5 category icons all the apps, some scripts & custom commands I use are easily & quickly opened

---

### Post by malspa on 2012-05-09
> **mc4man said:**
> Myself use the launcher & quicklists more so then the Dash for applications.

Me, too. I'm using something similar to what mc4man showed. For example, here's the file for my Utilities "quicklist" (~/.local/share/applications/utility.desktop):


```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=
Name=Utilities
Icon=/usr/share/icons/Humanity/categories/48/applications-other.svg
X-Ayatana-Desktop-Shortcuts=TextEditor;Nautilus;GCalcTool;KCharSelect;KSnapShot;UbuntuTweak;MyUnity;CCSM;SystemSettings;Synaptic;

[TextEditor Shortcut Group]
Name=geany
Exec=geany
TargetEnvironment=Unity

[Nautilus Shortcut Group]
Name=nautilus
Exec=nautilus
TargetEnvironment=Unity

[GCalcTool Shortcut Group]
Name=gcalctool
Exec=gcalctool
TargetEnvironment=Unity

[KCharSelect Shortcut Group]
Name=kcharselect
Exec=kcharselect
TargetEnvironment=Unity

[KSnapShot Shortcut Group]
Name=ksnapshot
Exec=ksnapshot
TargetEnvironment=Unity

[UbuntuTweak Shortcut Group]
Name=ubuntu-tweak
Exec=ubuntu-tweak
TargetEnvironment=Unity

[MyUnity Shortcut Group]
Name=myunity
Exec=myunity
TargetEnvironment=Unity

[CCSM Shortcut Group]
Name=compizconfig-settings-manager
Exec=ccsm
TargetEnvironment=Unity

[SystemSettings Shortcut Group]
Name=system-settings
Exec=gnome-control-center --overview
TargetEnvironment=Unity

[Synaptic Shortcut Group]
Name=synaptic
Exec=synaptic-pkexec
TargetEnvironment=Unity
```

---

### Post by Simon Cropper on 2012-05-09
Hi mc4man,

This sounds interesting and not to disimilar to changes I being making to the xfce destop menu.

That said what do you actually mean by 'quicklists'? How are these initiated and what do they look like? 

Are you able to show some images of these in action? 

Where would the configuration files you show below reside? Is there any resources on the web outlining their format and how they should be setup?

When you say 'launcher' what are you meaning? The 'docky-type' panel on the left? This is ok for the top 5-10 applications but that is all. When I am using unity this is the primary tool I use to open my common applications.

Simon

---

### Post by Simon Cropper on 2012-05-10
Hmmm

Just logged back into unity. It would seem that you are saying you can insert an icon into the launcher that opens a commonly used application and that if you right click on the icon a picklist appears -- this is what you are adjusting. So if I get it it is like a 1-teired menu.

As a simple example, if I wanted to create an icon that opened gedit and have a picklist that opened a particular file in the picklist, how would this be acheived?

Or alternatively, I have multiple bash scripts to open and close mounts/computers. How would I create a picklist of these and what would I connect them to?

Simon

---

### Post by malspa on 2012-05-10
Here's a screenshot of my Utilities quicklist.

After creating the file ~/.local/share/applications/utility.desktop, I simply dragged the file from the file browser (in my case, it was Dolphin) to the Launcher, and then I was able to use the Utilities quicklist. If I make changes to the utility.desktop file, I have to start a new session for the changes to take effect.

One question I have, in GNOME 2 I was able to edit the contents of the desktop's right-click menu (adding entries for various applications) using nautilus-actions. In GNOME 3, I haven't been able to do the same thing; the GUI for nautilus-actions has more options so maybe I'm missing something; has anyone been able to do this so that it'll work in Unity or GNOME Shell in Ubuntu 12.04?

---

### Post by Simon Cropper on 2012-05-10
Hi All,

I get what is happening. The 'Actions' a just standard options to the desktop files used in most menu systems (gnome, xfce, unity). 

As directed I could easily drag and drop a desktop icon onto the launcher.

So basically you are able to create probably 5 groups with actions defined in the picklist that can open any type of command.

I wonder if it would be just as easy and possibly more portable to create a library of scripts to open various applications sorted into a directory tree. Symlinks to directory or launchers could then be used present groups in what ever launching application a particular interface uses. This will stop the need to have to relearn the syntax for every desktop environment. I know that the desktop files are meant to do just that but mixing kde, gnome, xfce, unity systems makes it very hard to have a consistent approach -- everybody seems to being doing there own thing.

Simon

---

