---
title: "Compiz crashes / No Unity bar &amp; Launcher upon reboot"
date: 2012-05-29
forum: General Help
---

### Post by Eromatic on 2012-05-29
*(At the moment, I consider the issue fixed, but I am uncertain if the issue really is with the configuration done with CompizConfig Settings Manager. I would need to do multiple reboots and monitor configuration changes through Nvidia X Server Settings to know for sure. It is also of hope that if someone runs into this similar issue, that maybe this post could be of help to them.)*

__________


Some time recently I have observed on my computer that upon reboot, the Unity Launcher and top bar would appear and then quickly disappear, leaving nothing but the desktop icons and app windows with no decorations. 

At first I had though that this issue was due to a recent ppa update of the [nvidia-graphics-driver](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=precise) from &#8220;Ubuntu-X&#8221; team. At that point after the compiz problems had begun, I had decided to rollback to the nvidia-current driver & nvidia-settings to the version provided by the Ubuntu repositories (295.40-0ubuntu1). (x-swat ppa had already been removed from software sources before reboot.)

I had done this by doing the steps seen over at [askubuntu](http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers):

> To get my machine able to boot into Ubuntu I had to go to the Recovery Console, Make it Read/Write and remove the NVIDIA drivers. You might have to hold Shift down while booting to get the GRUB option for Recovery Console. I used the following commands after Dropping to a Root Shell Prompt from the Recovery Console:

```
mount -n -o remount,rw /
apt-get purge nvidia-current
rm /etc/X11/xorg.conf
reboot now
```


Using for above the sudo command of course, and doing a "sudo apt-get purge nvidia-settings" as well to remove the nvidia x server settings control panel.

Upon reboot and getting to my desktop, access to the Unity bar and launcher would be available again, but there of course would be no proprietary nvidia driver in use as I removed it from the previous steps. I would then install through Synaptic Package Manager, nvidia-current and nvidia settings. Upon reboot of a successful installation,
the proprietary nvidia driver would load and compiz and the Unity bar & launcher would also function normally.

It is only after a few reboots that the Unity bar & launcher would disappear upon access to the desktop. This would happen with or without a xorg.conf file present.

Being that sometimes upon the failed reboot, apport (send this bug report the developers) would note that compiz had crashed. Of course without compiz, you can't really run Unity. At a later point I had begun to suspect that maybe it was some configuration that I had done under CompizConfig Settings Manager. 

I would then proceede to backup & delete the folders within the Home directory that are related to compiz. Accessing Nautilus was easy as I still had access to creating new folders on the desktop.

(Control-h to show hidden files within a Nautilus window.)

Relocated and removed the following files & folders: 

```
/home/user/.compiz-1
/home/user/.config/.compiz-1
/home/user/.gconf/apps/compizconfig-1
/home/user/.gconf/apps/compiz-1
```

And also relocated and remove the folder & file:

```
/home/user/.nv
/home/user/.nvidia-settings-rc
```

Upon reboot and with a previously generated xorg.conf file kept in place by "Nvidia X Server Settings" (version 295.33), the Unity bar & Launcher would return and function normally. 

I later launched the Nvidia X Server Settings and applied and needed changes there (Such as v-sync for gl), then I had rebooted a few times to see if an issue was being cause by there. No issues were present upon reboot.

Later I had launched CompizConfig Settings Manager and had altered three settings, all within composite:

```
Detect Refresh Rate - Set to disabled
Refresh Rate - Set to 60
Unredirect Fullscreen Windows - Set to Enabled
```

After a reboot there after, upon enter to the desktop, the Unity bar & Launcher would be gone, with only the desktop icon seen present.

I suspect that as the "Unredirect Fullscreen Windows - Set to Enabled" setting was a recent change (Within the week), that this may be the setting that is damaging things here with Unity.

When I repeat the deletion of:

```
/home/user/.compiz-1
/home/user/.config/.compiz-1
/home/user/.gconf/apps/compizconfig-1
/home/user/.gconf/apps/compiz-1
```

And deletion of ```
/home/user/.nv
```
(Keeping /home/user/.nvidia-settings-rc in place)

...The Unity bar & Launcher would return and function normally upon reboot. 

(To reboot with a broken Unity, I do Control-Alt-F1, login with my user account, then do a "sudo reboot" to reboot the computer.)

The only thing I would still need to test is if just launching CompizConfig Settings Manager would result in the seen issues with Unity. (And to do a dozen reboots over time to be certain the the issue had been corrected.)

Usually when Compiz & Unity goes down, it will never come back upon after multiple reboots on its own. Deleting the noted Home files & folders or purging the nvidia-current & nvidia-settings would only bring back the Unity bar & Launcher. 


**(TL;DR)**

-Purging just the nvidia-current & nvidia-settings does not fix the issue as it does reappear later after a few reboots. 

-Deleting the noted Home files & folders does appear to correct the issue, as the problem had not returned after multiple reboots.

-The issue was more common on a multi-monitor configuration with Twinview, but was still present even with one monitor only and no xorg.conf file.

-At this point, I hope that there isn't anything else that I may be missing that may have caused this issue.

-All that stuff that I had read on other sites about probably doing a "unity --replace and unity --reset" didn't seem to work at all.

-Unknown if it really was CompizConfig Settings Manager alterations that mucked things up with Unity, but is probable.


Some info on this system:

AMD X2 BE2400
3GB System Memory
250GB sataII hard drive
Ubuntu 12.04 32bit with all updates
Multi-monitor configuration
Nvidia 9500GT

---

### Post by wojox on 2012-05-30
[IMG]http://ubuntuforums.org/picture.php?albumid=2470&pictureid=8416[/IMG]

Guess that's why they added that warning to it.

---

### Post by Eromatic on 2012-05-30
> **wojox said:**
> [IMG]http://ubuntuforums.org/picture.php?albumid=2470&pictureid=8416[/IMG]

Guess that's why they added that warning to it.

Lol, true! :P

---

### Post by wojox on 2012-05-30
> **Eromatic said:**
> Lol, true! :P

I've done the same thing trying to get wobbly windows. :p

---

### Post by wilee-nilee on 2012-05-30
Compiz is a beast, but you can set yourself up with a button to restart it so you don't have to logout or reboot.
```
sudo apt-get install --no-install-recommends gnome-panel
``````
gnome-desktop-item-edit ~/Desktop/ --create-new
```I put this in another file Documents and dragged it to the cairo dock using the fusion icon as the restart tool.

You can also run this command with a terminal or a alt-f2 
```
compiz --replace
```You can reset unity is you need to this should reset compiz as well. again alt f2  
```
unity --reset
```

I have a killer compiz saved file you can just load if you want has the cube and other cool stuff, just post if you want it.

---

### Post by wojox on 2012-05-30
> **wilee-nilee said:**
> 
I have a killer compiz saved file you can just load if you want has the cube and other cool stuff, just post if you want it.

I'm game. I'll try it out. :P

---

### Post by wilee-nilee on 2012-05-30
I have all the extra compiz stuff installed as well, just save it in a text file name as you want and load it from the preferences.

[http://paste.ubuntu.com/1015694/](http://paste.ubuntu.com/1015694/)

I'm kind of surprised people don't trade these like conkies, a bit more of a hassle I guess, conkies are a bit kinder.

---

### Post by wojox on 2012-05-31
I can spin the cube with my mouse wheel, sweet thanks. :popcorn:

---

