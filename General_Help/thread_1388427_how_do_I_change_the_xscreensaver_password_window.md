---
title: "how do I change the xscreensaver password window?"
date: 2010-01-23
forum: General Help
---

### Post by 11010110 on 2010-01-23
Hello everyone, 

I recently installed xscreensaver in order to change some settings on some of the screensavers I have. All is well until I lock the screen. I do not like the look of the password entry window. the one that came with the GTK2 theme I use looked great and I was wondering if there was a way to tell xscreensaver to use that one instead of the one that it uses by default. Also, whenever I restart my computer I have to open up xscreensaver and tell it to kill the gnome-screensaver daemon and then start the xscreensaver one. Is there a way to automate this process?

Thanks to all in advance.

---

### Post by rCXer on 2010-01-23
To stop the gnome-screensaver daemon from running at startup enter this in the terminal...
```

gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

```

To make xscreensaver run automatically at startup, System -> Preferences -> Startup Applications. Press Add. Type "xscreensaver" for name and "xscreensaver -no-splash" for the command.

I don't know how to change the xscreensaver theme.

---

### Post by Toz on 2010-08-18
To change the skin of the xscreensaver dialog, do the following:

1. Create or add to ~/.Xresources. Here is a sample skin (compliments of [http://wiki.archlinux.org/index.php/Xdefaults#xscreensaver_theming):](http://wiki.archlinux.org/index.php/Xdefaults#xscreensaver_theming):)
> ! xscreensaver ---------------------------------------------------------------

!font settings
xscreensaver.Dialog.headingFont:        -*-dina-bold-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-dina-medium-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-dina-medium-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-dina-medium-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-dina-bold-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-dina-medium-r-*-*-12-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-dina-bold-r-*-*-12-*-*-*-*-*-*-*
!general dialog box (affects main hostname, username, password text)
xscreensaver.Dialog.foreground:         #ffffff
xscreensaver.Dialog.background:         #111111
xscreensaver.Dialog.topShadowColor:     #111111
xscreensaver.Dialog.bottomShadowColor:  #111111
xscreensaver.Dialog.Button.foreground:  #666666
xscreensaver.Dialog.Button.background:  #ffffff
!username/password input box and date text colour
xscreensaver.Dialog.text.foreground:    #666666
xscreensaver.Dialog.text.background:    #ffffff
xscreensaver.Dialog.internalBorderWidth:24
xscreensaver.Dialog.borderWidth:        20
xscreensaver.Dialog.shadowThickness:    2
!timeout bar (background is actually determined by Dialog.text.background)
xscreensaver.passwd.thermometer.foreground:  #ff0000
xscreensaver.passwd.thermometer.background:  #000000
xscreensaver.passwd.thermometer.width:       8
!datestamp format--see the strftime(3) manual page for details
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y


2. Import the contents of the .Xresources file into the xrdb:
> xrdb .Xresources

3. Restart xscreensaver:
> xscreensaver-command -restart

4. Edit .Xresources to suite your needs. Remember to do #2 and #3 after each change.

/ToZ

---

