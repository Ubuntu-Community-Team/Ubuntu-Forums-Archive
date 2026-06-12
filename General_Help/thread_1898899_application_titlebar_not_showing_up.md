---
title: "application titlebar not showing up"
date: 2011-12-22
forum: General Help
---

### Post by netopalis45 on 2011-12-22
I just started using Oneric on a new laptop and decided to use the Ubuntu Classic desktop. When I log in to the regular Ubuntu Classic, the application titlebar does not show up. I had this problem before with an older version of Ubuntu but don't remember how it was fixed. I am currently using the Ubuntu Classic (No Effects) but would really like to get to the other one.

---

### Post by hackb0y294 on 2011-12-22
What exactly is missing? If the entire window border is missing, try running in a terminal:

```
metacity --replace
```

---

### Post by sikander3786 on 2011-12-22
First of all, Ubuntu Oneiric doesn't come with the Ubuntu Classic session by default so I guess you installed it yourself. Please confirm.

Secondly, you don't get the problem in Ubuntu Classic without effect but in the regular Ubuntu Classic with effects, you can't see the window decorations, the bar with close, minimize buttons etc., right?

---

### Post by netopalis45 on 2011-12-22
sikander3786: I did install it myself, and I guess it was the window decorations that didn't show up
hackb0y294: It worked perfectly, thanks

---

### Post by BC59 on 2011-12-22
> **sikander3786 said:**
> First of all, Ubuntu Oneiric doesn't come with the Ubuntu Classic session by default so I guess you installed it yourself. Please confirm.



Well...I think installing Advanced Settings or Gnome Tweak Tool, is installing the Classic session as well, that's why many people are confused and believe it was installed by default.

---

### Post by sikander3786 on 2011-12-22
If running the command 'hackb0y294' presented solved the issue, you still are running Metacity and not Compiz and might not get the animation effects and all that stuff. And you might also need to switch to Metacity everytime you login.

If you want to sort out the Compiz issue, please let us know if you installed the proprietary drivers (if any) for your graphics card. Output of these command would help us:

```
lshw -c video
/usr/lib/nux/unity_support_test -p
```

> **BC59 said:**
> Well...I think installing Advanced Settings or Gnome Tweak Tool, is installing the Classic session as well, that's why many people are confused and believe it was installed by default.

Yeah exactly. Just tested and got this:

```
sudo apt-get install gnome-tweak-tool
[sudo] password for tuxgarage: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
alacarte caribou cups-pk-helper gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
gir1.2-cogl-1.0 gir1.2-folks-0.6 gir1.2-gee-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0
gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs gnome-applets gnome-applets-data
gnome-icon-theme-full gnome-panel gnome-panel-data [COLOR="Red"]gnome-session
gnome-session-bin gnome-session-common gnome-session-fallback gnome-shell[/COLOR]
gnome-themes-standard libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common
libcogl5 libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0 mesa-utils mutter-common python-gmenu
```

---

### Post by Z06Gal on 2011-12-22
I am having the same issue in Gnome Classic.  No title bars, a big black box around my cairo dock and running metacity --replace, compiz --replace, compiz-decorator --replace does nothing. I cannot figure out what the issue is.  Any settings that I make do not stay.  If I close ccsm and then open it again, all the settings I made are gone.

---

### Post by netopalis45 on 2011-12-22
I bought the computer from System76 so all the drivers came preinstalled so I'm pretty sure that is not the problem. I am having to run metacity --replace almost every time I log in. If I use compiz --replace it all goes away again.

---

### Post by BC59 on 2011-12-22
Gnome Classic is over. It's not maintained. Only new projects like Mate will have some future.

---

### Post by Z06Gal on 2011-12-22
I have logged into Mate, Gnome Classic, and Cairo Dock with and without effects and it is the same with each = no compiz, no title bars, and a black box around my dock. I have seen people who downgraded metacity to fix the issue but I am not sure how to do that.

---

### Post by BC59 on 2011-12-22
The latest version of Metacity is the _metacity (1:2.34.1-1ubuntu4) oneiric_. 
Now if you like to use the older one, using Synaptic (you can install it through Ubuntu Software Center) uninstall the metacity 1:2.34.
Then go [here]("https://launchpad.net/ubuntu/oneiric/+package/metacity") and download the old one, which is metacity 1:2.30.
Be careful to download the corresponding to your computer architecture, i386 or AMD64.
When you download the .deb package, double click and let Ubuntu Software Center to install it.

---

### Post by Z06Gal on 2011-12-22
Thanks, I'll definitely try that:)

---

### Post by Z06Gal on 2011-12-22
I removed metacity and downloaded the deb file but when I click on "install package" it freezes and doesn't install.  The thing that gets me is I logged into gnome classic a couple weeks ago just to mess around with compiz and it worked great.  I have installed anything so something had to have happened in an update or something.  It just doesn't make sense to me. :confused::confused:

---

### Post by BC59 on 2011-12-23
I don't know...maybe try this. Open Synaptic and search for compiz. Then from the list of packages shown press the left column **S** on the top and you will see with green color all the packages installed of compiz. Select them and choose **Mark for complete removal**. When all are removed reinstall them again. Be careful to not forget any package to reinstall.

---

