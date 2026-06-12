---
title: "Help! Ubuntu is doing things that I don't want it to"
date: 2010-08-17
forum: General Help
---

### Post by justinsn95 on 2010-08-17
Hi all. Ubuntu 10.04 has been acting up lately. Perhaps someone here knows how I can fix these issues. 

Issue #1. For some reason, the bar at the bottom of the login screen has turned white. You know how in 10.04, there is a little bar at the bottom of the screen where you enter your password to login? That bar used to be clear/greyish, and now its white. I don't want it to be white. It contrasts and looks ugly. The only thing I ever did was mess with that thing that lets you select what you want to load. A command prompt, or gnome, or whatever. It was not white before that, now it is white and ugly. How do I get it to change back?

Issue #2. Why won't my splash screen ever work? I have it turned on. I have checked, and checked, and then checked again. The splash screen (for boot) is turned on, and a splash screen is installed and "activated" as per the pic. But all I ever get is some bizarre green flecked lines going across the top of my screen at boot, instead of a nice splash screen. 

Issue #3. My cursor is totally different in firefox. I have no idea why. When I am hovering over the desktop, the cursor is white. When I am hovering over FireFox, the cursor changes its little theme, and is red. This is very off putting. I don't know why it shows a red cursor in the pics, cause that's wrong. Its not red, its white. I have checked the cursor settings many times, and it is set to white. But at the bottom of the window, it shows the cursor to be the red one. I have tried to change it, to no avail.

---

### Post by hyperdude111 on 2010-08-17
1. Try     ```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Log out then select the style you want at the login.

Then log in and execute ```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

2. Do you have a nvidia card with nonfree drivers installed ? If so google around fixes for plymouth splash, I have the same issue but couldn't fix it.

3. If you only plan on using the default white cursor theme and remove the red one try :
```
sudo apt-get install dmz-cursor-theme
```
```
sudo apt-get autoremove xcursor-themes
```

If you want to keep the red theme but use the white one try:

Right click on desktop and chose "Change background" Navigate to the theme your are currently using and chose "Customise" then select your cursor.
If you have KDE installed but are not using it then you may also need to go the KDE "System Settings"  = System > Preferences > System Settings. Go to mouse and keyboard > Mouse > Chose cursor theme.

---

### Post by justinsn95 on 2010-08-19
Ok well I got the cursor issue fixed. I have no idea how, though. I think what it was, is that my settings finally took hold and were actually applied. I think that is the problem with my splash screen as well, and might be the source of a lot of other bugs that Ubuntu has. The settings just don't like to stick. I don't know if its just bad programming or what, but if I could only make one complaint about Ubuntu, that would be it. Its like pulling teeth trying to get the settings to stick. In anything. My screenlets even suck. Half the time they do what they are supposed to, half the time they forget to. Ubuntu just really needs a whole lot more polish. 

Do yall think that perhaps I might have better luck with a different distro? Is there one that is known to be a little bit more bug free? Maybe Linux Mint? Or perhaps even Kubuntu might treat me better? It really is hard to learn a new OS when you can't tell if something is a bug, or a "feature". And I'm not complaining here, I am asking an honest question.

---

