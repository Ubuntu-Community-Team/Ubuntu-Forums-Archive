---
title: "chrome and trash help."
date: 2009-10-27
forum: General Help
---

### Post by FreezWay on 2009-10-27
I download chrome a while ago, no issues. Recently i tried out chromium, but it was buggy (i have a number of issues) and i noticed after i uninstalled both that i have 300+ megs sitting in .cache/google-chrome/Cache is this OK to delete? After uninstalling chrome i still have chrome stuff in my .config folder, despite having used purge and not remove.

Also, when i downloaded a new kernals source and compiled it, i threw away the source (dumped it in my trash,) however there is still kernal stuff there. is this ok to delete.

Finally, how do i get chrome to install in my usr/bin folder and not home?

---

### Post by bribera on 2009-10-27
Any cache files for Chrome or Chromium should be OK to delete; they only exist to speed up browsing while you're using the program, so if you've uninstalled the program they serve no purpose.

You can delete the entire kernel source directory and any binaries inside it. Just **don't** delete anything from /boot ;)

Google is now distributing a preview version of Chrome that's packaged as a .deb file -- you can grab it here: [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

If you open a .deb file from your web browser, it should open with the Package Installer. This will install the binaries in /usr/bin -- however, you'll still have some chrome-related configuration and cache folders in your home directory that are specific to your user profile.

---

### Post by FreezWay on 2009-10-27
sweet that worked... except one thing, chrome isn't in my internet folder... i can start it from my terminal but it doesn't appear there.

---

### Post by bribera on 2009-10-27
Huh, that's odd. I'm running the testing version of xubuntu, and it put it in my Network menu (which I believe is the equivalent of the Internet menu).

I believe you can create a launcher and place it in the menu (or in the panel or on your desktop) by following this guide:
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

The command for chrome is **google-chrome**

---

