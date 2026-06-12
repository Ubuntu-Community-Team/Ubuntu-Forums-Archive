---
title: "Cannot Login to GUI after Kernel Update"
date: 2010-03-04
forum: General Help
---

### Post by Jonah Bron on 2010-03-04
Hello, world!

This is my first time here.  I've had Ubuntu for a few months now, and  have been loving it.  I just recently got a newer computer, and loaded  Ubuntu onto it.  I installed all my programs and files, and everything  has been working perfectly.  The Update Manager came up, and wanted to  do some updates, so I let it.  One of them was a Kernel update.  When it  was finished, it wanted to restart, so I did.  After rebooting, I saw  the new Kernel in Grub, and proceeded to boot.

The login screen came  up, and I typed in my password as usual.  It acted as though it was  logging me in, and then it went right back to the login screen.  I tried  booting in recovery mode, and with the old kernel.  In recovery mode, I  logged in with the terminal.  When that worked, I tried to startx.   That gave me a black screen containing nothing but the cursor.  Nothing  has worked so far.

What's all this now?

Thanks in advance,

Jonah Bron

---

### Post by rnerwein on 2010-03-04
hi
you say that was a kernel update. if you don't use the native graphic driver which cames from ubuntu you have to reconfigure your ( e.g. nvidia or some other ) driver and reboot.
ciao

---

### Post by Jonah Bron on 2010-03-04
As far as I know, I'm using the native one.  No "restricted drivers" are installed, and I haven't downloaded anything from ATI.

---

### Post by Jonah Bron on 2010-03-04
Oh, I forgot: I checked in the terminal, and my user files are intact.

---

### Post by Jonah Bron on 2010-03-04
Hey!  I just tried pressing keys, and Ctrl+Alt+Right/Left moves me between my desktops.  They're all black, and the little desktop switching indicator is the lame looking static kind.  Also, the hotkey for taking a screenshot works, and that brings up the screenshot window.  It doesn't have the skin, the buttons and stuff are all flat looking.  What is going on?

---

### Post by bobnutfield on 2010-03-04
Sounds like the kernel upgrade has altered your xorg.conf somehow.  You didn't say what video chip you have, but if you have not installed any proprietory drivers, you might try this in a terminal:

> sudo dpkg-reconfigure -phigh xserver-xorg

Ubuntu will try to reconfigure your graphics based on your hardware.  This has worked for me in the past.

---

### Post by Jonah Bron on 2010-03-04
I tried that command, but it didn't work.  It didn't give me any errors, though.  In fact, It didn't give me anything.  I still get the (graphical) login window, but login is not possible.

Thanks

---

### Post by Jonah Bron on 2010-03-04
If nobody knows how to fix this, I'll have to just go ahead and reinstall :(

---

