---
title: "Grub Screen not Displaying"
date: 2011-03-17
forum: General Help
---

### Post by Quarkrad on 2011-03-17
I have 10.10 running on a 64bit Intel dual core 2.5GHz system with 2 Meg RAM.  I recently bought a new display, Acer G195hdv, and all was fine. I dual boot with winXP using Burg as my boot manager.  The first issue was my graphics card blew and I used the internal graphics but had to boot in Failsafe graphics mode.  With help on this forum I got this working by altering the grub/burg menu.  I installed a new graphics card yesterday (Asus engt220 - basically Nvivia) and on rebooting everything is fine in terms of my Desktop graphics and drivers.  Problem is, when I switch on I have no grub/burg - actually this isn't quite true.  What happens is, after the bios/cosmos is loaded I see a brief display, top left of screen, of text saying Grub Loading, then the screen goes blank (black) with an acer display small blue box saying Input Not Supported for about 2 seconds.  Then the screen goes blank (black) with a flashing curser top left of screen as Ubuntu boots in the background.  Suddenly the screen goes (Ubuntu) mauve in colour with words Ubuntu 10.10 for about 2 secs before the Desktop loads. 
Also, I have a script that runs rsync on shutdown.  When I was in Failsave graphics mode when I shut down I have a mauve screen with the 4 white dots in the middle of the screen whilst Ubuntu was shutting down.  This could be running for some time depending what new backups rsync was running in the background.  Now what happens is when I shut down and rsync is running in the background I still get the (shutdown) mauve screen but I can see all the files that are being backed up displayed in white text on the screen.  Any help to get my grub/burg screen displayed much appreciated - I think it is 'there', just not being displayed.

---

### Post by seawolf167 on 2011-03-17
If you'd like to see it on boot you can hold the [SHIFT] key when the computer starts up to display the menu, else if you want to see it everytime you boot, you'll need to edit the grub config file:

```
gksudo gedit /etc/default/grub
```change the line

```
GRUB_HIDDEN_TIMEOUT=0
```to

```
GRUB_HIDDEN_TIMEOUT=10
```save, exit, then run

```
sudo update-grub
```

---

### Post by Quarkrad on 2011-03-17
My GRUB_HIDDEN_TIMEOUT is #'d out - this is the first few lines of my etc/default/grub file: 

[COLOR="Blue"]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""[/COLOR]

The first few lines of my etc/default/burg file is:

[COLOR="Blue"]# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"
GRUB_CMDLINE_LINUX=""[/COLOR]

---

### Post by Quarkrad on 2011-03-19
bump

---

### Post by Quarkrad on 2011-03-20
The soltion was to reset the screen resolution in Burg to 800 x 600 - the screen was back!

---

