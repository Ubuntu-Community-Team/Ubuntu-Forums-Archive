---
title: "[HOWTO] Firefox fglrx dual-head Single-Display (Multidesktop)"
date: 2012-01-05
forum: General Help
---

### Post by se4n_1 on 2012-01-05
This is my first how to. I have a dual head setup on Ubuntu Maverick and have consistently had the annoyance of the firefox failed to start because it is already running message. Mozilla have no intention of solving this as they do not consider it a bug, it is however extremely annoying.

After lots of searching I couldn't find a viable way to use firefox simultaneously on both monitors. This fix just envolves removing the lock files before firefox starts. Warning: Mozilla made the lock files for a reason, to protect your profile! Removing them probably isn't an ideal solution but it has been working for me flawlessly for a few days now. The only thing I'd suggest is not installing addons unless you've done:

$ killall firefox

$ firefox

to make sure there is only one instance running, with the correct locks when you update addons.

All that said to allow firefox to run on both screens just do this:

$ cd ~
$ gedit .firelaunch.sh

add the lines:

#!/bin/bash

rm -f /home/<user>/.mozilla/firefox/<profile>/.parentlock
rm -f /home/<user>/.mozilla/firefox/<profile>/lock

firefox [https://encrypted.google.com/webhp?complete=0](https://encrypted.google.com/webhp?complete=0)

Where <user> is your username and <profile> is the profile of your firefox. For example my <profile> is: nzqr1jfi.default, yours will be different. and the website is what you'd like the new firefox window to open onto, I like encrypted google but you can choose any website.

Next simply right click on any firefox launchers you have and change the command to:

/home/<user>/.firelaunch.sh

In unity you may need to download alacarte:

# apt-get install alacarte

$ alacarte

In order to change the launch command.

All being well; now you can use firefox on both monitors, without the annoying message saying forefox is not responding! :P

---

