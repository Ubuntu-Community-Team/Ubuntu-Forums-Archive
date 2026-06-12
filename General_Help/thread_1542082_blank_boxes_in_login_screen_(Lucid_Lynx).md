---
title: "blank boxes in login screen (Lucid Lynx)"
date: 2010-07-30
forum: General Help
---

### Post by edwinw on 2010-07-30
A bit of a problem report, together with a rant.

I installed Lucid Lynx on a medium-old system, Athlon 2200+ with an ATI video card.  No problems during the install itself.  The problem is that when I boot into the login screen, I get a bunch of blank boxes.  If I move the mouse around, I can see various areas highlighted, but I can't actually see the menu options.  I can type in my username and password to log in (not being able to see what I'm typing), but then the desktop panels are empty boxes - once again I can mouse over them to get empty drop down menus, but I can't see anything else.

I've had enough experience with Ubuntu in the past to do some troubleshooting myself.  Usually I would just boot into a terminal, switch Xorg to use the vesa driver and go from there.  However, a number of decisions in Lucid Lynx have made troubleshooting practically impossible.

1 - No grub menu.  No way for me to pick a safe boot option.
2 - Install CD doesn't come with any rescue boot options.
3 - Ctrl-Alt-Backspace to kill the X server and Ctrl-Alt-F1 to boot into a shell don't work.
4 - the default filesystem is ext4, which means my old rescue CDs aren't likely to be of much help.

Sigh.  I understand that Ubuntu is trying to make things look pretty and all, but these user-friendly changes are making it near impossible to fix a problem like the one I have.  I just downloaded a System Rescue Linux CD but it's kind of late to be trying it out now.

So, if somebody could either guide me on how to solve my problem it would be much appreciated!

---

### Post by dino99 on 2010-07-30
to see the grub menu: at end of bios process, hold "shift" key down, then edit the boot line (ctrl+E) and remove quiet splash and add nomodeset, then boot (ctrl+X)

then :

sudo rm -f /etc/X11/xorg.conf (kernel directly deal with X now)
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by edwinw on 2010-07-31
dino99, thanks for the tips, unfortunately it didn't work.  That is, I still had blank boxes after putting nomodeset in the kernel boot line.  I actually tried a bunch of other things from a bit of googling, like xforcevesea, acpi=off, radeon.modeset=0 and they all didn't work.

However, I have a temporary workaround.  I reinstalled 8.04 (which is proving to be a workhorse in terms of supporting the most hardware), and then upgraded to Lucid.  I ended up with the same blank boxes.  The difference is after the upgrade from Jaunty, I still had my old grub boot menu, which included a failsafe desktop login option.  This allows me to get into a desktop at least.

Based on my googling, I may just be out of luck with respect to my hardware, a MSI K7N2GM2 motherboard, Athlon 2200+ processor and ATI Radeon 9600 AGP video card (the video card being the problem).  The video drivers included with Lucid don't work for me.

By the way, now that I'm in a desktop, I did try dino99's dpkg-reconfigure commands but the system says there's no package called jockey (there's jockey-gtk and jockey-common according to Synaptic).

I also tried installing the fglrx driver from Synaptic but it didn't work with my hardware.  I even tried downloading the driver directly from ATI, but upon running the shell script I got the following error:

```

Error: ./default_policy.sh does not support version
default:vs:i686::none:.2.6.32-24-generic; make sure that the version is being correctly set by --iscurrentdistro

```

Am I correct in reading this to mean that the proprietary ATI driver (the 9.3 one for some older cards) is not compatible with the Lucid kernel?  If that's the case, is this something that ATI can or will fix?  Or is it possible that the driver should work with the latest kernel, but the installer is just being a bit too picky?  Any help would be appreciated!

---

### Post by pcolamar on 2010-08-01
I have got a similar problem
Since yesterday, after the boot sequence I get the login screen with all user's names but the right half of the screen is black

The keyboard seems not be responsive (actually it is very, very slow, like  1 char/min !).

Users witout passwd can login and get the standard Gnome desktop and everything works but users that have to type a passwd cannot pass the login screen (as I said , the keyboard is in practice unresponsive)

Just to test , I reset the passwd of one of the login that had it and after that this user could login just clicking the login-name on the login screen.

I do not get what the origin of the problem could be.

I have tried without success:
1) to change the grub config replacing "quiete splash" with "nomodeset"
2) to login with kernel 2.32..  , 2.33.., 2.34.., always the same problem
3) to follow dino99 suggestion with no success

The  driver I use (ATI card Radeon x300) is the 1.5 MESA 7.7.1

Everything works fine if I boot in ubuntu 9.04  (Note it is a multi boot machine and that the /home is the the same for all)

Any suggestion ?
Cheers
Palmer

---

