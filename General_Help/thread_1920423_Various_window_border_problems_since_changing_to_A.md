---
title: "Various window border problems since changing to AMD graphics card! (11.10)"
date: 2012-02-04
forum: General Help
---

### Post by JonUK76 on 2012-02-04
Hi all, I've run into a problem which I am hoping someone will have some tips on fixing.  Or tell me I'm out of luck until something is changed.  I'm using Ubuntu 11.10 with the default Unity desktop. I've recently changed graphics card from an Nvidia card to an ATI HD 5770.  I removed the Nvidia drivers and installed the ATI proprietary FGLRX driver.

The driver seems to be working OK, direct rendering is enabled, and tests like glxgears indicate openGL works fine.  However, I've noticed some odd behavior with window borders, and some other problems.  I'm pretty sure they didn't occur with the Nvidia driver.

1) When an app is windowed (not maximized) the borders don't update when an application gives feedback through the window titles.  For example, Firefox does not display the current page title in the border as it should do, it stays as "Ubuntu Start Page" which is my default homepage, regardless of how many pages I've been to since.  [See pic]("http://i1237.photobucket.com/albums/ff480/jonuk76/Screenshotat2012-02-04232823.png").

2) The close/minimize/maximize buttons work, but about half the time don't have the usual animation when the mouse pointer is hovered over them.

3) With Libreoffice, when re-sizing the window by dragging a corner, it can cause issues where the window turns darker, and stays darker, and an orange border stays around the outside.  This interferes with other windows.  For example in [this picture]("http://i1237.photobucket.com/albums/ff480/jonuk76/Screenshotat2012-02-04233542.png"), after re-sizing LibreOffice Writer to deliberately cause the issue, I opened a terminal and put it over the top of LO.  You can see the border and shading affecting the terminal window.  If this happens the only way to cure it is to close and restart LibreOffice.

The first and third issues are a real annoyance for me, while the second is somewhat trivial.

Switching to Unity 2D solves all of these problems, but really the 3D desktop should work, shouldn't it?  I'm not sure it can be blamed on driver problems alone, as I use the same driver in OpenSUSE KDE, and that does not have any notable issues.

Thanks

---

### Post by kherring7383 on 2012-02-04
Unfortunately Linux in general has had some problems with ATI graphics cards that's why many Linux veterans always use Nvidia, especially for 3D rendering.

I currently work for a company that builds Linux boxes for some high end clients who use Nvidia exclusively because it's a superior product and has good tech support.

Several years ago when I decided to make the move to Ubuntu, all the research I did recommended  using Nvidia cards. Just about every new build I do now I always suggest  Nvidia.

I'm sure you had you're reasons for moving to ATI, but you might want to experiment to see an Nvidia card solves you're problem.

Good Luck.

---

### Post by JonUK76 on 2012-02-04
Thanks, yes I could do that but would rather not :(  The reason for ATI was because I've had a couple of hardware failures of Nvidia cards in the past year or two (this was to replace a broken 9800GT), and really I needed something at short notice.  The HD 5770 just came up in stock locally at the right price.  I do agree with what you say though, AMD's Linux drivers are well off the pace it seems.

A little more searching has found this - which all reads as familiar issues to me.  Looks like this might not be so easy to fix :( [https://bugs.launchpad.net/unity/+bug/770283](https://bugs.launchpad.net/unity/+bug/770283)

---

### Post by JonUK76 on 2012-02-13
Just as an update if it's of interest to anyone.  I removed the ATI proprietary driver and installed the open source Radeon driver (Gallium?), and it's working much better for me.  It actually seems faster in 2D (less tearing on screen, video seems smoother) and the above mentioned bugs do not affect this driver.  Minor annoyance is the video cards fan appears to be at 100% all of the time with this driver - I'm sure this is something that can be changed with tweaking but I'm not sure how at the moment.

I ran into some issues during the attempt to change drivers....

- I disabled the proprietary ATI driver through "Additional Drivers" in System Settings and rebooted.  This resulted in an unbootable system.  I naively assumed it would fall back to a generic VESA driver, but unfortunately not.  Attempting to boot the system resulted in my monitors switching off during the boot process and no video output at all was possible.  Even the console (tty) did not work.

I got around this by booting to "Recovery Mode" (which revealed an unrelated bug as my USB keyboard was not recognised in recovery mode - had to use a PS/2 keyboard) and followed the instructions on this page to purge the ATI FGLRX driver using the console - [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)  I followed the "fully remove FGLRX and install ATI from scratch" instructions.

- The system still would not start up to the graphical login screen, but would get so far before appearing to hang, so I CTRL-ALT-F1'd to a console and manually deleted the xorg.conf file ("sudo rm /etc/X11/xorg.conf")and rebooted.  This worked.

---

