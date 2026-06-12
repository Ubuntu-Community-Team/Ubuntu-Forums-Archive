---
title: "You Tube videos don't play anymore, Flash player remove by upgrade Ubuntu 9.04 64-bit"
date: 2010-06-03
forum: General Help
---

### Post by daldude on 2010-06-03
The latests update to Ubuntu Linux 9.04 64-bit for some reason removed Flash player and now streaming videos won't play anymore. First How Do I reinstall the 64-bit version or a 32-bit version that is stable if the 64-bit version is still in Beta and there for buggy and lacking some features the official release supports?
Second 
Why was it removed? Everyone uses Youtube so why do they make it so most people are turned off of Linux and encurgae them to go back to Windows where flash is supported?
:mad::confused:

---

### Post by lovinglinux on 2010-06-03
I don't think it remove it. The most likely scenario is that now a another plugin that was already installed is being loaded first.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by daldude on 2010-06-04
It did remove it because it said so before I updated my system and I figured it would reinstall the updated version since Flash is neede for many features on the INTERNET.

It said To Be removed
flash installer
flash non free

I installed FLASH-AID and it installed the buggy BETA 2 of the 64-bit version and did not have a choice of the regular stable 64-bit flashthe only choices wewe 64-bit Beta 2 or 32-bit Beta 2 and now when I try to play cretin Youtube videos Firefox crashes. I disabled Flash in the plugins tab but don't know how to remove it to maybe try to install the stable version of Flash.
How do I install the non beta 64-bit version of flash? 

> **lovinglinux said:**
> I don't think it remove it. The most likely scenario is that now a another plugin that was already installed is being loaded first.

Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

---

### Post by oldos2er on 2010-06-04
As far as I know there is no "non-beta" flash yet. The latest is here: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by lovinglinux on 2010-06-04
> **daldude said:**
> It did remove it because it said so before I updated my system and I figured it would reinstall the updated version since Flash is neede for many features on the INTERNET.

It said To Be removed
flash installer
flash non free

I installed FLASH-AID and it installed the buggy BETA 2 of the 64-bit version and did not have a choice of the regular stable 64-bit flashthe only choices wewe 64-bit Beta 2 or 32-bit Beta 2 and now when I try to play cretin Youtube videos Firefox crashes. I disabled Flash in the plugins tab but don't know how to remove it to maybe try to install the stable version of Flash.
How do I install the non beta 64-bit version of flash?

There is no stable 64bit flash. The version you get with my tool is the latest 64bit version available. 

I have labeled the 32bit version as Beta because it has the same version number of the 64bit. I'm not sure if it is really a beta, but it causes more problems than the 64bit.

About your crashes, check if you have libmoon installed and remove it. This package is causing such issues. Also start Firefox from a terminal and post the output when it crashes.

---

### Post by daldude on 2010-06-05
How do I remove FLASH? Most of the videos I try to play crash Firefox and all I can do is disable Flash but can't remove it, not even in synaptic package manager because it won't let me mark it for complete removal.
Or how Do I run Flash-Aid so it can remove Flash assuming it has that ability.

> **lovinglinux said:**
> There is no stable 64bit flash. The version you get with my 
tool is the latest 64bit version available. 

I have labeled the 32bit version as Beta because it has the same version number of the 64bit. I'm not sure if it is really a beta, but it causes more problems than the 64bit.

About your crashes, check if you have libmoon installed and remove it. This package is causing such issues. Also start Firefox from a terminal and post the output when it crashes.

---

### Post by lovinglinux on 2010-06-05
> **daldude said:**
> How do I remove FLASH? Most of the videos I try to play crash Firefox and all I can do is disable Flash but can't remove it, not even in synaptic package manager because it won't let me mark it for complete removal.
Or how Do I run Flash-Aid so it can remove Flash assuming it has that ability.

I will add an option to completely remove flash on the next version.

You can do it form command line like this:

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by daldude on 2010-06-05
This is the most aggravating thing I've ever had with my PC, no matter how many times I reinstall Flash it always crashes Firefox when I try to play most videos in Youtube and using Synaptic Package Manager just gives me errors and it seems there are conflicts or missing system files or something that can't be resolved without a complex annalists of my system that would take hours of chaseing dead end solutions all because Updae Manager screwed up and removed files related to flash not to mention screwed up my WINE Installation so now the only solution seem to be what is usually associated to Windows, I complete reinstall of the operating system. Why does Ubuntu not have it own version of system restore where one can restore back to an earlier time before the damage was done to the OS? I guess I should have not set Update Manager to delete older kernels and just delete them manually once the newer one has be explored and assure it has no major bugs or has not be screwed up like my system has.:(:mad:

---

### Post by lovinglinux on 2010-06-05
> **daldude said:**
> This is the most aggravating thing I've ever had with my PC, no matter how many times I reinstall Flash it always crashes Firefox when I try to play most videos in Youtube and using Synaptic Package Manager just gives me errors and it seems there are conflicts or missing system files or something that can't be resolved without a complex annalists of my system that would take hours of chaseing dead end solutions all because Updae Manager screwed up and removed files related to flash not to mention screwed up my WINE Installation so now the only solution seem to be what is usually associated to Windows, I complete reinstall of the operating system. Why does Ubuntu not have it own version of system restore where one can restore back to an earlier time before the damage was done to the OS? I guess I should have not set Update Manager to delete older kernels and just delete them manually once the newer one has be explored and assure it has no major bugs or has not be screwed up like my system has.:(:mad:

Please post the errors.

---

### Post by daldude on 2010-06-05
For Flashplugin installer[B]

"Could not mark all packages for installation
[/B]
The following packages have unresolved dependencies
Make sure that all required repositories are are added and 
enabled in preferences.

flashplugin-installer:
 Depends: nspluginwrapper but it is not going to be installed
 Depends: ia32-libs but it is not going to be installed"


For flash plugin nonfree

[B]"Could not mark all packages for installation
[/B]
The following packages have unresolved dependencies
Make sure that all required repositories are are added and 
enabled in preferences.

flashplugin-nonfree:
 Depends: flashplugin-installer but it is not going to be installed"


I have Main Server selected for Download from in Software Sources and Update Manager

---

### Post by lovinglinux on 2010-06-05
> **daldude said:**
> I have Main Server selected for Download from in Software Sources and Update Manager

Do you have the multiverse repository enabled? It should be enabled by default, unless you deselected it.

BTW, what happened to WINE?

---

### Post by daldude on 2010-06-06
I think I have multiverse repository enabled is it the "Software Restricted by Copyright (multiverse) repository" setting under repositories ? Then if so Yes it is check marked.

WINE is stil messed up and can't be removed or re installed and it won't launch.

> **lovinglinux said:**
> Do you have the multiverse repository enabled? It should be enabled by default, unless you deselected it.

BTW, what happened to WINE?

---

### Post by lovinglinux on 2010-06-06
> **daldude said:**
> WINE is stil messed up and can't be removed or re installed and it won't launch.

When the problem with Wine started? I mean after using my tool, after uninstalling something?

Have you tried to delete or rename the .wine folder? If you do that you will reset Wine.

---

### Post by daldude on 2010-06-07
Is there a log kept on what changes Update Manager makes? 
I started having all these problems after Update Manager removed Flash and I think some other files or services and I assumed it would replace the services and files it removed with the updated versions, after all if one does something like drink all the milk or empty a bottle of a particular condiment they are expected to replace them. 

It had some message about being a partial update and that some updates could not be installed but I forgot what the reason was or what the possible causes it said could have been the reason why it could not install updates.

---

### Post by lovinglinux on 2010-06-07
> **daldude said:**
> Is there a log kept on what changes Update Manager makes? 
I started having all these problems after Update Manager removed Flash and I think some other files or services and I assumed it would replace the services and files it removed with the updated versions, after all if one does something like drink all the milk or empty a bottle of a particular condiment they are expected to replace them. 

It had some message about being a partial update and that some updates could not be installed but I forgot what the reason was or what the possible causes it said could have been the reason why it could not install updates.

You can see the history in Synaptic Package Manager.

---

