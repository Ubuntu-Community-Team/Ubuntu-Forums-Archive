---
title: "Bash Profile Trouble and General Confusion"
date: 2010-10-22
forum: General Help
---

### Post by u83rn3Rd on 2010-10-22
(Note to Moderators: I had no idea where to post this so please feel free to move it if it should be elsewhere. Thanks)

I am fairly new to Linux and am trying to learn the terminal and shell scripting from [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php). Near the beginning of the shell scripting tutorial I am instructed to add an alias to ~/.bash_profile . After not finding the said file I did some googling and read that in Ubuntu the profile that is run upon login is ~/.profile if .bash_profile and .bash_login does not exist. Upon failure and further research, I found this does not run on startup in X session(Which I think means a GUI login verses just CLI?) and that the place to make modifications that will be run on login is ~/.xsession. Unfortunately, this also does not exist:confused:. Also, If I understand correctly(which is usually not the case:)) ~./bashrc is run everytime the terminal is opened. So, if anyone could help me out here and explain which ~/.* file I need to add this alias (and other things in the future) so that it will be run upon login while I am using the GUI and how this works I would be very grateful. Thank you!

PS I apologize if I was confusing in any way and also for extreme noobishness.

PPS Is there an easy way to login by default without a gui and then enter a command to use it if I wanted?

PPPS If it helps at all I am running the 64-bit version of 10.10

Also here is what ls -a (while in ~/) prints:

.
..
.adanaxis
.adobe
.audacity-data
.bash_history
.bash_logout
.bashrc
.B.blend
bin
.blender
blenderific
.Blog
.cache
.civclientrc
.civserver_history
.compiz
.config
crapsingingattemp1.wav
crapsingingattempt2.wav
crapsingingattempt3.wav
.dbus
Desktop
.dfarc3
.dink
DMOD
.dmrc
Documents
Downloads
.elluminate
.esd_auth
.evolution
examples.desktop
Firefox_wallpaper.png
firstdude.blend
firstdude.blend1
firstdude.blend2
firstdude.blend3
.fontconfig
.freeciv
.gconf
.gconfd
.gksu.lock
.gnash
.gnome2
.gnome2_private
.gnupg
.gstreamer-0.10
.gtk-bookmarks
.gvfs
.hardinfo
hs_err_pid1709.log
hs_err_pid3125.log
.ICEauthority
.icedteaplugin
.icons
.jagex_cache_32
jagex__preferences3.dat
jagex_runescape_preferences2.dat
jagex_runescape_preferences.dat
.kde
lmms
.lmmsrc.xml
.local
.macromedia
.miro
.mnemosyne
.mozilla
Music
.nautilus
.netx
.netxrc
.nvidia-settings-rc
.openoffice.org
Pictures
.profile
Public
.pulse
.pulse-cookie
.qt
.recently-used.xbel
songinessbass.wav
songiness.wav
.ssh
.sudo_as_admin_successful
.sudoku
.swp
Templates
test.txt
.themes
.thumbnails
.update-notifier
Videos
.xsession-errors
.xsession-errors.old

---

### Post by mikewhatever on 2010-10-22
~/.bashrc is the file. Take a look at it, it already has some aliases, though most are commented out.

---

### Post by matt_symes on 2010-10-22
Hi

MikeWhatever is correct. Use ~/.bashrc. However some people put their aliases in a separate file and call that from .bashrc. This can help keep all the aliases in one file distinct from anything else.

BTW Put long listings in code blocks.

Kind regards

---

### Post by u83rn3Rd on 2010-10-22
It worked. Thanks a ton!

If anyone could point me in the right direction to learning more about how bash profiles work in ubuntu and in general that would be really helpful too.

---

### Post by sisco311 on 2010-10-22
First check out the man page ;)
```
man bash | less +/^FILES
```
The differences are explained here: [http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html)

> **u83rn3Rd said:**
> 
PPS Is there an easy way to login by default without a gui and then enter a command to use it if I wanted?


Yes, boot with the text kernel parameter. Edit /etc/default/grub:
```
sudo nano /etc/default/grub
```
and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new grub2 config file:
```
sudo update-grub
```

To start the GUI run:
```
startx
```
or if you have issues with startx, start GDM:
```
sudo initctl start gdm
```

---

### Post by u83rn3Rd on 2010-10-22
Thanks very much everyone! I really appreciate the help. :) Sisco311 the man page and the article where enlightening and the method for booting up without the GUI worked just fine. Thanks again mikewhatever, matt_symes and sisco311 ! I suppose I should now mark this as [SOLVED].__

---

