---
title: "Incomplete Plymouth Themes (no .script) in Repos? &quot;Spinfinity&quot; Broke My Boot Process!"
date: 2010-05-20
forum: General Help
---

### Post by OzzyFrank on 2010-05-20
Now, as far as I know, I did nothing incorrectly, as I installed some of the popular **Plymouth** boot themes available in the repos via Synaptic. So I gather Synaptic did it all for me, and all I had to do then was change themes via:

**[COLOR="RoyalBlue"]sudo update-alternatives --config default.plymouth[/COLOR]**

I then chose **Spinfinity**, since many seemed to like it, and then:

**[COLOR="RoyalBlue"]sudo update-initramfs -u[/COLOR]**

All went well, with the message displayed:

**update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic**

with no error messages. Upon rebooting, the splash displayed fine, with the nifty little animation, but after that, the screen went blank, and while that can happen on and off, after a few minutes of no hard drive activity, I knew something was wrong. No login screen, no keyboard control at all, so I had to use the reset button.

In **recovery mode** I logged in via command line and **[COLOR="RoyalBlue"]startx[/COLOR]** to try to get to my desktop. I thought I had success when the wallpaper appeared, but then it froze there too. Luckily, I had set Ctrl+Alt+Del to open the **System Monitor**, and amazingly it appeared, where **x-session-manager** appeared stopped, so I resumed it and could finally get to the desktop.

Now the bit about possibly incomplete packages being installed comes from exploring the Plymouth themes folder, and noticing a discrepancy between the contents of "official" ones for Ubuntu, Xubuntu and Kubuntu and the new ones like Spinfinity and Solar, being that there is no **[COLOR="Red"].script[/COLOR]** file in the latter.

There is the tiny **.plymouth** file and all the graphics, but seems the ones that work also have a **[COLOR="Red"].script[/COLOR]** file around 35Kb.

Does anyone know what's going on with this situation? Others have used these themes fine, but I can't get to my desktop without all that mucking around. Obviously I changed back to a working splash, but still would like to know why these won't work for me.

Many thanks in advance.

---

### Post by dino99 on 2010-05-20
try with these packages:

[http://packages.ubuntu.com/lucid/plymouth-theme-spinfinity](http://packages.ubuntu.com/lucid/plymouth-theme-spinfinity)

---

### Post by OzzyFrank on 2010-05-20
Well, I tried, even though it was a tiny 36.8kb .deb, and the same version was installed. So I reinstalled it, but still no .script file, which is what I am assuming is causing the boot messup.

---

### Post by OzzyFrank on 2010-10-14
Well, I just tried again on a freshly installed system, and once again it broke my boot and I had to reboot in recovery mode and startx to get to the desktop. I did this even though I checked and found that once again there was no .script file, like the working themes have. I'm amazed anyone has this working, as I sure as heck can't. And as I said, this is on a fresh system.

---

