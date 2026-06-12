---
title: "Can't upgrade illegal package name `"
date: 2011-07-11
forum: General Help
---

### Post by s2monkey on 2011-07-11
I've been trying to install the latest updates on my Ubuntu 10.10 system but keep getting the same error in Update Manager and the terminal:
```
dpkg: file triggers record mentions illegal package name `
```
I've tried running **sudo dpkg --configure -a** and **sudo apt-get upgrade -f** after running **sudo apt-get update** but to no avail.  

After searching the forum and google I haven't been able to find this issue or a solution to a similar issue that works for my problem.  I'm still new to Ubuntu and would appreciate any help.

Thanks.

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums :-)

Open a terminal with Ctrl+Alt+T and run the following diagnostic command:

```
sudo apt-get check
```Post any error messages please.

---

### Post by s2monkey on 2011-07-13
Rubi1200,

I ran the command you requested but didn't get any error messages.  This is the output I got:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done

```

---

### Post by gmargo on 2011-07-13
Is that the whole error message?  There should be more info after that quote at the end.

This error occurs while parsing the file **/var/lib/dpkg/triggers/File**, so perhaps your file is corrupted.  Can you post the content of that file?

---

### Post by Habitual on 2011-07-13
You could try this script, I have used it in the past with much success for issues just like this one.

```

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi
clear
echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF
clear
echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Emptying the trash..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR

```

save it as say ~/cleanup.sh
Open a ternminal and issue
```
chmod 700 ~/cleanup.sh
```

then 
```
sudo ./cleanup.sh
```

If you are unsure, just answer No or Ctrl+C during it's run.

HTH.

---

### Post by s2monkey on 2011-07-13
This is how the message is displayed on the terminal:
```

dpkg: file triggers record mentions illegal package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Here is a copy of my **/var/lib/dpkg/triggers/File**:
```

/etc/init ureadahead
/etc/init.d ureadahead
/usr/share/info install-info
/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders libgdk-pixbuf2.0-0
/usr/share/fonts fontconfig
/usr/share/ghostscript/fonts fontconfig
/usr/share/texmf/fonts fontconfig
/usr/share/mime/packages shared-mime-info
/usr/lib/gtk-2.0/2.10.0/immodules libgtk2.0-0
/usr/share/applications python-gmenu
/usr/share/icons/hicolor hicolor-icon-theme
/usr/share/icons/gnome gnome-icon-theme
/usr/share/applications desktop-file-utils
/usr/man man-db
/usr/share/man man-db
/usr/local/man man-db
/usr/local/share/man man-db
/usr/X11R6/man man-db
/opt/man man-db
/etc/ufw/applications.d ufw
/usr/share/doc-base doc-base
/usr/share/gconf/defaults gconf2
/usr/share/gconf/mandatory gconf2
/usr/share/gconf/schemas gconf2
/usr/share/menu menu
/usr/lib/menu menu
/etc/menu-methods menu
/usr/lib/xine/plugins xine-ui
/usr/share/hal/fdi hal
/usr/lib/gio/modules libglib2.0-0
/usr/share/glib-2.0/schemas libglib2.0-0
/usr/share/app-install/desktop soætware-center
/usr/share/locale-langpack software-center

```

---

### Post by gmargo on 2011-07-13
The second-to-last line has an illegal character:
```

/usr/share/app-install/desktop soætware-center

```This should be:
```

/usr/share/app-install/desktop software-center

```

---

### Post by s2monkey on 2011-07-13
@Habitual

I ran your script as written and got the following output:
```
dpkg-query: file triggers record mentions illegal package name `
dpkg-query: file triggers record mentions illegal package name `
Cleaning apt cache...
./cleanup.sh: line 19: aptitude: command not found
Removing old config files...
sudo: aptitude: command not found
Removing old kernels...
sudo: aptitude: command not found
Emptying the trash...
Script Finished!
```

Since it appears I don't have aptitude installed I changed your script to use apt-get instead and got the following output:
```
dpkg-query: file triggers record mentions illegal package name `
dpkg-query: file triggers record mentions illegal package name `
Cleaning apt cache...
Removing old config files...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: file triggers record mentions illegal package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
Removing old kernels...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: file triggers record mentions illegal package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
Emptying the trash...
Script Finished!
```

It still appears I am haunted by the *file triggers record mentions illegal package name `* :confused:

---

### Post by s2monkey on 2011-07-13
SHARP EYES GMARGO!!!

Once I corrected that odd character I was able to upgrade successfully!  I wish I knew what I did to cause it to happen in the first place.

Thank you so much for the help everyone!

---

### Post by Habitual on 2011-07-13
glad it worked out.

---

### Post by Rubi1200 on 2011-07-13
I am also glad you got this fixed :-)

Enjoy!

---

