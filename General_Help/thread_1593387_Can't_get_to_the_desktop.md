---
title: "Can't get to the desktop"
date: 2010-10-11
forum: General Help
---

### Post by NCLI on 2010-10-11
When trying to install Maverick on my Desktop, I ran into quite a few issues. First off, when using the live cd and selecting "Install Ubuntu," the installer didn't appear. I then tried to use the other option "Try Ubuntu without installing," but that simply left me staring at the plymouth screen. If seemed like everything loaded, just in the background. Also, the keyboard locked up, and even the *lock keys didn't work, unless I used "ctrl+sysrq+r".

Finally, I successfully installed it with the alternative cd, but now I'm again stuck with a locked keyboard and a cursor, only this time it's not during plymouth, but just after having logged in using GDM! Only the cursor and the wallpaper are on the screen; no icons, no panels, no nothing.

I was able to use ctrl+alt+F1 to get to a TTY before logging in, and installed all available updates. Didn't help.

Anyone?

---

### Post by AoSteve on 2010-10-11
That doesn't sound like much fun.  Have you tried going from a minimal install?

You could install the minimal and from the command line just sudo apt-get install ubuntu-desktop.   Might try to see if that'll work for you bud!

---

### Post by gnicko on 2010-10-11
What you describe is very strange.

Please, tell us more....

Are you installing from a USB stick? 
Are you sure you have a good copy of the installation media?
Did you format your drive before installing?

---

### Post by sunmake on 2010-10-11
Start Live CD with F6 option 'nomodeset'(press ESC on first screen to get options).Let run Live to the end.Then install.But,if after reboot you find yourself without X runnig,restart and go to rescue mode.Then choose failsafeX mode.You will be able to get X running.Open Preferences-Screen and check all modes.In my case,I've got refresh rate=0 and cannot change this value.But I was able to install driver (fglrx in my case).Now, X start normall and I can set all values at Screen box.Unfortunately,can't open and run ATI configuration.

---

### Post by Hakunka-Matata on 2010-10-11
> **NCLI said:**
> When trying to install Maverick on my Desktop, I ran into quite a few issues. First off, when using the live cd and selecting "Install Ubuntu," the installer didn't appear. I then tried to use the other option "Try Ubuntu without installing," but that simply left me staring at the plymouth screen. If seemed like everything loaded, just in the background. Also, the keyboard locked up, and even the *lock keys didn't work, unless I used "ctrl+sysrq+r".

Finally, I successfully installed it with the alternative cd, but now I'm again stuck with a locked keyboard and a cursor, only this time it's not during plymouth, but just after having logged in using GDM! Only the cursor and the wallpaper are on the screen; no icons, no panels, no nothing.

I was able to use ctrl+alt+F1 to get to a TTY before logging in, and installed all available updates. Didn't help.

Anyone?

Do you mean you want to switch to the Desktop from the tty terminal?  If so ctrl+alt+F7

---

### Post by NCLI on 2010-10-11
First off, thanks a lot to all of you for replying. It's getting very late here, so I'm going to get some sleep before trying any of this, but please come back some time tomorrow to read the results.
> **AoSteve said:**
> That doesn't sound like much fun.  Have you tried going from a minimal install?

You could install the minimal and from the command line just sudo apt-get install ubuntu-desktop.   Might try to see if that'll work for you bud!
Will try this tomorrow :D
> **gnicko said:**
> What you describe is very strange.

Please, tell us more....

Are you installing from a USB stick? 
Are you sure you have a good copy of the installation media?
Did you format your drive before installing?
I've tried installing from USB and cd, Live and Alternate.

I didn't format my drive, but since even the Live CD/USB hangs, I can't see how that could be an issue.
> **sunmake said:**
> Start Live CD with F6 option 'nomodeset'(press ESC on first screen to get options).Let run Live to the end.Then install.But,if after reboot you find yourself without X runnig,restart and go to rescue mode.Then choose failsafeX mode.You will be able to get X running.Open Preferences-Screen and check all modes.In my case,I've got refresh rate=0 and cannot change this value.But I was able to install driver (fglrx in my case).Now, X start normall and I can set all values at Screen box.Unfortunately,can't open and run ATI configuration.
Will try this tomorrow.
> **Hakunka-Matata said:**
> Do you mean you want to switch to the Desktop from the tty terminal?  If so ctrl+alt+F7
Knew that already, the problem is that if I switch, it just hangs.

EDIT: I haven't had time to work on the computer for a few days, please don't think I've forgotten about this thread.

---

### Post by jkxx on 2010-10-11
One more thing to try, install either "kubuntu-desktop" (if currently running ubuntu) or "ubuntu-desktop" if running kubuntu or another distro. This will do two things: install a different desktop environment and ask you which log in manager to use. If you currently have ubuntu, pick kdm there. If not, pick gdm. Hopefully these two steps will give you a usable GUI.

EDIT: and another temporary bandaid/fix. If the above still doesn't help, you may wish to create your own xorg.conf file and set your video driver to vesa, a basic 'generic' driver that works even if all others fail. Use this thread as a guide for the xorg.conf file: [http://ubuntuforums.org/showthread.php?t=1270209]("http://ubuntuforums.org/showthread.php?t=1270209"). Save the file as /etc/X11/xorg.conf and make sure you have root access in order to do so.

Good luck, feel free to contact me if neither of these helps and you are still stuck.

---

### Post by NCLI on 2010-12-20
I ended up getting it to work by booting with nomodeset, then installing the proprietary nVidia drivers. 

Thanks a lot guys!

---

