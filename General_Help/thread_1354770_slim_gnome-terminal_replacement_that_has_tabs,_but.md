---
title: "slim gnome-terminal replacement that has tabs, but no special dependency?"
date: 2009-12-14
forum: General Help
---

### Post by siddartha on 2009-12-14
Is there such a terminal? One that is slim and fast and also has tabs that can be programmed, yet does not have special dependency requirements - gtk, xlib...

---

### Post by benj1 on 2009-12-14
urxvt ?

---

### Post by kellemes on 2009-12-14
```
sudo apt-get install rxvt-unicode
```
"urxvt" to start..

[more info]("http://wiki.archlinux.org/index.php/Rxvt-unicode"), including how to get tabs.

---

### Post by siddartha on 2009-12-14
Thank you, I'll try that.

---

### Post by kellemes on 2009-12-14
By the way, even though I still recommend urxvt..
If you're in search for a full fledged graphical terminal emulator, slimmer compared to gnome-terminal then you may consider xfce's terminal.
```
sudo apt-get install xfce4-terminal
```
does depend on gtk though..

---

### Post by siddartha on 2009-12-14
> **kellemes said:**
> By the way, even though I still recommend urxvt..
If you're in search for a full fledged graphical terminal emulator, slimmer compared to gnome-terminal then you may consider xfce's terminal.
```
sudo apt-get install xfce4-terminal
```does depend on gtk though..

I have netbook remix installed that comes with a few libs already. I don't want to be a puritan and go xlib only. I don't want to install redundant libs either or I would have gone KDE about a week ago. GTK is fine as it is already in use. libthunar for example is not ok unless I find a way to painlessly replace all of nautilus with thunar. As for slim it's not so much about caring for every waste byte... it's about programmers being a disgrace. Back when 4M of RAM was everything you had most apps were almost instant. Today with 2G (and a proportional increase in CPU speed) gedit is far from loading fast. At this basic level of functionality I really couldn't care less about the bells and whistles that come along. It isn't OpenOffice (which makes a world of difference) so it is not justified to have such a long load time. Same goes for eog wich isn't Photoshop, but just a dumb viewer which discovered color calibration a couple of years too late. And the same goes for the terminal. I got used to the tabs so I want them available. And that's about it. Switching to tty1 should be slower than loading gnome-terminal. Well... it isn't.

---

### Post by siddartha on 2009-12-21
Finally. It's materm or mrxvt as it comes in the Ubuntu repository. It's quite ugly by today's standards. And you have to read the man page and create a config file to customize it, pretty much like conky. Otherwise it's wonderful. Makes you wonder how aberant has become the Gnome programming today - just for a graphical config you get something 10x bigger.

---

### Post by falconindy on 2009-12-21
Customization takes place in ~/.Xdefaults. This'll get you started:
```
! screen font
Xft.dpi: 96
Xft.antialias: true
Xft.rgba: rgb
Xft.hinting: true
Xft.hintstyle: hintslight

! x11 mouse theme
Xcursor*theme: DMZ-White
Xcursor.size:  24

! --[ General ]-------------------------------------
URxvt*depth: 32
URxvt*scrollBar:false
URxvt*saveLines:32767
URxvt*cursorColor:#83C048
URxvt*highlightColor:#444444
URxvt.font: -*-terminus-medium-r-*-*-14-*-*-*-*-*-iso10646-1
URxvt.boldFont: -*-terminus-bold-*-*-*-14-*-*-*-*-*-iso10646-1
URxvt.loginshell: true
URxvt.internalborder: 0
URxvt.underlinecolor: #999999

! --[ URL Handling ]--------------------------------
URxvt.keysym.M-u: perl:mark-yank-urls:activate_mark_mode
URxvt.perl-ext: default,matcher,mark-yank-urls

URxvt.urlLauncher: chromium-browser
URxvt.matcher.button: 1
URxvt.matcher.pattern.1: \\bwww\\.[\\w-]\\.[\\w./?&@#-]*[\\w/-]

! --[ colors ]--------------------------------------
URxvt*background: rgba:0000/0000/0000/dddd
URxvt*foreground:#eeeeee

! Gnome Terminal
!! Black
!*color0:#000000
!*color8:#555753
!! Red
!*color1:#cc0000
!*color9:#ef2929
!! Green
!*color2:#4e9a06
!*color10:#8ae234
!! Yellow
!*color3:#c4a000
!*color11:#fce94f
!! Blue
!*color4:#3465a4
!*color12:#729fcf
!! Magenta
!*color5:#75507b
!*color13:#ad7fa8
!! Cyan
!*color6:#06989a
!*color14:#34e2e2
!! White
!*color7:#d3d7cf
!*color15:#eeeeec

!Tango
! Black
*color0:        #000000
*color8:        #555753
! Red
*color1:        #ff6565
*color9:        #ff8d8d
! Green
*color2:        #93d44f
*color10:       #c8e7a8
! Yellow
*color3:        #eab93d
*color11:       #ffc123
! Blue
*color4:        #204a87
*color12:       #3465a4
! Mangenta
*color5:        #ce5c00
*color13:       #f57900
! Cyan
*color6:        #89b6e2
*color14:       #46a4ff
! White
*color7:        #cccccc
*color15:       #ffffff
```
The ! is a comment. You'll want to change the browser under URL handling, and the font (or install Terminus). The Xft and Xcursor lines are likely unneeded/unwanted.

---

### Post by Mark76 on 2009-12-21
How about Roxterm?  Only 778 kB installed and the only dependencies are libc6, libdbus, libdbus-glib, libglade, libglib, libgtk, libpango and lbvte.  Has support for tabs, true transparency with a compositing window manager, adding file and folder paths via drag and drop, a context menu that's exactly the same as the menubar (so you can turn that off if you like) and keyboard shortcuts are a doddle to add.

---

