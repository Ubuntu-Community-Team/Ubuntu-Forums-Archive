---
title: "Install Google Earth in Ubuntu 9.04"
date: 2011-03-06
forum: General Help
---

### Post by atravnic on 2011-03-06
Hi there -- I started to follow the Tombuntu instructions, downloaded and saved the Google Earth installer for Linux, located the downloaded file whose name [google-earth-stable_current_i386.deb] is different from that given in the instructions [GoogleEarthLinux.bin], right clicked the downloaded file, expand the "Use a custom command" section of the "Open With" dialog, typed sh, click "Open", and......nothing happened. The "Google Earth Setup" window of the next step never appeared.

Can anyone please help me out. Thank you?      ...Fred

---

### Post by jcolyn on 2011-03-06
If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by scouser73 on 2011-03-06
Enter this command into Terminal.

**> sudo apt-get install lsb-core**

Now download Google Earth: [http://www.google.com/earth/index.html](http://www.google.com/earth/index.html)
install and enjoy.

---

