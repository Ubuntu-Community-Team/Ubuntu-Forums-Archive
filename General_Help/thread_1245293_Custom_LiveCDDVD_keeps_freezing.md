---
title: "Custom LiveCD/DVD keeps freezing"
date: 2009-08-20
forum: General Help
---

### Post by gotenks05 on 2009-08-20
Recently, I have created a custom LiveDVD of Ubuntu, in order to take away the hassle of Java, the Internet, and multimedia, which was really successfully in my trial runs.  I now use it as my Ubuntu installation media, but I want to make an even more personalized version of Ubuntu, where Thunderbird accepts a Vcard as the entire addressbook, instead of individual people and my own backgrounds/wallpapers loaded, as well as have Thunderbird at the top of the screen instead of evolution.  Well, I have looked the information and got those parts to work out by placing things in the appropriate places, like /usr/share/ and /etc/skel/.  I even copied the Thunderbird folder from my home directory and deleted all information regarding my own email account, but I am now encountering a problem that did not happen when I made my original custom LiveDVD.  Testing the iso in Virtualbox and on an actual machine, the operating system locks up or freezes.  However, my computer, which is running Ubuntu on a second partition, which is being used to create the LiveDVD, does not freeze up like that.  For example, opening a wine application and the the screen resolution window freezed it.  Thunderbird locked up after using a wine application and I could not do anything on the main interface of the liveDVD, forcing me to reboot.  It has also freezed when I opened gparted.  How can I stop the freezing and keep the settings I want?  I am using remastersys on Ubuntu 8.04 with all the current updates.

Also, I got the information from the Klikit site regarding what folders to copy into the /etc/skel/, upon a search for changing the default wallpaper on a remastersys liveDVD, and the linuxmint forums for the location of the wallpapers and changed the text files to the new locations, so remastersys would load the right wallpaper.

---

