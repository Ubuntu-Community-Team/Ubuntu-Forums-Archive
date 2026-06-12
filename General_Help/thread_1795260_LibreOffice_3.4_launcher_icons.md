---
title: "LibreOffice 3.4 launcher icons"
date: 2011-07-02
forum: General Help
---

### Post by bovender on 2011-07-02
Hi,

I manually installed LibreOffice 3.4. When Writer is running, there is no Writer icon in the launcher, just an icon with a question mark:

[IMG]http://lazy_leukocyte.users.sourceforge.net/libo34_launcher_icon.png[/IMG]

Interestingly, when searching for Writer in the application lens, its icon shows up alright:

[IMG]http://lazy_leukocyte.users.sourceforge.net/libo34_is_installed.png[/IMG]

When I dragged this icon to the launcher & start Writer, the Question mark still appears.

How to make the launcher use the correct icon for Writer while it is running?

Thanks!

---

### Post by mc4man on 2011-07-02
launcher icons are just shortcuts to a .desktop, not an application

When you installed  LibreOffice 3.4 were there .desktop's installed and if so where to?

---

### Post by bovender on 2011-07-02
> user@machine:/opt/libreoffice3.4$ find . -name "*.desktop"
./share/xdg/math.desktop
./share/xdg/calc.desktop
./share/xdg/draw.desktop
./share/xdg/writer.desktop
./share/xdg/base.desktop
./share/xdg/startcenter.desktop
./share/xdg/javafilter.desktop
./share/xdg/printeradmin.desktop
./share/xdg/impress.desktop
./share/xdg/qstart.desktop

Well I guess I have to move/copy these to the right place...

---

### Post by mc4man on 2011-07-02
Start by copying, (or moving)   one to either 
~/.local/share/applications/ or /usr/local/share/applications/
(you may need to create the applications folder

_After that then drag_ the .desktop to the launcher and do a log out/in
It should stay in the launcher and be the 'controlling' icon

Edit: make sure the Exec= line in the .desktop is correct, if you can start from terminal with just the binary name, option,  then the .desktop should be ok, if not then full path the Exec= line
Ex. here, -  this is the Exec=
Exec=libreoffic -writer %U
and libreoffic -writer works from cli


re-edit
You may just be able to drag & drop the .desktop(s) from their current location - worth trying

---

### Post by bovender on 2011-07-07
Hi, it worked the way you described.

Interestingly, the icons that now appear when an LO program is running look quite different from the ones that show up in the list of software in the application lens.

Anyway it's way better than having a question mark in the launcher.

---

### Post by rtimai on 2012-03-03
I recently experimented with switching to the LXDE (desktop) and received several LibreOffice updates during that time, and after switching back to the Unity desktop found my LibreOffice-Calc and LibreOffice-Writer icons displaying as "?" in the Launcher. 

I fixed the icons by running Alacarte (aka Main Menu) which oddly enough, also showed "?" icons ONLY for Calc and Writer. I selected Properties for each, clicked on the icon display, and navigated to 

/usr/share/icons/gnome/48x48/apps

and selected the appropriate .png image file. The launcher icons were restored after rebooting (probably logging out and in would have worked too.)

You can find other icons by performing a File System search for

libreoffice-*.png

libreoffice-*.xpn

I don't know what files are modified by this method, but I just checked and none of the .desktop files were modified by this method.

---

