---
title: "Today's updates ruined my nVidia driver"
date: 2009-07-22
forum: General Help
---

### Post by DeMus on 2009-07-22
Today I received a large amount of updates, new installs, even a removal of a package. Included, as an update, was the nVidia 190 driver.
I started the install and after the reboot I ended up in CLI. Then I got a message the graphical driver used a low resolution which I could repair. I did and ended up in my normal desktop.
I went to Hardware drivers and saw that my proprietary driver was not activated so I tried doing that. The message I got is visible in the attached picture.
When I start nVidia-settings I get a message my nVidia driver is not installed. According to Synaptic I use the new 190 driver.
What to do now?

Somebody please help.

---

### Post by JK3mp on 2009-07-22
Yikes. I've heard of similiar issue's and usually just a reinstall of the drivers help. Or rollback and use the old ones. Sometimes when you see alot of updates you may wanna pick and choose(from the non security ones) which to install or not install, because some may break certain things on your install. If it insists that you already have the new nvidia drivers installed, try reinstalling the old ones.(may first require removal of new ones). Personally i see no reason in updating graphics drivers if your current one is working just fine. Best of luck.
-Peace

---

### Post by NightwishFan on 2009-07-22
Run a whole slew of commands. Nvidia 190 destroyed my apt (way long time ago in pre-beta), and I was forced to reinstall. Hopefully that is not what is wrong for you. :(

Try this:

```
sudo apt-get update && sudo apt-get -f install
```

Before you say 'yes' if the command asks you, please post the output here as a copy/paste or screenshot.

---

### Post by DeMus on 2009-07-22
> **NightwishFan said:**
> Run a whole slew of commands. Nvidia 190 destroyed my apt (way long time ago in pre-beta), and I was forced to reinstall. Hopefully that is not what is wrong for you. :(

Try this:

```
sudo apt-get update && sudo apt-get -f install
```

Before you say 'yes' if the command asks you, please post the output here as a copy/paste or screenshot.

After the list of repositories I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-11
  linux-headers-2.6.28-12 linux-headers-2.6.28-12-generic
  nvidia-180-kernel-source nvidia-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What's next?

---

### Post by NightwishFan on 2009-07-22
Ok, all seems well. Try:

```
sudo apt-get remove nvidia-glx-190 && sudo apt-get install nvidia-glx-180 && sudo apt-get autoremove && sudo apt-get -f install
```

Edit, on a related note, you would need a ppa (3rd party repository) to have an update to Nvida 190, as it is not officially supported.

---

### Post by piratebill on 2009-07-22
Have you tried installing the previous driver using envy?

---

### Post by DeMus on 2009-07-22
> **NightwishFan said:**
> Ok, all seems well. Try:

```
sudo apt-get remove nvidia-glx-190 && sudo apt-get install nvidia-glx-180 && sudo apt-get autoremove && sudo apt-get -f install
```

Edit, on a related note, you would need a ppa (3rd party repository) to have an update to Nvida 190, as it is not officially supported.

Yes, I do have that repository.
This is what I get following your command line:

sudo apt-get remove nvidia-glx-190 && sudo apt-get install nvidia-glx-180 && sudo apt-get autoremove && sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-190 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-11 linux-headers-2.6.28-12
  linux-headers-2.6.28-12-generic nvidia-180-kernel-source nvidia-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-180: Depends: nvidia-180-libvdpau (>= 180.44) but it is not going to be installed
E: Broken packages

When you look in the picture in my first post it also says something about broken packages. How can I find them and how to get rid of them?

Thanks very much for your help.

---

### Post by NightwishFan on 2009-07-22
That is what 'apt-get -f install' is supposed to do. Try it again, alone. (This might be what had happened to me. I recommend the Nvidia 185 drivers frankly.)

Keep me posted, I will be on for about 10-15 more mins.

---

### Post by DeMus on 2009-07-22
> **NightwishFan said:**
> That is what 'apt-get -f install' is supposed to do. Try it again, alone. (This might be what had happened to me. I recommend the Nvidia 185 drivers frankly.)

Keep me posted, I will be on for about 10-15 more mins.

First I got this:
```
sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-11 linux-headers-2.6.28-12
  linux-headers-2.6.28-12-generic nvidia-180-kernel-source nvidia-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Then I used Synaptic to uninstall 2.6.28.11 and 2.6.28.12 completely (headers and images), fakeroot and dkms (which I installed again)

Then I got this:

```
sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I uninstalled it using Synaptic. Then it was:

```
sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I though: Yes, got it.
Went back to your initial line and got:

```
sudo apt-get remove nvidia-glx-190 && sudo apt-get install nvidia-glx-180 && sudo apt-get autoremove && sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-190 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-180: Depends: nvidia-180-libvdpau (>= 180.44) but it is not going to be installed
E: Broken packages


In Synaptic for nVidia I see what is visible in the attached picture.
What can I uninstall and what do I need to install to get a driver which uses the 3D capabalities of my videocard?

Thanks.

---

### Post by Arup on 2009-07-22
Demus,

Are you installing nvidia from ppa by any chance? I upgraded my nvida to 190 beta and it installed fine via .sh

---

### Post by NightwishFan on 2009-07-22
Perhaps you should remove the new Nvidia ppa, or try the 185 driver and not the 190.

Try to install nvidia-glx-185 if possible from restricted drivers or synaptic.

If all else fails, go to software sources, remove the Nvidia ppa, and install the 180 driver in the standard repo.

Sorry, I have to leave now though, good luck.

---

### Post by DeMus on 2009-07-22
> **Arup said:**
> Demus,

Are you installing nvidia from ppa by any chance? I upgraded my nvida to 190 beta and it installed fine via .sh

In Synaptic in the sections on the left hand side I see this:

Local/Main: nvidia-180-modaliases
ppa.launchpad.net/main: nvidia-190-libvdpau

So, yes I do use ppa.

---

### Post by bear24rw on 2009-07-22
i've had problems in the past with apt-get not resolving dependancies right, but aptitude worked fine. You can maybe try doing an aptitude update and aptitude full-upgrade and see if that fixed the dependancy problem

---

### Post by stoneage on 2009-07-22
I'm guessing it would help to remove nvidia-190libvdpau, but I can't say if it is the only obstacle.

---

### Post by Arup on 2009-07-22
Remove the ppa and remove the 190 driver and linux restricted modules completely and instal via .sh download from nvidia, make sure you have build-essential installed.

---

### Post by DeMus on 2009-07-22
> **Arup said:**
> Remove the ppa and remove the 190 driver and linux restricted modules completely and instal via .sh download from nvidia, make sure you have build-essential installed.

I tried that a few times but it doesn't work. After a few questions I get a message it is looking for something and at 31% it stops.

BUT, I have good news. With Synaptic I uninstalled 190 and installed 180. I ended up in CLI. D*mn.
Then tried to restore the graphical driver which did not work, rebooted again and the GUI started. Then again in Synaptic I updated to 190 again and rebooted. Now in Hardware Drivers it says my 190 is installed and in use. Yeah.

I still say (something I am saying for a year or maybe even longer):
why does this have to be so difficult? Why can't i just update a driver without all the problems?

Anyway, it works now. I try to remember not to update again in the next future.
NightwishFan and all others who answered: thank you very much.

DeMus

---

### Post by Arup on 2009-07-22
Thats strange, if done right, it uninstalls and installs flawlessly, I keep going back and forth between beta and stable to test out features and never face any issues.

---

### Post by DeMus on 2009-07-22
> **Arup said:**
> Thats strange, if done right, it uninstalls and installs flawlessly, I keep going back and forth between beta and stable to test out features and never face any issues.

Things went wrong during a major update I got today. But with the help of all of you it works again. I must say, it looks like the screen is faster now. Windows are build faster, at least so it seems. Is there a program to test this?


[SIZE="7"]:D[/SIZE]

---

### Post by Arup on 2009-07-22
> **DeMus said:**
> Things went wrong during a major update I got today. But with the help of all of you it works again. I must say, it looks like the screen is faster now. Windows are build faster, at least so it seems. Is there a program to test this?


[SIZE="7"]:D[/SIZE]

sudo apt-get install gtkperf

---

### Post by DeMus on 2009-07-22
> **Arup said:**
> sudo apt-get install gtkperf

Thanks. With the standard setting I get 3.31 seconds. Is that fast or just so-so?

---

### Post by NightwishFan on 2009-07-23
No problem. I tried the 190 debs and they worked fine for me. As a precaution I always remove the driver before I update, though they worked fine just updating in the past.

---

