---
title: "Firefox adobe flash plugin can no longer be enabled"
date: 2010-05-09
forum: General Help
---

### Post by p0nman on 2010-05-09
I hope this is not the wrong place to post this because it is specifically  firefox/flash issue.  However,  I'm having an issue changing the flash plug to display flash.  I clean installed 10.04 a week ago, upgraded to to the closed source adobe plugin, and everything was great.  However, a day ago, I had an issue with one site, and I decided to switch back to the default swfdec player.  Since that time I have not been able to switch back to adobe.  Every time I attempt to, firefox complains that adobe is already installed.  Even if I remove the adobe flash plugin via synaptic and allow firefox to reinstall it, it still uses swfdec.

---

### Post by James78 on 2010-05-09
There are a few ways to try to change what flash plugin Firefox uses.

1) Remove and reinstall, but you tried that. Is swfdec still installed? If so perhaps purging it can help, but don't get rid of it if it requires some dependencies you need. (I think Gnome requires it for some odd reason...)
2) Visit a flash website, and you should see a little blue plugin icon in the status bar at the bottom of the page, you can click on it and change the flash plugin being used to render flash content.
3) In Firefox, go to Edit -> Preferences -> Applications. Find Shockwave Flash (there might be 2), and for both of them, use the dropdown to find Shockwave Flash.
4) Run "sudo update-alternatives --config flash", and you might be able to select Adobe's flash player from the list.

I recommend using #4 first, as it should create the necessary symlinks, versus the other methods.

On the dropdowns for selecting the flash plugin, Adobe's flash plugin might not be listed, you might need to manually find it. It's located at /usr/lib/flashplugin-installer/libflashplayer.so

And, if all else fails, deleting your Firefox profile @ ~/.mozilla will most likely reset the application preferences, then letting Firefox recreate a new profile and reinstalling the plugin from say, a site, would make it gain control again.

---

### Post by p0nman on 2010-05-09
> **James78 said:**
> There are a few ways to try to change what flash plugin Firefox uses.

1) Remove and reinstall, but you tried that. Is swfdec still installed? If so perhaps purging it can help, but don't get rid of it if it requires some dependencies you need. (I think Gnome requires it for some odd reason...)
2) Visit a flash website, and you should see a little blue plugin icon in the status bar at the bottom of the page, you can click on it and change the flash plugin being used to render flash content.
3) In Firefox, go to Edit -> Preferences -> Applications. Find Shockwave Flash (there might be 2), and for both of them, use the dropdown to find Shockwave Flash.
4) Run "sudo update-alternatives --config flash", and you might be able to select Adobe's flash player from the list.

I recommend using #4 first, as it should create the necessary symlinks, versus the other methods.

On the dropdowns for selecting the flash plugin, Adobe's flash plugin might not be listed, you might need to manually find it. It's located at /usr/lib/flashplugin-installer/libflashplayer.so

And, if all else fails, deleting your Firefox profile @ ~/.mozilla will most likely reset the application preferences, then letting Firefox recreate a new profile and reinstalling the plugin from say, a site, would make it gain control again.

Those are good suggestions, but none worked.  The 'blue' plugin icon?  mine's grey, but still playing with swfdec. The drop down box it shows is where I've been trying to change it the whole time.  It won't switch to adobe.  I attempted to change it in [http://about:config](http://about:config) --> modules.plugins.mimetype.application/x-shockwave-flash  by changing this value to: libflashplayer.so but no change.  It uses swfdec anyway.  

I think this is a bug.

---

### Post by James78 on 2010-05-09
It probably is, you should report it as a precaution, maybe someone will come up with a fix. Good luck!:)

---

### Post by lovinglinux on 2010-05-10
```
sudo apt-get remove swfdec-mozilla
sudo apt-get install flashplugin-nonfree
```

---

### Post by p0nman on 2010-05-11
> **lovinglinux said:**
> ```
sudo apt-get remove swfdec-mozilla
sudo apt-get install flashplugin-nonfree
```

I didn't need the second piece because it was already installed and apt-get updated my dependencies automatically!

I still believe this is a bug ([https://bugs.launchpad.net/ubuntu/+bug/578069](https://bugs.launchpad.net/ubuntu/+bug/578069)), I shouldn't have to uninstall swfdec to use the adobe version, but at least I'm back up and running again, thanks!


> Removing swfdec-mozilla ...
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/iceape/plugins/flashplugin-alternative.so (iceape-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/iceweasel/plugins/flashplugin-alternative.so (iceweasel-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/xulrunner/plugins/flashplugin-alternative.so (xulrunner-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/midbrowser/plugins/flashplugin-alternative.so (midbrowser-flashplugin) in auto mode.
update-alternatives: using /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to provide /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so (xulrunner-addons-flashplugin) in auto mode.


---

