---
title: "Problems with flash"
date: 2010-05-29
forum: General Help
---

### Post by Gizbuntu on 2010-05-29
See the attached picture.

I'm using Ubuntu 10.04.

I've tried removing and re-installing flash using both Terminal and Ubuntu Software Center to no avail.

Can I get some help with this?

---

### Post by Ozymandias_117 on 2010-05-29
What flash player are you trying to use?

---

### Post by Gizbuntu on 2010-05-29
D'oh!

Shockwave Flash Plugin.

---

### Post by Ozymandias_117 on 2010-05-29
Have you tried other sites - maybe the problem is with that particular site?

What do you get with ```
ls -l /etc/alternatives/mozilla-flashplugin
```

---

### Post by Gizbuntu on 2010-05-29
I've tried Youtube, Grooveshark, and multiple flash game based sites. All of them fail to load flash.

Terminal output:

```
lrwxrwxrwx 1 root root 43 2010-05-29 18:40 /etc/alternatives/mozilla-flashplugin -> /usr/lib/swfdec-mozilla/libswfdecmozilla.so
```

---

### Post by takisan on 2010-05-29
> **Gizbuntu said:**
> I've tried Youtube, Grooveshark, and multiple flash game based sites. All of them fail to load flash.

Terminal output:

```
lrwxrwxrwx 1 root root 43 2010-05-29 18:40 /etc/alternatives/mozilla-flashplugin -> /usr/lib/swfdec-mozilla/libswfdecmozilla.so
```
Well, have you been sudo apt-getting flash or have you been installing via firefox. It could be anything, but the worst would be that the package is broken.

I, personally, hate Flash and think that Java should win. Shockwave and Adobe Flash are technically different things, so try both. And from what I've heard, avoid GNASH.

---

### Post by Gizbuntu on 2010-05-29
I did ```
 sudo apt-get install ubuntu-restricted extras
```

---

### Post by Ozymandias_117 on 2010-05-29
If you are okay with installing stuff that isn't open source, I would try ```
sudo aptitude install flashplugin-nonfree
```

---

### Post by Gizbuntu on 2010-05-29
I'll try it and let you know if all goes well.

---

### Post by Gizbuntu on 2010-05-29
That didn't work either. What do I try now?

---

### Post by oldos2er on 2010-05-29
Can you please post the output from "sudo aptitude install flashplugin-nonfree" so we can see where it failed?

---

### Post by Gizbuntu on 2010-05-29
```
gizmo@gizmo-laptop:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  flashplugin-nonfree 
0 packages upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B/1,770B of archives. After unpacking 41.0kB will be used.
Writing extended state information... Done
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 164062 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.45.2ubuntu1_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.45.2ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
```That's the output. Doesn't appear to be anything wrong with it. =/

---

### Post by oldos2er on 2010-05-29
So if you restart Firefox, does flash work?

---

### Post by Ozymandias_117 on 2010-05-29
If not:
```
ls -l /usr/lib/flashplugin-installer
```

---

### Post by Gizbuntu on 2010-05-30
oldos, restarting Firefox does not work.

Ozy, here is the output from the code you gave me:
```
 gizmo@gizmo-laptop:~$ ls -l /usr/lib/flashplugin-installer
total 10052
-rw-r--r-- 1 root root 10291000 2010-05-29 18:43 libflashplayer.so
```

---

### Post by Ozymandias_117 on 2010-05-30
In firefox type ```
about:plugins
``` and post what it shows under "Shockwave Flash"

---

### Post by lovinglinux on 2010-05-30
You need to remove swfdec.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Gizbuntu on 2010-05-30
I also tried uninstalling swfdec and using FLASH-AID. Neither solutions solved the problem.

As requested, the Shockwave Flash output is attached in a picture. The part underneath the cursor reads "File:  dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so".

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> I also tried uninstalling swfdec and using FLASH-AID. Neither solutions solved the problem.

As requested, the Shockwave Flash output is attached in a picture. The part underneath the cursor reads "File:  dosdevices_c^3A_windows_system32_Macromed_Flash_NPSWF32.dll.so".

It seems you are using the Windows flash version with Wine. Try to remove it from Wine interface. If it doesn't work, then delete the ~/.wine folder (if you don't have any important installed with Wine) and restart Firefox.

This is not the first time I see this problem, which is weird.

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> It seems you are using the Windows flash version with Wine. Try to remove it from Wine interface. If it doesn't work, then delete the ~/.wine folder (if you don't have any important installed with Wine) and restart Firefox.

This is not the first time I see this problem, which is weird.

I removed the WINE folder as requested. Now Swiftfox claims that "Additional plugins are required to display all media on this page". I know I should now install the flash plugin, but I just wanted to make sure beforehand in case I screw something up again.

Basically, which plugin should I use? Adobe, swfdec or gnash? I'd like to avoid gnash as previously mentioned.

---

### Post by cuberts on 2010-05-30
> **Gizbuntu said:**
> See the attached picture.

I'm using Ubuntu 10.04.

I've tried removing and re-installing flash using both Terminal and Ubuntu Software Center to no avail.

Can I get some help with this?I also had this problem, but I was able to solve this by installing google chrome for ubuntu linux. you can install it by going to this link: [http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha)

I hope that this will help you with that problem that you are having

---

### Post by Gizbuntu on 2010-05-30
> **cuberts said:**
> I also had this problem, but I was able to solve this by installing google chrome for ubuntu linux. you can install it by going to this link: [http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha)

I hope that this will help you with that problem that you are having

I want to fix this problem in Swiftfox, not install another browser entirely...

I've already tried Chrome. I dislike having my data mined.

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> I removed the WINE folder as requested. Now Swiftfox claims that "Additional plugins are required to display all media on this page". I know I should now install the flash plugin, but I just wanted to make sure beforehand in case I screw something up again.

Basically, which plugin should I use? Adobe, swfdec or gnash? I'd like to avoid gnash as previously mentioned.

Now use [FLASH-AID](http://flash-aid-extension.blogspot.com/). It will install the Adobe version and it will work.

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> Now use [FLASH-AID]("http://flash-aid-extension.blogspot.com/"). It will install the Adobe version and it will work.

There is no option to re-activate FLASH-AID. I tried un/re-installing it but that did not work.

When I tried to install the Adobe plugin manually, Swiftfox claimed that the package flashinstaller-plugin was already installed. As such, I un-installed it and installed it from the browser.

Flash STILL fails to load.

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> There is no option to re-activate FLASH-AID. I tried un/re-installing it but that did not work.

The automated installation only works when you install the extension for the first time or when you update the extension. This is done to avoid prompting for installation on every start. Nevertheless, you can access the extension functions from the status bar. There is an icon there with a menu.

> **Gizbuntu said:**
> When I tried to install the Adobe plugin manually, Swiftfox claimed that the package flashinstaller-plugin was already installed. As such, I un-installed it and installed it from the browser.

Flash STILL fails to load.

I have just released a new version of the extension that should take care of that problem. Please install the new version, run the automatic flash installer, restart Firefox, then test if it works. If not, go to about[noparse]:[/noparse]plugins, copy the flash path and paste it here.

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> I have just released a new version of the extension that should take care of that problem. Please install the new version, run the automatic flash installer, restart Firefox, then test if it works. If not, go to about[noparse]:[/noparse]plugins, copy the flash path and paste it here.

I updated FLASH-AID and used the auto-installer for Flash. It didn't work.

There is now no entry for Flash in about[noparse]:p[/noparse]lugins. I'm guessing we're getting somewhere now.

I tried manually installing the Adobe plugin again. Yet AGAIN, Swiftfox claims that the flashplugin-installer is already installed...

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> I updated FLASH-AID and used the auto-installer for Flash. It didn't work.

There is now no entry for Flash in about[noparse]:p[/noparse]lugins. I'm guessing we're getting somewhere now.

Did you get any errors from the terminal output? Have you restarted Firefox? Are you installing the 32bit or the 64bit version?

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> Did you get any errors from the terminal output? Have you restarted Firefox? Are you installing the 32bit or the 64bit version?

I got a few prompts asking me whether or not I wished to continue, but no errors as such. I have restarted Swiftfox each time I've tried anything, and I'm using the 32-bit version, as swiftfox-prescott only comes in that architecture.

---

### Post by lovinglinux on 2010-05-30
It seems Swiftfox has some bug, because it is not recognizing the flash plugin, but it does recognize other plugins. Additionally, if I delete the pluginreg.dat file, which should force it to reload the list of installed plugins, then I doesn't recognize any plugins.

---

### Post by lovinglinux on 2010-05-30
There is definitely a bug in Swiftfox that prevents it from recognizing any new installed plugin. If you start Firefox using the same user profile, then close Firefox and start Swiftfox it does recognize the plugins, but they don't work. I would recommend switching to the default Firefox for now.

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> There is definitely a bug in Swiftfox that prevents it from recognizing any new installed plugin. If you start Firefox using the same user profile, then close Firefox and start Swiftfox it does recognize the plugins, but they don't work. I would recommend switching to the default Firefox for now.

What a shame...

I'll switch to Chrom**ium** for now.

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> What a shame...

I'll switch to Chrom**ium** for now.

Please confirm if you can load the plugin properly with Firefox instead of Swiftfox. I want to make sure is a Swiftfox issue.

---

### Post by Gizbuntu on 2010-05-30
> **lovinglinux said:**
> Please confirm if you can load the plugin properly with Firefox instead of Swiftfox. I want to make sure is a Swiftfox issue.

Firefox loads the plugin just fine, yes. Flash is present in the about[noparse]:[/noparse]plugins list on _Firefox_, but not on Swiftfox.

---

### Post by lovinglinux on 2010-05-30
> **Gizbuntu said:**
> Firefox loads the plugin just fine, yes. Flash is present in the about[noparse]:[/noparse]plugins list on _Firefox_, but not on Swiftfox.

Thanks. Do flash work fine in Firefox?

---

