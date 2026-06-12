---
title: "(Hopefully) simple questions on mounting and unmounting devices"
date: 2006-03-25
forum: General Help
---

### Post by wgscott on 2006-03-25
I started using Ubuntu about 6 or 8 months ago, and recently upgraded to KDE after the 5.10 update (i.e., I did not install from the Kubuntu distribution).

When running gnome, unmounting a CD seems straightforward.  I haven't yet figured out how to do it in KDE.  :oops:   I had to issue the command 

```
umount /media/cdrom
```

to get it to give up the CD when I press the eject button.

To make matters worse, when I plug in a keychain drive, I get a message about not being able to mount due to the lack of an appropriate entry in /etc/fstab.

Indeed, my /etc/fstab has an entry for the cdrom and for a floppy, as well as all of the nfs and smb mounts I have, but lacks any entry for these sorts of things that get plugged into USB and firewire ports.

I've checked the documentation but can't find anything on how to fix these annoyances.

](*,)


I should add that I turned off desktop display of icons (so that I could run KDE remotely from my PC on one of the virtual desktops of my Mac OS X machine in X11 rootless mode -- sorry, I guess that is kind of geeky) so I am worried that doing so might somehow mess these things up.

---

### Post by Barrakketh on 2006-03-25
Inserting a CD, DVD, or external drive causes a drive icon to appear on the desktop and within the Storage Media panel in the Kicker.  By default it's next to the trash can.  Right clicking on the desktop icon or single clicking on the Storage Media icon will let you either eject the disc or safely remove the USB drive.

You can also find it in the Storage Media section in Konqueror (if you're using the web browser view in Konqueror, it's media:/)

---

### Post by wgscott on 2006-03-25
[QUOTE=Barrakketh]Inserting a CD, DVD, or external drive causes a drive icon to appear on the desktop [/QUOTE]


Ah, so I did in fact create my own problem by turning off the display of desktop icons.  :shock:

I'll have to figure out a way to do this only when displayed remotely.

But should /etc/fstab have entries for the scuzzy devices (which appears to be what it calls USB and firewire devices)?

---

### Post by Barrakketh on 2006-03-25
[QUOTE=wgscott]But should /etc/fstab have entries for the scuzzy devices (which appears to be what it calls USB and firewire devices)?[/QUOTE]
No.  Devices that are automatically mounted don't get their own fstab entry (you're never guaranteed whether your USB drive is going to be /dev/sda1 or /dev/sda2...it depends on what order they were connected).  Instead they would only be listed in /etc/mtab, which is what's printed when you type "mount" with no arguments.  

Don't forget that you can view the the devices in Konqueror, and if you don't have the Storage Media applet on your Kicker (it's there on a clean Kubuntu install) then you could add it.  I'm not sure whether you're using KDE 3.5.1 or not (Breezy users can add a repository to update to it), but if you are you're able to right click on the Kicker and choose "Add Applet to Panel..." and choose Storage Media.

---

### Post by wgscott on 2006-03-25
Thanks.  I'll give that a try.

Meanwhile, to turn off the desktop icons, I followed the following piece of advice:

> NOTE: By default, X11 on Mac OS X runs in "rootless" mode, generally. If you run KDE in rootless mode, it will take over your desktop with a window that covers everything up.  You can remove this by disabling
desktop icons in the KDE control center.  Open the control center
(either from the "K" menu bar, or by typing "kcontrol" in an xterm)
then expand the "Desktop" list, click "Behavior", and uncheck the
"Show icons on desktop" checkbox.

I did this, and now I am trying to see what file gets modified when this happens.  Is there a unix command-line equivalent to toggle this behavior on and off?

Ideally, I'd like to have something of the form

```


if [[ -n $SSH_CONNECTION ]];then
  command turning off desktop icons
else
  command turning on desktop icons
fi

```

in my .zshrc file.


I'm using the default current stable Breezy 5.10 KDE (3.4.3-0ubuntu1 ).

---

### Post by Barrakketh on 2006-03-25
No command that I know of.  The file that sets whether to display icons or not is ~/.kde/share/config/kdesktoprc

In particular, this part:
```
[General]
Enabled=false

```
hides them, setting it to true shows them.  If you're better at sed than I am you can probably write a script to change that for you.

---

### Post by wgscott on 2006-03-25
Thanks.  That should be easy to do.

While in that file, I also found this:

```

[Media]
exclude=media/hdd_mounted,media/floppy5_unmounted,media/cdrom_unmounted,media/floppy_unmounted,media/hdd_unmounted


```

The plot thickens.

---

### Post by wgscott on 2006-03-25
For anyone else reading this, here is what I'm putting into my startup script (should work with zsh or bash or ksh):

```

# For KDE, turn off desktop icons if displayed remotely
if [[ -z $SSH_CONNECTION ]];then
         perl -pi -e 's|Enabled=false|Enabled=true|g' ~/.kde/share/config/kdesktoprc
else
         perl -pi -e 's|Enabled=true|Enabled=false|g' ~/.kde/share/config/kdesktoprc
fi

```

---

### Post by Barrakketh on 2006-03-25
[QUOTE=wgscott]Thanks.  That should be easy to do.

While in that file, I also found this:

```

[Media]
exclude=media/hdd_mounted,media/floppy5_unmounted,media/cdrom_unmounted,media/floppy_unmounted,media/hdd_unmounted


```

The plot thickens.[/QUOTE]
Look in the third tab in Behavior where it says "Device Icons"

EDIT: FYI, your script will also disable the screensaver.

---

### Post by wgscott on 2006-03-27
[QUOTE=Barrakketh]
EDIT: FYI, your script will also disable the screensaver.[/QUOTE]


Only on the remote display, where I don't want it.


In any case, it seems to work great.

I had to put the lines in .zshenv rather than .zshrc.

---

