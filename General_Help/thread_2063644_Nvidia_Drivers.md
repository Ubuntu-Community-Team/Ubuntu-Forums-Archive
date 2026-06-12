---
title: "Nvidia Drivers??"
date: 2012-09-27
forum: General Help
---

### Post by Eirreann on 2012-09-27
So I just installed Ubuntu 12.04 on my gaming Desktop (because my laptop has been giving me grief...)  Installation went incredibly well and I'm using it now, HOWEVER, I don't have any video drivers!  I'm using an Nvidia GTX 670.

---

### Post by Cavsfan on 2012-09-27
> **Eirreann said:**
> So I just installed Ubuntu 12.04 on my gaming Desktop (because my laptop has been giving me grief...)  Installation went incredibly well and I'm using it now, HOWEVER, I don't have any video drivers!  I'm using an Nvidia GTX 670.

You should be able to install nvidia-current-updates.
**sudo apt-get install nvidia-current-updates **
That should also pull in the other necessary programs.
I have a geforce 9800 GT and that works fine for me. 
It is version 295.49.

I have not been able to install anything later than that.

---

### Post by Eirreann on 2012-09-27
> **Cavsfan said:**
> You should be able to install nvidia-current-updates.
**sudo apt-get install nvidia-current-updates **
That should also pull in the other necessary programs.
I have a geforce 9800 GT and that works fine for me. 
It is version 295.49.

I have not been able to install anything later than that.

Thanks!  That worked brilliantly!!!

---

### Post by Cavsfan on 2012-09-27
> **Eirreann said:**
> Thanks!  That worked brilliantly!!!

You are welcome! Glad I could help.
You may want to check out this thread too:
[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1968155_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1968155")

---

### Post by GeForce 9500GT on 2012-09-27
If you want the latest Nvidia driver (which is  									 										304.51) you can do this in a terminal:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```
```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by Cavsfan on 2012-09-27
> **GeForce 9500GT said:**
> If you want the latest Nvidia driver (which is                                                                               304.51) you can do this in a terminal:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
``````
sudo apt-get update
``````
sudo apt-get install nvidia-current nvidia-settings
```

I did this with my 12.04 install and it left it unbootable. I had to do a clean install.
That xswat ppa doesn't work for everyone.

Use at your own risk.

---

### Post by Eirreann on 2012-09-27
> **Cavsfan said:**
> I did this with my 12.04 install and it left it unbootable. I had to do a clean install.
That xswat ppa doesn't work for everyone.

Use at your own risk.
Yeah, I actually tried that before making this thread; found it in a Google search.  Nothing went wrong... but nothing happened, so yeah, haha!

---

### Post by GeForce 9500GT on 2012-09-28
*>  I did this with my 12.04 install and it left it unbootable. I had to do a clean install.That xswat ppa doesn't work for everyone.Use at your own risk.*
* *
> *Yeah, I actually tried that before making this thread; found it in a Google search. Nothing went wrong... but nothing happened, so yeah, haha!*
 
I never had any issues with that x-swat PPA. It always worked for me and that PPA is commonly recommended on every forum for Debian-based distro's. I think the problem is not the PPA but your own system/hardware.

---

### Post by Cavsfan on 2012-09-28
> **GeForce 9500GT said:**
> I never had any issues with that x-swat PPA. It always worked for me and that PPA is commonly recommended on every forum for Debian-based distro's. I think the problem is not the PPA but your own system/hardware.

There are others that have had the same problem with the xswat ppa.
I have Ubuntu Lucid Lynx, Precise Pangolin, Quantal Quetzal and Windows 7 installed.
Lucid has the **304.51** driver installed and it works great. Precise has the **295.49** driver installed from nvidia-current-updates. 
As I already stated I tried the xswat ppa once and it bombed my system. I also tried installing the latest driver manually in Precise but, since it boots into a read only recovery, I could not do it.
Quantal has the **304.43** driver I believe which came from nvidia-current.
Windows 7 has the **306.23** driver installed with directx 10 and it works very well.
So, one should not assume it is a system/hardware problem just because the xswat ppa does not work for me.
It works for some and not for others. I have been there and done that and that is why I am saying to use the xswat ppa at your own risk.

---

### Post by brianhaz on 2012-09-30
Hi!  I'm having issues with my graphics drivers similar to the ones the original poster was having, but they are not resolved by the fix.  My video card is an nvidia GTX 570HD.  When I try to install the nvidia proprietary drivers, I get this message:

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

Here's my jockey log:

[INDENT]2012-09-30 10:30:58,913 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7197a0c>
2012-09-30 10:30:59,924 DEBUG: reading modalias file /lib/modules/3.2.0-31-generic-pae/modules.alias
2012-09-30 10:31:00,048 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-30 10:31:00,055 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-30 10:31:00,092 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-30 10:31:00,126 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-30 10:31:00,128 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-30 10:31:00,129 DEBUG: nvidia.available: falling back to default
2012-09-30 10:31:00,220 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-09-30 10:31:00,220 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-30 10:31:00,223 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-30 10:31:00,226 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-30 10:31:00,227 DEBUG: nvidia.available: falling back to default
2012-09-30 10:31:00,260 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-09-30 10:31:00,263 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-30 10:31:00,267 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-30 10:31:00,268 DEBUG: nvidia.available: falling back to default
2012-09-30 10:31:00,300 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-30 10:31:00,304 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-30 10:31:00,308 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-30 10:31:00,308 DEBUG: nvidia.available: falling back to default
2012-09-30 10:31:00,341 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-30 10:31:00,345 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173[/INDENT]

and so on and so forth for a long time, because I tried many times in different ways.

I only got unity with visual effects working once, when I manually installed the 304.51 drivers in recovery mode, but that was not satisfactory because MyUnity was bugged in that state and wouldn't launch, I don't think gnome 3 was working, and also because the system kept reporting that there were newer nvidia drivers that needed to be enabled.

Can you guys help me parse that jockey log?  Ideas, please?  Thanks for the help!

---

### Post by Cavsfan on 2012-10-01
What I would try is to purge your existing nvidia files and try to re-install:
Enter in terminal **sudo apt-get purge nvidia*** and hopefully that doesn't rip out too much stuff.

Whatever else it takes out besides files starting with nvidia make note of and just re-install them after installing the nvidia drivers.
Once you have removed all of the old nvidia files. **DO not** reboot.
In terminal enter this:

**sudo apt-get install nvidia-current-updates **

Then re-install any other files (if any) the purge took out like this:
**sudo apt-get install <filename(s)>**

Then you should be able to reboot and be good to go.
This method should install nvidia driver version 295.49 which seems to work pretty well.

Once you reboot, enter this in terminal: **apt-cache policy nvidia-current-updates**
It will show you the version.

---

