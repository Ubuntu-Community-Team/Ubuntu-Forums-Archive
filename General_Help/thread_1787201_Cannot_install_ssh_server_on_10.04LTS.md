---
title: "Cannot install ssh server on 10.04LTS"
date: 2011-06-20
forum: General Help
---

### Post by ExTruckie on 2011-06-20
Hi All

I am having trouble installing the ssh server onto my file server running 10.04LTS. I had it on this box when I was running 9.04-.10. I keep getting connection refused errors. Attached is a screenshot of my terminal during install. I think that the install is failing but am uncertain how to correct it.

---

### Post by ExTruckie on 2011-06-23
Need to bump this

I also have some additional info. If I try to install the ssh server metapackage from the software center it also fails. see the attached screenshot. 
Now it seems strange that I cannot install a ssh server so, something else must be wrong.
If a reinstall is necessary so be it, but had enough trouble with getting this install to go properly.

Thanks in advance

---

### Post by gmargo on 2011-06-23
Pay attention to the error message:
> 
dpkg: syntax error in file triggers file `/var/lib/dpkg/triggers//File'
Post the contents of the **/var/lib/dpkg/triggers/File** file please.  There is a problem with it.

---

### Post by ExTruckie on 2011-06-23
> **gmargo said:**
> Pay attention to the error message:
Post the contents of the **/var/lib/dpkg/triggers/File** file please.  There is a problem with it.


t, &#1083;&#1077;&#1074;&#1072;&#1103; &#1082;&#1083;&#1072;&#1074;&#1080;&#1096;&#1072; Control, &#1083;&#1077;&#1074;&#1072;&#1103; &#1082;&#1083;&#1072;&#1074;&#1080;&#1096;&#1072; Shift, &#1083;&#1077;&#1074;&#1072;&#1103; &#1082;&#1083;&#1072;&#1074;&#1080;&#1096;&#1072; &#1089; &#1083;&#1086;&#1075;&#1086;&#1090;&#1080;&#1087;&#1086;&#1084;, Scroll Lock, &#1073;&#1077;&#1079; &#1087;&#1077;&#1088;&#1077;&#1082;&#1083;&#1102;&#1095;&#1072;&#1090;&#1077;&#1083;&#1103;
Choices-sv.utf-8: Caps Lock, Alt\, höger, Control\, höger, Shift\, höger, Tangent med logotype\, höger, Menyknapp, Alt+Shift, Control+Shift, Control+Alt, Alt+Caps Lock, Vänster Control+Vänster Shift, Alt\, vänster, Control\, vänster, Shift\, vänster, Tangent med logotype\, vänster, Scroll Lock, Ingen utbytbarhet
Choices-th.utf-8: Caps Lock, Alt &#3586;&#3623;&#3634;, Control &#3586;&#3623;&#3634;, Shift &#3586;&#3623;&#3634;, &#3611;&#3640;&#3656;&#3617;&#3650;&#3621;&#3650;&#3585;&#3657;&#3586;&#3623;&#3634;, &#3611;&#3640;&#3656;&#3617;&#3648;&#3617;&#3609;&#3641;, Alt+Shift, Control+Shift, Control+Alt, Alt+Caps Lock, Control &#3595;&#3657;&#3634;&#3618;+Shift &#3595;&#3657;&#3634;&#3618;, Alt &#3595;&#3657;&#3634;&#3618;, Control &#3595;&#3657;&#3634;&#3618;, Shif


As requested sir.

---

### Post by gmargo on 2011-06-23
Something is really messed up.
Here is my **/var/lib/dpkg/triggers/File** on 10.10 Maverick:
```

/etc/init ureadahead
/etc/init.d ureadahead
/usr/share/info install-info
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/etc/ufw/applications.d ufw
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/share/doc-base doc-base
/usr/share/app-install/desktop software-center
/usr/share/locale-langpack software-center
/usr/share/menu menu
/usr/lib/menu menu
/etc/menu-methods menu
/usr/share/hal/fdi hal
/usr/lib/packagekit-backend packagekit
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/usr/lib/libreoffice/share/extensions libreoffice-common
/etc/php5/conf.d libapache2-mod-php5
/usr/share/locale/locale.alias lintian
/usr/lib/locales-all lintian
/usr/lib/vlc/plugins vlc-nox

```

---

### Post by ExTruckie on 2011-06-23
> **gmargo said:**
> Something is really messed up.
Here is my **/var/lib/dpkg/triggers/File** on 10.10 Maverick:
```

/etc/init ureadahead
/etc/init.d ureadahead
/usr/share/info install-info
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/etc/ufw/applications.d ufw
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/share/doc-base doc-base
/usr/share/app-install/desktop software-center
/usr/share/locale-langpack software-center
/usr/share/menu menu
/usr/lib/menu menu
/etc/menu-methods menu
/usr/share/hal/fdi hal
/usr/lib/packagekit-backend packagekit
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/usr/lib/libreoffice/share/extensions libreoffice-common
/etc/php5/conf.d libapache2-mod-php5
/usr/share/locale/locale.alias lintian
/usr/lib/locales-all lintian
/usr/lib/vlc/plugins vlc-nox

```

I see that!!! wow it is bad. next question. How do I fix it? maybe just copy and paste yours?
This all started after a failed upgrade to 11.04

---

### Post by gmargo on 2011-06-23
While I believe it possible to regenerate that particular file, the question must remain: what other files were messed up at the same time?  

Can you really trust it now?  

Time to backup and reinstall?

---

### Post by ExTruckie on 2011-06-23
I see your point. 
I had alot of trouble with this existing install. Had to burn the disk 3 times before I got one that would load. I know I should reburn another copy before I try again. I do have a good copy of 9.04 and could go the upgrade route but I really don't have the time for that. Is there another place to dl 11.04?
Thanks
:(

---

### Post by ExTruckie on 2011-06-23
just finished dling 11.04 and am burning it onto a disk. I'll see tomorrow if iit works or not.

---

### Post by ExTruckie on 2011-06-25
Ok I got a good copy of 11.04 (burn to a DVD not CD) 
I need to backup my system but have to do it from the cmd line. I found the following in the archives and was warned by the archive that the info maybe unusable due to os upgrades. 
Are the following cmds still valid?


                                  **Best Way to Backup and Restore**             
                                                                To backup:

**tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot  --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz  --exclude=/mnt --exclude=/sys /**

To Restore:

**tar xvpfz backup.tgz -C /**

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

Just posting a helpful tip, for all of you out there trying to find a decent backup solution.

Ein Prosit
 

Thanks.

Well I ran it anyway, The worst it could do is trash my system that I have to reinstall. looks like the cmd is still ok.

---

