---
title: "How does one change icon for unity launcher?"
date: 2011-05-16
forum: General Help
---

### Post by SirSkorpan on 2011-05-16
Hi,

I've just installed Ubuntu 11.04. I also installed Blender (just unpacking the file to a folder in my file system). Now I wanted a shortcut to blender on the new unity launcher. So I created a launcher on the desktop and choose the Icon I wanted and dragged the launcher to the Unity launcher bar. I get the launcher on the bar but the Icon changes to the default Ubuntu Icon. So this is the icon I'd like to change from.

I can't find any information on how to change this icon. Any tips would be appreciated.

---

### Post by Frogs Hair on 2011-05-16
I have changed three application Icons for my launcher . Migrate to the .icon folder in home hidden folders or usr/share in the file system .

Enter the folder of the set you are using and find 128 x 128 Apps folder. 
Locate the icon you would like to use and copy it to home rename the icon with the name as it is in the synaptic package manager . Return it to the Apps folder , logout and login .

Example : I am using Firefox Nightly and I wanted to use the icon from my set because the one provided looked out of place . When I renamed the icon I had to name it firefox-trunk.png as the App is named in synaptic. I also changed the workspace and dictionary icons this way.

---

### Post by wojox on 2011-05-16
Open Blender and right click on the dock icon and select add to panel.

---

### Post by SirSkorpan on 2011-05-17
Hi thanks for the replies. I've tried both suggestions but I haven't been able to do exactly what I wanted.

First  of all I realized I mixed up which program gave me the "default ubuntu  icon", i'm still having some troubles with Blender and it's icon though.  The programs in question is Wings3D and Blender.

Second I should mention that the programs are not installed though the "Software Center" since the versions there are quite old. Instead they are downloaded from the Wings3D and Blender sites. Blender is installed in a program folder in my home folder and Wings (since it was some sort of automatic extractor/installer) installed itself directly in the home folder.

wojox your  suggestion seem to work in a strange way. When  I start Blender and  choose "keep in launcher" in the unity launcher it gives me a launcher  with the original Blender icon (which is good). Although if I close  Blender and start Wings3D it seems like it takes over the launcher  (thats the best way I can describe it). I've tried to illustrate it below.

[IMG]http://aphorise.com/temp/actuallyWings.png[/IMG]

What happens is that the launcher will now start wings instead (really wierd).

As for Frogs Hairs tip I didn't really get it to work. This is what I did:

[IMG]http://aphorise.com/temp/startingpoint.png[/IMG]
[IMG]http://aphorise.com/temp/addingLaunchers.png[/IMG]



An then this is what I would like to do. It would be great to be able to do this with other programs as well and not just these two.

[IMG]http://aphorise.com/temp/differentIconsDescription.png[/IMG]

Thank you so much for your help!
Skorpan

---

### Post by SirSkorpan on 2011-05-17
I should mention that I tried the other location that Frogs Hair talked about (I think) but in this location none of the icons changed (not the Launcher Icon nor the "Running-application-icon"). See picture below (the running icon doesn't show however).

[IMG]http://aphorise.com/temp/otherLocation.png[/IMG]

Anyone has an idea of what might be wrong?

Grateful for all help!
Skorpan

---

### Post by wojox on 2011-05-17
Post the output of this command in code tags:

```
ls /usr/share/applications/
```

---

### Post by SirSkorpan on 2011-05-17
I got the Following output
```

alacarte.desktop
apport-gtk-mime.desktop
apturl.desktop
at-properties.desktop
bamf.index
banshee-audiocd.desktop
banshee.desktop
banshee-media-player.desktop
baobab.desktop
bluetooth-properties.desktop
brasero.desktop
brasero-nautilus.desktop
byobu.desktop
ccsm.desktop
checkbox-gtk.desktop
compiz.desktop
computer-janitor-gtk.desktop
default-applications.desktop
defaults.list
desktop.en_US.UTF8.cache
display-properties.desktop
empathy-accounts.desktop
empathy.desktop
eog.desktop
evince.desktop
evolution-2.2.desktop
evolution.desktop
evolution-mail.desktop
evolution-settings.desktop
file-roller.desktop
filezilla.desktop
firefox.desktop
gbrainy.desktop
gcalctool.desktop
gconf-editor.desktop
gdm-guest-session.desktop
gdmsetup.desktop
gedit.desktop
gksu.desktop
gmenu-simple-editor.desktop
gnome-about.desktop
gnome-about-me.desktop
gnome-appearance-properties.desktop
gnomecc.desktop
gnome-dictionary.desktop
gnome-font-viewer.desktop
gnome-nettool.desktop
gnome-network-properties.desktop
gnome-panel.desktop
gnome-power-preferences.desktop
gnome-screensaver-preferences.desktop
gnome-screenshot.desktop
gnome-search-tool.desktop
gnome-settings-mouse.desktop
gnome-sound-recorder.desktop
gnome-sudoku.desktop
gnome-system-log.desktop
gnome-system-monitor.desktop
gnome-terminal.desktop
gnome-theme-installer.desktop
gnome-user-share-properties.desktop
gnome-volume-control.desktop
gnome-wm.desktop
gnomine.desktop
gparted.desktop
gstreamer-properties.desktop
gucharmap.desktop
gwibber-accounts.desktop
gwibber.desktop
gwibber-preferences.desktop
hplj1020.desktop
ibus-setup.desktop
icedtea-netx-javaws.desktop
im-switch.desktop
indicator-datetime-preferences.desktop
inkscape.desktop
jockey-gtk.desktop
kde4
keybinding.desktop
keyboard.desktop
language-selector.desktop
libreoffice-calc.desktop
libreoffice-draw.desktop
libreoffice-impress.desktop
libreoffice-math.desktop
libreoffice-startcenter.desktop
libreoffice-writer.desktop
mahjongg.desktop
metacity.desktop
mimeinfo.cache
mount-archive.desktop
nautilus-autorun-software.desktop
nautilus-browser.desktop
nautilus-computer.desktop
nautilus.desktop
nautilus-file-management-properties.desktop
nautilus-folder-handler.desktop
nautilus-home.desktop
network-scheme.desktop
nm-connection-editor.desktop
onboard.desktop
onboard-settings.desktop
openjdk-6-java.desktop
openjdk-6-policytool.desktop
orca.desktop
palimpsest.desktop
pitivi.desktop
python2.6.desktop
python2.7.desktop
quadrapassel.desktop
rhythmbox.desktop
rhythmbox-device.desktop
screensavers
seahorse.desktop
session-properties.desktop
shares.desktop
shotwell.desktop
shotwell-viewer.desktop
simple-scan.desktop
software-properties-gtk.desktop
sol.desktop
synaptic.desktop
synaptic-kde.desktop
system-config-printer.desktop
tomboy.desktop
totem.desktop
transmission-gtk.desktop
tsclient.desktop
ubuntu-about.desktop
ubuntuone-control-panel-gtk.desktop
ubuntu-software-center.desktop
unity-preferences.desktop
update-manager.desktop
usb-creator-gtk.desktop
users.desktop
vinagre.desktop
vinagre-file.desktop
vino-preferences.desktop
window-properties.desktop
yelp.desktop

```But I'm not sure what I'm looking at (Although I'm guessing I'm looking for Wings3D and Blender?)

Thanks!
Skorpan

---

### Post by wojox on 2011-05-17
You said you unpacked it to a folder in your filesystem? In your home directory?

What does this say:

```
ls ~/.local/share/applications/
```

---

### Post by SirSkorpan on 2011-05-17
Yes I downloaded a *.tar.bz2 file from blender.org and unpacked it to a ~/Program/Blender/

For Wings3D I downloaded a *.bzip2.run.gz from wings3d.com which unpacked to a *.bzip2.run file which in turn extracted itself to a folder in my home folder (~/wings-1.4.1/) (I tried to move it but the program wouldn't start if I did)

The command you provided gave the following output:

```

ls: cannot access /home/christian/.local/share/applications/: No such file or directory

```

thanks!
/Skorpan

---

### Post by mc4man on 2011-05-17
Your wings will use 1 of 2 .bmp's in wings-1.4.1/lib/wings-1.4.1/ebin, and it's likely it won't run unless at least one is present.
You can replace with icon of your choice using the same name

It's likely a launch icon for wings won't be the 'running' icon, if desired to save space you could add wings to a quicklist for blender (which does use the same icon to launch and run.

---

### Post by mc4man on 2011-05-17
forum duped

---

### Post by SirSkorpan on 2011-05-17
I think that I have found a solution. Not as simple as I'd have liked but it works. It seems like one need to make one's own *.desktop files (apparently a little script file (not sure if you call them that) which holds the information of a launcher in the Unity sidebar. What I did was:

1.) Create/Download the file you want as Icon (not sure if it matters but I used *.png)

2.) save the file in the hidden folder ".icons" in the home folder (ctrl+H to show the hidden stuff) [thanks to Frogs Hair, who pointed me to that location in the first place]

3.) start a new file in gedit and write the following (actually I copied most of it from a the libreoffice-startcenter.desktop file one finds in usr/share/applications/ and figured out the basics of the code):
```

[Desktop Entry]
Version=<VERSION OF APPLICATION> #not sure if this is needed or if it actually the applications version thats supposed to be here
Terminal=false
Icon=<NAME OF ICON FILE WITHOUT EXTENSION>
Type=Application
Categories=<PROGRAMMING, OFFICE for example>; #I think these corresponds to the categories in the ubuntu classics program menu that used to be in the top left 
Exec=<LAUNCHER COMMAND> #the line you would use in the terminal or when creating a Launcher
#MimeType=application/vnd.openofficeorg.extension;
Name=<NAME OF THE APP> 
Name[pt_BR]=<NAME OF THE APP>
GenericName=<NAME OF THE APP>

```Change the text written in caps within <> and you can omit everything behind a #
[Thanks to wojox who pointed med to this location :) ]

NOTE: If some one knows the function of the Name variables (name of what?), the Version variable (version of what), the MimeType variable (what is this and what does it do?) as well as the Categories variabel. Please feel free to post below. This works but there might be a lot of unnecessary things or I might have omitted something that might be useful to add

4.) save the file as a *.desktop file in ~/.local/share/applications/  (again a hidden folder .local in your home folder.

5.) drag and drop the newly created *.desktop file to the Unity bar.

Now to change the icon you will just have to replace the icon file from step 1-2 and you might have to log out and back in (or start the application).

As for the "running-application-icon" for Wings I found two *bmp icons in Wings program folder which I changed to custom icons. That might work on other applications if it does things the same way.

This might not be a solution to the General problem but it worked. But really, there should be a simpler way to change icons in the Unity Bar. Perhaps there is?

Thanks a bunch for the help!
Skorpan

---

### Post by SirSkorpan on 2011-05-17
Thanks mc4man I found the two .bmps thanks for your help though!

/Skorpan

---

### Post by mc4man on 2011-05-17
Generally you'd only need to directly edit the .desktop of the app - the icons in the unity launcher that you can add or remove (favorites) are just shortcuts to the .desktop's

Some apps like wings, once started will use the 'builtin icon' no matter what you set a 'launcher' icon to
An alt. example to blender and wings would be like this
```
gedit ~/.local/share/applications/blender.desktop
```

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/home/doug/blender/blender
Name=Blender
Icon=/home/doug/blender/icons/48x48/apps/blender.png
X-Ayatana-Desktop-Shortcuts=Wings

[Wings Shortcut Group]
Name=Wings 3D
Exec=/home/doug/wings-1.4.1/wings
TargetEnvironment=Unity

```
In this case only blender.desktop is dropped on the launcher, when running blender that icon is active.
Wings is started from a r. click on the blender icon > Wings 3D, it then opens with the wings icon which is only in the launcher while wings is open

Other variations include just creating a graphics.desktop where all your graphics apps are started from the quicklist - here's an example of my current 'Utilities' icon > 1 icon provides a utilities menu
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

---

### Post by SirSkorpan on 2011-05-17
Alright thank you for that info. Thats great to know I think I'll put together something similar to that!

>  		Generally you'd only need to directly edit the .desktop of the app -  the icons in the unity launcher that you can add or remove (favorites)  are just shortcuts to the .desktop's

Yeah one of my problems at first was that I made a launcher on the desktop that I dragged to the Unity bar. but when I deleted the launchers on the desktop the launcher in that bar also disappeared :)

Any how, Thanks again you've been of great help!

---

### Post by NormanFLinux on 2011-05-17
Go to usr/share and open applications folder as root. Change the desired application icon and you're done!

---

### Post by mc4man on 2011-05-17
> **SirSkorpan said:**
> 
Yeah one of my problems at first was that I made a launcher on the desktop that I dragged to the Unity bar. but when I deleted the launchers on the desktop the launcher in that bar also disappeared :)


That just illustrates how the launcher favorite icons are only shortcuts - if you remove or move the .desktop (desktop launchers are just .desktops), after dropping on to the launcher then the shortcut is broken

When modifying .desktops in /usr/share/applications (whether adding quicklists, changing icons ect.) keep in mind that an update will probably overwrite
So if doing any extensive mods then maybe keep a backup somewhere or for single users copying to ~/.local/share/applications will work for most uses/changes
(/usr/local/share/applications will provide for multiple users

---

### Post by SirSkorpan on 2011-05-17
> **NormanFLinux said:**
> Go to usr/share and open applications folder as root. Change the desired application icon and you're done!

Yeah that works well if you've installed the program through, for example, software center but when it's one that you've installed by unpacking it in a folder in your system then, as far as I could find, that way is not an option since the .desktop hasn't been created (and there is no icon in that folder).

Back up is a good tip! Will do!

---

### Post by Dngrsone on 2011-05-24
I ran into a slight problem when creating new launchers for my own use:

I created a launcher, picked an icon of convenience (not having the icon-set I wanted at the time) and then dragged that launcher onto the launcher bar.

Afterward, I changed the icon on the launcher in my desktop, but the icon on the launcher bar would not revert.

When I went to edit the Launcher script, I discovered that there are two different icons per launcher:

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/dngrs/.icons/Daily.gif
Name[en_US]=Daily
Exec=firefox -no-remote -P Daily
Name=Daily
Icon=/home/dngrs/.icons/Daily.gif
```

The first one shows the location of the icon that is shown in the Unity Launcher bar, and the second is the icon picked for the launcher as it sits on the desktop.

Unity will recognise .png and .gif, but not gimp .xcf files.

---

### Post by mihalybaci on 2011-06-24
> **Frogs Hair said:**
>  Example : I am using Firefox Nightly and I wanted to use the icon from my set because the one provided looked out of place . When I renamed the icon I had to name it firefox-trunk.png as the App is named in synaptic. I also changed the workspace and dictionary icons this way.

I also use Firefox Nightly and I'm sick of looking at a question mark, but I haven't been able to change it. I would like it to be the standard 'mozicon' of the world at night, but I haven't found the right folder to put it in I guess. I've renamed the image from mozicon128.png to firefox-trunk.png, as you suggested and copied it to the following folders:

> 
[michael@jeeves /]$ sudo find . -name firefox-trunk.png
./home/michael/.icons/firefox-trunk.png
./home/michael/firefox/icons/firefox-trunk.png
./usr/share/icons/hicolor/48x48/apps/firefox-trunk.png
./usr/share/icons/hicolor/128x128/apps/firefox-trunk.png
./usr/share/icons/firefox-trunk.png
./usr/share/icons/oxygen/128x128/firefox-trunk.png
./usr/share/icons/HighContrastLargePrintInverse/48x48/apps/firefox-trunk.png


I unpacked Nightly in my home directory and run it from there using an alias if that makes a difference. Thanks.

---

### Post by eumetaxas on 2011-08-01
Thank you SirSkorpan!

---

