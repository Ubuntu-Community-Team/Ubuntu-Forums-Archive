---
title: "How do I add a custom launcher to the menu in Ubuntu 12.04?"
date: 2012-05-06
forum: General Help
---

### Post by k999 on 2012-05-06
Hi,

I've built The GIMP 2.8 from source. It's in a custom location, and I want to add it to the launcher so that I can run it as any other application without launching it via a terminal.

How do I do this under Unity on Ubuntu 12.04?

---

### Post by jeffreyldavidson on 2012-05-06
The easiest way is to install Main Menu in software cetner and then you can add the program by creating a new item. It can then be placed on the sidebar if you like.

---

### Post by xyzzyman on 2012-05-06
Create an entry with Alacarte, it's pre-installed. Just press the super key and type alacarte.

---

### Post by k999 on 2012-05-06
Thanks for the tips. I don't have alacarte on my Ubuntu 12.04 system, but I guess I could install it. I haven't tried Main Menu either, but I found another recipe online that suggested I create a text file called program.desktop on my Desktop, and edit it as I needed.

It sort of worked, but not completely. I need to set a custom environment variable (LD_LIBRARY_PATH). On the command line, I run gimp 2.8 like this:

```
LD_LIBRARY_PATH=$HOME/build/lib $HOME/build/bin/gimp-2.8
```

However, just pasting this command on the Exec= line doesn't work, presumably because this string is just exec()-ed later. Is there any way to work around this from the launcher, or do I need a wrapper script for this?

---

### Post by mc4man on 2012-05-06
You can either use the gimp.desktop in gimp install (likeky opt/..) or create a new one. 

New one,  - as far as Icon= line, will work if gimp 2.6 is innstalled or the comm. below will make it work.
Otherwise copy the gimp.png to like Pictures or Documents & full path the Icon= line
```

gedit ~/.local/share/applications/gimp2.desktop
```

adjust blue if different

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Gimp 2.8
Comment=Create images and edit photographs
Exec=[COLOR="Blue"]/opt/gimp-2.8/bin/gimp-2.8[/COLOR] %U
TryExec=[COLOR="Blue"]/opt/gimp-2.8/bin/gimp-2.8[/COLOR]
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.8.0
X-GNOME-Bugzilla-OtherBinaries=gimp-2.8
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;
```

Run this to allow Icon=gimp to work if gimp-2.6 isn't installed. Adjust blue if different
The idea is to get a gimp.png into that pixmaps folder
```
sudo cp [COLOR="Blue"]/opt/gimp-2.8/share/icons/hicolor/48x48/apps/gimp.png[/COLOR] /usr/share/pixmaps/

```

Then just browse to ~/.local/share/applications & drag gimp2.desktop on to the launcher

---

### Post by jerome1232 on 2012-05-06
alacarte and "main menu" are the same program, and they do all of this work for you. :D

offtopic: Things just keep getting bumped out of the default install that really should be there, I mean taking out the menu editor... really?

---

### Post by k999 on 2012-05-06
jerome1232, I installed alacarte/Main Menu, but can't see that I can add any custom environment variables. Am I missing something?

---

### Post by jerome1232 on 2012-05-06
I'm sorry, I missed that post, is there a reason you don't want to put that into your ~/.pam_environment (for a per user thing) or /etc/environment as a system wide setting.

Requires re-login to take affect.

edit: Also I guess alacarte can't do that, if you wanted it loaded only when you start gimp, see here [https://help.ubuntu.com/community/EnvironmentVariables#Launching_desktop_application_with_an_environment_variable](https://help.ubuntu.com/community/EnvironmentVariables#Launching_desktop_application_with_an_environment_variable)

---

### Post by mc4man on 2012-05-06
Whether it matters here or not would depend on use case but -   alacarte  won't include a MimeTypes= line which is needed for DnD of files on to the launcher icon

Also I'd check to see if it ends the Exec= line with a %<letter>, either U or f. If not the app won't show on the r. click context menu

Sometimes better to do yourself

---

### Post by k999 on 2012-05-07
Of course, env ought to do the trick! I'll give that a shot, thanks!!

---

### Post by Colombiano123 on 2013-03-04
- Click on Home Folder icon from the launcher,
- Choose File System on the left side menu, 
- Go to this path: [FONT=Ubuntu Mono]/usr/share/applications[/FONT] , there you will find all your applications.

To add application to launcher:
- Run the application,
- Now the application is in the launcher, right click on the icon in the launcher and choose Lock to Launcher.

To create a new custom launcher application, based on an existing one:
- On [FONT=Ubuntu Mono]/usr/share/applications[/FONT] , right click on the application,
- Choose Copy to -> Desktop,
- On Desktop, right click on new icon created,
- Go to Properties, now you can customize this application.

---

### Post by k999 on 2013-03-04
Hey Colombiano123,

Running a random application and clicking "Lock to launcher" doesn't work. I've checked out code for a program from git and run it from the git directory. It shows up on the launcher, and I can lock it to the launcher, but clicking on it again later doesn't work. When running from the command line, I've tried both absolute path and ./program, neither works. If you get this to work, I'm curious how. This program doesn't take any command line arguments, it's just launched directly. I've tried with several programs, none of them worked.

---

### Post by forestG on 2013-04-05
Actually if you have installed synapse then if you run the command though synapse (just typing the name of the application) you can the pin the application to the launcher. It worked fine with Eclipse. Also the approach with  Alacarte mentioned before also works

---

### Post by gabor111 on 2013-04-07
I have a similar problem with CrashPlanDesktop:

I can start it fine from command line like this:
```
user@mypc:~$ /usr/local/bin/CrashPlanDesktop
```
and the program starts normaly, and a nice icons appears in the Unity Launcher.

After I right-click on it and and choose Lock to Launcher, the icon remains on it after closing the application, but I can't start it with this icon. In fact this icon disappears after a few clicks on it.

It tryed alacarte/Main Menu and synapse too, but didn't find how to make a new icon in the launcher.

Thx a lot if somebody can help me.

---

### Post by deadflowr on 2013-04-07
> **gabor111 said:**
> I have a similar problem with CrashPlanDesktop:

I can start it fine from command line like this:
```
user@mypc:~$ /usr/local/bin/CrashPlanDesktop
```
and the program starts normaly, and a nice icons appears in the Unity Launcher.

After I right-click on it and and choose Lock to Launcher, the icon remains on it after closing the application, but I can't start it with this icon. In fact this icon disappears after a few clicks on it.

It tryed alacarte/Main Menu and synapse too, but didn't find how to make a new icon in the launcher.

Thx a lot if somebody can help me.

The simplest way to get a program to be added to the launcher is to create a desktop file.
First open gedit, or other text editor.
The add something like this

```
[Desktop Entry]
Name = Whatever name you want to use
Exec = The command that launchs the program
Icon = whatever icon pleases you
Type = Application
```

In general, you need to have a name, exec, and type to set this up. Icons are optional.
There are several kinds of type, application, link and some other ones I haven't the need to remember.

With this part done, save the file with the extension .desktop at the end.
From here you can either place it in /home/user/.local/share/applications
Or /usr/share/applications.
As little manipulation is needed to do either.
For the /usr/share/application placement, you'll need to be root.
In Unity, programs placed in the .local/share/applications folder need to be marked as executable.

When all is set, open the dash and type the name of the program, and either launch it, or drag to the launcher.
Lock it as you want.

There of course are more options you can add to the desktop entry. If you want to see them, simply open up a .desktop
file in a text editor. I usually open gedit and the run open and go to a place like /usr/share/applications and then find a program I'd like to look at and press Okay.
Some of the optional entries are for stuff like categories, and others like Unity specific quicklists.

---

### Post by deadflowr on 2013-04-10
Quick recap, as it's been a while since I've created any launchers, and it seems either I had a bug or something changed as I no longer need to mark the file as executable in the .local folder.
Before, if I created a desktop file and placed it in the .local folder, if I didn't set the file to executable, then it didn't show up in the dash, or menu system.
If I opened the dash and typed the program name, I would get the actual desktop file and not the program.

So it seems marking to execute isn't needed.
At least for me now it isn't.

---

### Post by gabor111 on 2013-04-11
Thank you for your detailed and usefull description.
It's working fine.

---

### Post by efflandt on 2013-04-11
Note that in Exec= or the command in a desktop launcher (alacarte or Main Menu) does not do shell intepretation or may not properly interpret parameters, so if you need shell interpretation or a multipart command, begin the command with **sh -c** and enclose the command in single or double quotes (depending whether it includes any other quotes or other quotes that need to be escaped). For example this is a command in a desktop launcher to launch minecraft to be able to use parameters and ~/ (interpreted home dir) in a path:

sh -c 'java -Xmx2G -Xms1G -cp ~/MC-client/minecraft.jar net.minecraft.LauncherFrame'

So maybe something like:

sh -c 'export LD_LIBRARY_PATH=~/build/lib && ~/build/bin/gimp-2.8'
(not sure if the "export" is required)

Once you get a desktop or Dash launcher working, you should be able to pin it to Unity bar.

---

