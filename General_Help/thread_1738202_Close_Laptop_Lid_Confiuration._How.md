---
title: "Close Laptop Lid Confiuration. How?"
date: 2011-04-24
forum: General Help
---

### Post by leegold on 2011-04-24
Hi,

Using Lubuntu 10.10. When I close my Laptop (pull the screen/lid down to close it) it goes into a standby mode where I must press my now blinking on/off button to restart it.

I want to have it so my laptop stays on. The screen by default will probably turn off (that seems hardwired into the hardware) but other than that I want control over this.

Most flavors of Unbuntu easily have control over this by GUI menus but I don't see any way in Lubuntu. Is there a way?

Thanks

---

### Post by Joe of loath on 2011-04-24
Left click the battery icon and select properties. It's just gnome-power-manager :D

---

### Post by leegold on 2011-04-25
Unfortunately Lubuntu does not use Gnome AFAIK.

---

### Post by Joe of loath on 2011-04-25
It uses the gnome-power-manager. I know, because I have it open in front of me :D

---

### Post by cavalier911 on 2011-04-25
menu/preferences/desktop session settings/automatically started applications/
check (enable) Power Manager / OK
Reboot
On Lubuntu Lucid 10.04 there are no working shortcuts to open gnome-power-preferences or gnome-power-statistics
Start gnome-power-preferences from lxterminal or menu/run
General tab, tick Always display an icon
The applet will appear next to the network manager in the system tray area of lxpanel. Clicking the icon will open gnome-power-preferences.
AC Power tab/Actions/When laptop lid is closed
_Menu Shortcuts:_
There is a /usr/share/applications/gnome-power-preferences.desktop
Comment out this line:
**#**OnlyShowIn=GNOME;XFCE:
menu/Preferences/Power Management *appears*
To make gnome-power-statistics.desktop just copy/rename gnome-power-preferences.desktop
Edit EXEC=gnome-power-statistics and Name=Power Statistics
menu/Preferences/Power Statistics

---

