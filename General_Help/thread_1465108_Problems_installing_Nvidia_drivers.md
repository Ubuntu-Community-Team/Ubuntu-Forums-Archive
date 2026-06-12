---
title: "Problems installing Nvidia drivers"
date: 2010-04-29
forum: General Help
---

### Post by fterh on 2010-04-29
What I did:

ctrl+alt+f2, logged in, then typed:
```
sudo /etc/init.d/gdm stop
cd /home/fabian/Downloads
sudo sh NVIDIA*
```

Installation failed though, a log was saved to my system (which I deleted afterwards).

Any idea why it failed? :(

---

### Post by madverb on 2010-04-29
sudo aptitude install nvidia-current

---

### Post by GSF1200S on 2010-04-29
Alternatively, you can go to System > Administration > Hardware Drivers and just enable the Nvidia driver that way. 

*Note: This next step installs drivers that are not officially in the Ubuntu repositories- you will be installing from a Third-Party repo that has packaged the later versions*

If you have Karmic Koala (9.10), you can update to the 195 series of Nvidia drivers by doing:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```
and
```
sudo apt-get update
```
and then go to System > Administration > Hardware Drivers and enable the 195 driver. I then HIGHLY recommend that you go to System > Administration > Software Sources and DISABLE the above repository so that you dont end up updating other packages you might want left alone. Of course, you may like to live life on the edge ;)

---

### Post by fterh on 2010-04-29
> **GSF1200S said:**
> Alternatively, you can go to System > Administration > Hardware Drivers and just enable the Nvidia driver that way. 

*Note: This next step installs drivers that are not officially in the Ubuntu repositories- you will be installing from a Third-Party repo that has packaged the later versions*

If you have Karmic Koala (9.10), you can update to the 195 series of Nvidia drivers by doing:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```
and
```
sudo apt-get update
```
and then go to System > Administration > Hardware Drivers and enable the 195 driver. I then HIGHLY recommend that you go to System > Administration > Software Sources and DISABLE the above repository so that you dont end up updating other packages you might want left alone. Of course, you may like to live life on the edge ;)
What do you mean "disable the above repository"? Which repository are you referring to?

And why can't I install it from nvidia.com?

---

### Post by 3rdalbum on 2010-04-29
Use the version from Hardware Drivers wherever you can. If you install the Nvidia driver that you manually downloaded, you'll have to reinstall it every time you do a kernel update. That's a royal pain.

If you need the later version (for instance, for later hardware) note that in 10.04 you need to blacklist the Nouveau kernel module.

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Put the following at the end of the file:

```
blacklist nouveau
```

Save changes and reboot and you'll be able to manually install the Nvidia driver.

---

### Post by GSF1200S on 2010-04-29
Disable the repository I told you to **add** after you install the driver. The main Ubuntu repo is not a good one to disable ;)

You can install the one from Nvidia, but it will be extra work to do, and everytime a kernel is released, you will have to reinstall it. Its your choice of course :)

---

### Post by fterh on 2010-04-29
> **3rdalbum said:**
> Use the version from Hardware Drivers wherever you can. If you install the Nvidia driver that you manually downloaded, you'll have to reinstall it every time you do a kernel update. That's a royal pain.

If you need the later version (for instance, for later hardware) note that in 10.04 you need to blacklist the Nouveau kernel module.

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Put the following at the end of the file:

```
blacklist nouveau
```

Save changes and reboot and you'll be able to manually install the Nvidia driver.
Yeah I'm using the 10.04 LTS. Perhaps that's why installation failed. Had no idea it would be this complex just to install a simple video driver :D

---

### Post by 3rdalbum on 2010-04-29
> **fterh said:**
> What do you mean "disable the above repository"? Which repository are you referring to?

The one that has a web address containing "nvidia-vdpau". But I'd actually say to keep it active so you get updates from it. It's up to you.

---

### Post by 3rdalbum on 2010-04-29
> **fterh said:**
> Yeah I'm using the 10.04 LTS. Perhaps that's why installation failed. Had no idea it would be this complex just to install a simple video driver :D

Ubuntu makes it easy with its Hardware Drivers program in the System > Administration menu. If you don't want to use the Hardware Drivers program, then it becomes more complex. Nvidia's installer is a bit archaic, and I'm trying to get them to make an easier one.

---

### Post by w0ss4g3 on 2010-04-29
I'm having a similar problem today, although the driver will install.. but X seems to crash on boot.

I'm running 9.10 and I just updated to the new kernel 2.6.31-21 (was on -20). Before the update I was running the 195.36.24 drivers which I'd got from the nvidia site. I can reinstall the driver when running the new kernel, but it boots into low graphics mode :(

If I add the repo to my sources, I still only have the 185 driver available from the Admin menu. Is this actually the 195 driver, just named wrongly?

I can't use the 185 driver as I have a GT240, which afaik is not supported by it :\

any ideas?

---

### Post by GSF1200S on 2010-04-29
> **w0ss4g3 said:**
> I'm having a similar problem today, although the driver will install.. but X seems to crash on boot.

I'm running 9.10 and I just updated to the new kernel 2.6.31-21 (was on -20). Before the update I was running the 195.36.24 drivers which I'd got from the nvidia site. I can reinstall the driver when running the new kernel, but it boots into low graphics mode :(

If I add the repo to my sources, I still only have the 185 driver available from the Admin menu. Is this actually the 195 driver, just named wrongly?

I can't use the 185 driver as I have a GT240, which afaik is not supported by it :\

any ideas?

Did you do:
```
sudo nvidia-xconfig
```
afterwards? You shouldnt need to, but just as a precaution. If the driver installs and Xorg is updated, you should be fine. Can you get the error printout and let us know what it is? Once again, the 195 drivers are available in a ppa- I installed them on 9.10 and had no issues...

---

### Post by cryptotheslow on 2010-04-29
I have a GTS 250 and am using the 190.53 driver from the NVidia site.

As usual the kernel upgrade from -20 to -21 required it to be reinstalled.

It is simple enough - when the system reboots after the kernel upgrade you will most likely get the low graphics warning message up - just take the option to login to a console. Then:

cd to wherever you have stored the driver install file (in my case cd ~/nvidiadriver)

sudo service gdm stop (just to be sure gdm is not running)
sudo sh ./NVIDIA-Linux-x86-190.53-pkg1.run

Just follow the prompts. The installer will recognise that the driver is already installed and remove it before rebuilding its kernel module and reinstalling. I always answer NO to the last prompt which is asking whether you want the installer to modify your xorg.conf - as the driver has already been installed and I know my xorg.conf is just fine as it is there is no point it being 'updated'.

Then just:

sudo service gdm start

et voila - the usual X login screen appears.

So in short GTS250 + kernel 2.6.31-21 + NVidia driver v190.53 is working just fine.

I'll grab a copy of the v195.36.24 driver now and confirm that works OK too.

*edit to add: *Just installed the v195.36.24 driver downloaded from the NVidia site and can confirm GTS250 + kernel 2.6.31-21 + NVidia driver v195.36.24 works just fine.

N.B. If this is the way you choose to install the driver make sure to keep a copy of the installer file somewhere handy as you will need it on every kernel upgrade!

---

### Post by fterh on 2010-04-29
> **GSF1200S said:**
> Alternatively, you can go to System > Administration > Hardware Drivers and just enable the Nvidia driver that way. 

*Note: This next step installs drivers that are not officially in the Ubuntu repositories- you will be installing from a Third-Party repo that has packaged the later versions*

If you have Karmic Koala (9.10), you can update to the 195 series of Nvidia drivers by doing:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```
and
```
sudo apt-get update
```
and then go to System > Administration > Hardware Drivers and enable the 195 driver. I then HIGHLY recommend that you go to System > Administration > Software Sources and DISABLE the above repository so that you dont end up updating other packages you might want left alone. Of course, you may like to live life on the edge ;)
Okay I tried that but I can't find the 195 driver. How do you check your current driver version anyway?

---

### Post by cryptotheslow on 2010-04-29
> **fterh said:**
> Okay I tried that but I can't find the 195 driver. How do you check your current driver version anyway?

System > Preferences > NVIDIA X Server Settings

The driver version in use is displayed there.

---

### Post by fterh on 2010-04-29
Okay this is weird. After going to System>Administrator>Hardware Drivers and activating the "(version current)" driver I realized that it's the 195.36.15 (not the very latest).

So I ran "sudo service gdm stop", ctrl+alt+f2, logged in, "cd /home/fabian/Downloads" and "sudo sh N*". Again after accepting the license agreement I got the message "The distribution-packaged pre-install script failed. Would you like to continue the installation?" (IIRC) I continued installation.

Weird thing is this time it worked. No more installation failed halfway through. After restarting gdm I checked "sudo nvidia-settings" and it's the very latest 195.36.24.

I didn't configure the blacklist. Very weird. Anybody care to explain to a newbie?

---

### Post by cryptotheslow on 2010-04-29
v195.36.24 was only released by NVIDIA yesterday so it is not surprising that it has not made its way into Lucid's Hardware Driver manager.

By the sound of it you downloaded v195.36.24 directly from NVIDIA and manually installed it - hence why you have the newer version installed.

I have seen a lot of comments over the last few weeks that the NVIDIA driver installer from their site did not correctly configure the blacklisting thing on lucid. Maybe the new installer release yesterday now does? I can't verify this as I'm running karmic.

---

### Post by w0ss4g3 on 2010-04-29
Ok, I completely removed all of the Nvidia drivers (both 185 and the 195 I had installed previous) and then rebooted into the new -21 kernel. The installation gave a warning message or two:

Unable to open '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for reading (no such file or directory)

However, I just hit OK when it came up and it installed again. I ran nvidia-xconfig again and restarted X. It now appears to be running correctly (eg, can use the enhanced desktop effects, compiz-fusion etc). So all appears to be ok.

I swear I ran nvidia-xconfig when I updated to the new kernel, but perhaps I didn't!

Anyway, at the moment, I can confirm the 195.36.24 driver worsk fine on the -21 kernel with my GT 240 :)

Thanks for help suggested guys!

---

### Post by fterh on 2010-04-30
> **cryptotheslow said:**
> v195.36.24 was only released by NVIDIA yesterday so it is not surprising that it has not made its way into Lucid's Hardware Driver manager.

By the sound of it you downloaded v195.36.24 directly from NVIDIA and manually installed it - hence why you have the newer version installed.

I have seen a lot of comments over the last few weeks that the NVIDIA driver installer from their site did not correctly configure the blacklisting thing on lucid. Maybe the new installer release yesterday now does? I can't verify this as I'm running karmic.
I don't know, I downloaded the installer but it gave me an error halfway through installation. I then installed from Hardware Drivers, then tried Nvidia again (re-downloaded as I had deleted the installer). Maybe they released the new one **right before** I re-downloaded. But it worked the 2nd time.

---

### Post by fterh on 2010-04-30
Okay I think I understand what's going on. Installed a fresh new copy of 10.04 LTS final, downloaded Nvidia driver 195.36.24, tried to install, failed.

It says something along the lines of "Nvidia module not found".

But if I installed a driver from System>Administration>Hardware Drivers first, it works because the module has been installed.

That's my theory, at least. Need gurus to confirm though :D

Edit: If I had tried to install (unsuccessfully) 195.36.24, then I installed 195.36.15 from Hardware Drivers, then upgraded to 195.36.24 (successfully), will there be "junk files" lying about in my system due to the first unsuccessful installation? I know this isn't Windows and the installer should have deleted any installed files when installation failed, but I just want to be safe.

And if I were to upgrade to the very latest version by downloading & running the installer from nvidia.com how do I uninstall it in the case of system instability? Just curious. Deactivating the driver from Hardware Drivers removed the .15, not the .24.

---

### Post by fterh on 2010-04-30
> **fterh said:**
> Okay I think I understand what's going on. Installed a fresh new copy of 10.04 LTS final, downloaded Nvidia driver 195.36.24, tried to install, failed.

It says something along the lines of "Nvidia module not found".

But if I installed a driver from System>Administration>Hardware Drivers first, it works because the module has been installed.

That's my theory, at least. Need gurus to confirm though :D

Edit: If I had tried to install (unsuccessfully) 195.36.24, then I installed 195.36.15 from Hardware Drivers, then upgraded to 195.36.24 (successfully), will there be "junk files" lying about in my system due to the first unsuccessful installation? I know this isn't Windows and the installer should have deleted any installed files when installation failed, but I just want to be safe.

And if I were to upgrade to the very latest version by downloading & running the installer from nvidia.com how do I uninstall it in the case of system instability? Just curious. Deactivating the driver from Hardware Drivers removed the .15, not the .24.
Bump this message

---

### Post by dino99 on 2010-04-30
sorry i've not read all the story, only last post, so:

- better to install the buil-in lucid nvidia driver instead of downloading from nvidia.

- goto system --> admin --> synaptic
1) be sure the repo are only the official ones (lucid, no exotic repo)
2) update the repo (first left icon into synaptic menu)

and remove/purge all the nvidia packages installed
then install nvidia-current, nvidia-current-modaliases, nvidia-common

- close synaptic and reboot now

---

### Post by fterh on 2010-04-30
> **dino99 said:**
> sorry i've not read all the story, only last post, so:

- better to install the buil-in lucid nvidia driver instead of downloading from nvidia.

- goto system --> admin --> synaptic
1) be sure the repo are only the official ones (lucid, no exotic repo)
2) update the repo (first left icon into synaptic menu)

and remove/purge all the nvidia packages installed
then install nvidia-current, nvidia-current-modaliases, nvidia-common

- close synaptic and reboot now
What do step 1, 2, and the remove/purge do? Do they remove the .24 one I installed from Nvidia?

---

### Post by w0ss4g3 on 2010-04-30
If you want to remove the .24 one from nvidia, just run nvidia-uninstall. I'm not sure if this will touch the repo driver though, so probably best to run nvidia-uninstall first, then install the repo drivers as dino99 described.

I think he means purge all repo-installed sources first, then install the packages he mentioned.

---

