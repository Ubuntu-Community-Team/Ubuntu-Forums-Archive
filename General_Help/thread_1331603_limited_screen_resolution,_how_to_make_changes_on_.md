---
title: "limited screen resolution, how to make changes on the display"
date: 2009-11-19
forum: General Help
---

### Post by trixxxter on 2009-11-19
2 days ago for the first time i have erased the Windows XP, and installed th opensuse 11.2 KDE , and i thought it was great, (and i still do). However since everyone kept on telling me that Ubuntu was even better i have made clean install of ubuntu 9.1. I have been trying to install it for 4 hours and the screen would only flicker and it would install, later after unsellecting some options it installed as it should. Now i have a problem with the screen resolution it would only give me 640x480 and 800x600 modes, but it's too low and not the whole content of the windows could be viewed. After 5 hours learning of what 'sudo' 'terminal' and xranrd is i have found a method to manually enter 1024x768 resolution at the terminal and it was all great... until reboot, after restarting the Ubuntu the resolution was back at the 2 previos choices 640x480 and 800x600. I read at some forum that the xorg.conf file should be altered, but there is no such file, neither there is xprofile file... 

If there is someone experience user of Ubuntu could you PLEASEEEEEE tell me if there is a way to make the 1024x768 resolution active on the start, is tehere somewhere that i should enter the code, is there a way like cmd file in Win. XP that would invoke the change after boot, or is there a way to make make this automated....

Frankly this linux "make it your self" for drivers programs and basic stuff makes me really nervous.

One more thing that i don't know are there viruses out there for linux systems and antiviruses that should be installed? i have installed the AVG free for linux but i can't find it anywhere?

---

### Post by Cheesemill on 2009-11-19
It sounds like you dont have the drivers for your graphis card installed.
Go to System > Administration > Hardware Drivers and install any drivers that are listed (there is usually no need for any manual configuration whatsoever).
After a reboot you should be able to choose your required resolution from System > Preferences > Display

There is no need for any AV software on a Ubuntu machine unless you're running a file or mail server for windows clients.

---

### Post by trixxxter on 2009-11-19
> **Cheesemill said:**
> It sounds like you dont have the drivers for your graphis card installed.
Go to System > Administration > Hardware Drivers and install any drivers that are listed (there is usually no need for any manual configuration whatsoever).
After a reboot you should be able to choose your required resolution from System > Preferences > Display

There is no need for any AV software on a Ubuntu machine unless you're running a file or mail server for windows clients.

that was the first thing i have tried, to install new vga driver, but there is nothing listed, so i guess every driver is installed correctly. I forgot to mention i'm running on G31M motherboard with integrated Intel graphics 3100, maybe it's not supported under Ubuntu?, the manufacturer doesn't supply linux drivers, only windows platform.

---

### Post by bl4ckl34d3r on 2009-11-25
Bump i almost have this exact same problem please someone fix this

---

