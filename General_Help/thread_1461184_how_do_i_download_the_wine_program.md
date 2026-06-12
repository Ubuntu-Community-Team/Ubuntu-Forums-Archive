---
title: "how do i download the wine program?"
date: 2010-04-23
forum: General Help
---

### Post by titandrake on 2010-04-23
How do I download the wine program?

---

### Post by Doug11 on 2010-04-23
You should be able to find it in the software centre or under the synaptic package manager.

---

### Post by oldfred on 2010-04-24
I found a site on how to run teh windows version of Picasa in wine.

This is from my history, but I think I had to move picasa to the program subdirectoy before it would install. It also needs some extras like better fonts.

  339  cd /usr/bin
  340  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
  341  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
  342  sudo chmod 777 winetricks
  343  sudo apt-get install cabextract wine wine-gecko
  344  winetricks allfonts fontsmooth-rgb gecko allfonts
  345  wine picasa35-setup.exe
  346  winecfg

[http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html#more-2019)
[http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html](http://www.omgubuntu.co.uk/2009/09/picasa-35-linux-install.html)

---

### Post by stvdel on 2010-04-24
Go to Applications/Ubuntu Software Center then type in Wine in the search box. Click on the arrow and install it. If you want to install the latest version for 9.10 add 
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main 
and 
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main 
to your System/Administration/Software Sources/Other Software click on the add button and add them one at a time. Then click close and close. Go to your System/Administration/Update Manager and check for updates and then install.

---

