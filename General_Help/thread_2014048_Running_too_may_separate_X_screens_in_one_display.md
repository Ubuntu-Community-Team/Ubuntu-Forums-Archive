---
title: "Running too may separate X screens in one display"
date: 2012-07-01
forum: General Help
---

### Post by Mojomagus on 2012-07-01
I recently got an extra screen and connected it to my Ubuntu 12.04 box. When I was adjusting the configuration on the NVIDIA X server settings I choose numerous times the display option to configure a separate X screen.

Every time I would choose this option and after a restart my top menu bar (using GNOME classic) would multiply and along with that every time I launch an application multiple instances of the application appears.

What I think is happening is that Ubuntu is now running a number of separate X screens and all of them aprearing in one screen (display:0).

Any ideas on how I fix this or just back to the defult configuration? I've tried uninstalling the NVIDIA drivers, reconfiguring xserver, deleting xorg.conf, all with no success.

Thanks

---

### Post by pelle.k on 2012-08-08
You're not alone. It shouldn't happen if you choose a twinview or xinerama setup though. Personally i get wierd window placement behaviour in any other mode than separate x screens, so i feel those options are sub-optimal. I'll be sure to report back i find a solution to the problem.

---

### Post by papibe on 2012-08-08
Hi Mojomagus.

I have 2 monitors each running a separate X screen. Both working OK using the Nvidia driver.

Try this: run the 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```
Then set your monitors as separate X screens. When you have everything working as it should, save the configuration file:
```
X Server Display Configuration -> Save to X Configuration File
```
Now your settings should remain the same after the next restart.
Regards.

---

### Post by Mojomagus on 2012-08-15
Thanks for the replies guys.

I'm not sure what was happening exactly but NVIDIA was definetely messing up GNOME.

I managed to get my desktop back to normal by resetting the GNOME configuration to default by deleteing the file /.config/dconf/user.

Not a very elegant solution I know. Since then I've given up using my extra screen but as soon as I gather courage again I'll give it another shot.

---

