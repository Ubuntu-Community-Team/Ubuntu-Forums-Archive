---
title: "OPEN WITH listed duplicated applications"
date: 2010-03-24
forum: General Help
---

### Post by sokam on 2010-03-24
Here is my problem.  Over the weekend, I was trying to install some Windows applications in Wine/PlayOnLinux.  The result was not very useful for what I wanted and I removed all the application including wine and Playonlinux completely from my computer (9.10 64bit).

But I was not really able to completely clean up what I did because when I right click on any files and use "OPEN WITH", I got a LONG list of application with many of them are uninstalled and duplicated. 

Here is the screen shot of OPEN WITH:
[http://docs.google.com/View?id=dgjbg74x_69cm6934ds](http://docs.google.com/View?id=dgjbg74x_69cm6934ds)

How do I clean this up?

---

### Post by Greenwidth on 2010-03-24
Have a look for duplicate.desktop files in:
~/.local/share/applications

Also for a particular filetype, click properties (of a file) > Open With Tab

---

### Post by sokam on 2010-03-24
I wasn't sure what I am looking for in 
~/.local/share/applications

I see what you mean by opening the file property and go to the OPEN WITH tab.  However, that mean I have to do each file type by hand!  Not to mention I have to find all the supported file type to open with.  Any quicker solution?

---

### Post by Greenwidth on 2010-03-24
The .desktop files should be the ones you're after, do you have several with the same name (or very similar).
There might also be some in /usr/share/applications.

NB I have double entries for Brasero and F-Spot, I think they are for launching with different parameters.

---

### Post by Greenwidth on 2010-03-24
```
ls ~/.local/share/applications
```
on my fairly recently installed Karmic produces:
```
fusion-icon.desktop  
mimeapps.list  
mplayer.desktop
```
ie not a lot.
wheras ls /usr/share/applications gives:
```
alacarte.desktop
apport-gtk-mime.desktop
at-properties.desktop
backintime-gnome.desktop
backintime-gnome-root.desktop
baobab.desktop
blackjack.desktop
bluetooth-properties.desktop
brasero-copy-medium.desktop
brasero.desktop
brasero-nautilus.desktop
ccsm.desktop
checkbox-gtk.desktop
compiz.desktop
computer-janitor-gtk.desktop
default-applications.desktop
defaults.list
display-properties.desktop
empathy.desktop
eog.desktop
evince.desktop
evolution-2.2.desktop
evolution.desktop
evolution-mail.desktop
file-roller.desktop
firefox.desktop
f-spot.desktop
f-spot-import.desktop
f-spot-view.desktop
fusion-icon.desktop
gcalctool.desktop
gconf-editor.desktop
gdebi.desktop
gdmsetup.desktop
gedit.desktop
gimp.desktop
gksu.desktop
glchess.desktop
glines.desktop
gmenu-simple-editor.desktop
gnect.desktop
gnibbles.desktop
gnobots2.desktop
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
gnometris.desktop
gnome-volume-control.desktop
gnome-wm.desktop
gnomine.desktop
gnotravex.desktop
gnotski.desktop
gpilotd-control-applet.desktop
gstreamer-properties.desktop
gtali.desktop
gucharmap.desktop
hplj1020.desktop
htop.desktop
iagno.desktop
ibus-setup.desktop
jockey-gtk.desktop
keybinding.desktop
keyboard.desktop
language-selector.desktop
mahjongg.desktop
manage-print-jobs.desktop
meld.desktop
metacity.desktop
mimeinfo.cache
mount-archive.desktop
my-default-printer.desktop
nact.desktop
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
openoffice.org-calc.desktop
openoffice.org-draw.desktop
openoffice.org-impress.desktop
openoffice.org-math.desktop
openoffice.org-writer.desktop
orca.desktop
palimpsest.desktop
python2.6.desktop
rhythmbox.desktop
same-gnome.desktop
screensavers
seahorse.desktop
session-properties.desktop
shares.desktop
skype.desktop
software-properties-gtk.desktop
sol.desktop
synaptic.desktop
synaptic-kde.desktop
system-config-printer.desktop
time.desktop
tomboy.desktop
totem.desktop
transmission.desktop
tsclient.desktop
ubuntu-about.desktop
ubuntuone-client-applet.desktop
ubuntu-software-center.desktop
update-manager.desktop
usb-creator-gtk.desktop
users.desktop
vinagre.desktop
vinagre-file.desktop
vino-preferences.desktop
window-properties.desktop
xsane.desktop
yelp.desktop

```

---

### Post by sokam on 2010-03-24
Ok, I do have a long list of .desktop when I

ls ~/.local/share/applications

So I can just delete all the one I have uninstalled?

---

### Post by Greenwidth on 2010-03-24
Prob best to move them somewhere else, so you can put them back if you make a mistake / find you need them.

---

### Post by kazakore on 2010-03-24
Well mine were definitely from installing a second Desktop Environment (XCFE in my case) which I just removed as many as the components I could find from Synaptic and most of them have gone. Be careful as some may be designed for Gnome (which you are probably using) and some for another DE.

---

### Post by sokam on 2010-03-24
I know I uninstalled Wine but there are mountains of .desktop dedicated to wine plus MS Office, AutoCAD and other windows appz .desktop that I am pretty certain they are not native appz.  In fact, I don't see any native appz name in this folder!  How does this .desktop files link to "OPEN WITH" since I don't see one to one correlation between them?

---

### Post by Greenwidth on 2010-03-25
It depends how you installed them. 
Installed as root, they will appear in /usr/share/applications, installed as your username, your username's home.

---

