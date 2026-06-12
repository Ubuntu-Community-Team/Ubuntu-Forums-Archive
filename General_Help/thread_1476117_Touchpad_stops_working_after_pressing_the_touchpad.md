---
title: "Touchpad stops working after pressing the touchpad toggle button"
date: 2010-05-07
forum: General Help
---

### Post by phpadik on 2010-05-07
I am running Ubuntu 10.04 Lucid Lynx LTS. My laptop is an HP Pavilion TX1210AU (TX1000 series).

After disabling the touchpad using the toggle button and reenabling it again, it stopped working.

I tried restarting my laptop and the mouse worked again only up to the Login Screen. After logging in to my account, the mouse froze again. I tried making a new account and tried logging into it (I'm using it now) and it's now fixed.

Does Ubuntu change any user settings everytime the touchpad toggle (on/off) button is switched? Maybe I could just reenable it myself.

I am willing to post any relevant log files, just tell me.

---

### Post by stanley drew on 2010-05-13
I am having exactly the same problem on a HP Pavillion! How did you solve it? Only by creating a new account? Isn't there any way to make my touchpad come back?

---

### Post by RobCis on 2010-08-08
Hello I was having the same issue with my Pavillion and to solve it I did this: 

1) Hit Atl + f1 that will open the Apps menu then go to: Accessories and open a Terminal..

2) Write the following command:

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

(Note: it seems that nothing was done).

3) press CTRL+ALT+F1 in order to open the login prompt.

4) press the up arrow in order to see the command without writing it.. 

5) Reboot the Machine...  (Keep Pressed the Power Button)

:D

Rob!

---

