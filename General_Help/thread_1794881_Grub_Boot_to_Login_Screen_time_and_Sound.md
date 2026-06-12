---
title: "Grub Boot to Login Screen time and Sound"
date: 2011-07-01
forum: General Help
---

### Post by SunfireSSR on 2011-07-01
After upgrading to 11.04, it takes ~24 seconds to get to the login screen. I unchecked the startup programs I didn't want to load, but that didn't help.
Also, I can't figure out why the Login Sound doesn't play. I've set everything I know of except for where you unmute the startup audio. thought it was in /etc/init.d/alsa(something). Any help I would appreciate.

---

### Post by ahears on 2011-07-01
> **SunfireSSR said:**
> After upgrading to 11.04, it takes ~24 seconds to get to the login screen. I unchecked the startup programs I didn't want to load, but that didn't help.
Also, I can't figure out why the Login Sound doesn't play. I've set everything I know of except for where you unmute the startup audio. thought it was in /etc/init.d/alsa(something). Any help I would appreciate.



Check your '/etc/default/grub' for timeout:

First make a backup and open the editor:

> 

sudo cp /etc/default/grub /etc/default/grub.bak && sudo gedit /etc/default/grub

The beginning of the file looks like this:

> 

GRUB_DEFAULT=0
[COLOR=Blue]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]GRUB_TIMEOUT=10[/COLOR]

[COLOR=Red]
[/COLOR][COLOR=Blue]If there is a GRUB_HIDDEN_TIMEOUT value of more than 0  you will want to change it to 0, or disable it with the '#' symbol as  show above.[/COLOR]
[COLOR=Red]
The 'GRUB_TIMEOUT=10' can be modified to less but it represents ten seconds before a GRUB_DEFAULT is chosen automatically, in this case; menu item 0.[/COLOR]

Then run 'update-grub' to update the bootloader:

> 

sudo update-grub

Done.

Now for the login sound open your menu:

> 

**System >> Administration >> Login Screen**

This should give you access to your login sound. Hopefully this helps.

---

### Post by wildmanne39 on 2011-07-01
> **SunfireSSR said:**
> After upgrading to 11.04, it takes ~24 seconds to get to the login screen. I unchecked the startup programs I didn't want to load, but that didn't help.
Also, I can't figure out why the Login Sound doesn't play. I've set everything I know of except for where you unmute the startup audio. thought it was in /etc/init.d/alsa(something). Any help I would appreciate.Hi, with ubuntu tweak you can turn the start up sound on and off, and much more. You can install it from software center.

---

### Post by ahears on 2011-07-01
> **wildmanne39 said:**
> Hi, with ubuntu tweak you can turn the start up sound on and off, and much more. You can install it from software center. 


You will need to add this to the repository before running Synaptic:

> 

**sudo add-apt-repository ppa:tualatrix/ppa **
**sudo apt-get update**
**sudo apt-get install ubuntu-tweak**


After installation, the setting is found under: **Ubuntu Tweak >> Login Settings**

---

### Post by SunfireSSR on 2011-07-02
I have already done everything you guys suggested. I also have Ubuntu Tweaks installed.
The 24 seconds is after I chose the option to start Ubuntu at the Grub Menu. The login sound is muted somewhere, but I can't find the file. None of this happened until I upgraded from 10.10 to 11.04. Before that, it was quick to load and I could unmute the login sound. Any other ideas ?

---

### Post by wildmanne39 on 2011-07-02
> **SunfireSSR said:**
> I have already done everything you guys suggested. I also have Ubuntu Tweaks installed.
The 24 seconds is after I chose the option to start Ubuntu at the Grub Menu. The login sound is muted somewhere, but I can't find the file. None of this happened until I upgraded from 10.10 to 11.04. Before that, it was quick to load and I could unmute the login sound. Any other ideas ?
Hi, go to the shutdown button and then click on system settings, when the window opens type login and it will bring up the login preferences,click on login, then click on unlock and you can put a check
by play sound at start up.

---

### Post by SunfireSSR on 2011-07-02
Did that already. It still shows it is checked though. There used to be a file /etc/init.d/alsa-utils that you could unmute the login sound that fixed this. It's gone now.

---

### Post by wildmanne39 on 2011-07-02
Hi, I am out of ideas hopefully someone else will have the answer.

---

### Post by drs305 on 2011-07-02
As far as the 24 second logon, unfortunately that seems to be a function not controlled by Grub. While there was a concerted effort to greatly reduce boot times a few releases ago, I believe this effort was relegated for things the developers thought were more important that the initial boot speed.

As far as the sound issue, have you checked the sound 'theme'? Open Dash, type 'sound' and click on 'Sound'. That will open "Sound Preferences". In the Sound Effects tab, make sure the theme is "Ubuntu", or at least NOT "no sounds". Also check the two volume sliders. You can check the speaker volume in some of the other tabs to ensure sound is working at all.

---

### Post by SunfireSSR on 2011-07-06
Thanks to everyone that helped !!!

---

