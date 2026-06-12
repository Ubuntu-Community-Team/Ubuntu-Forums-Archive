---
title: "Unity, Foobillard &amp; Google Earth problems"
date: 2011-08-23
forum: General Help
---

### Post by voodoompempe on 2011-08-23
Hi all,

Yesterday I installed Ubuntu 11.04 32bit. This is my first time experimenting with Linux, so please bare with me, my knowledge is almost non existent. 

I have 3 problems, possibly unrelated, not sure. When I installed ubuntu, got the option of installing nvidia accelerated graphics driver (current version) which I did, and then got the unity interface. Today when I logged in I had lost it. Switching to nvidia accelerated graphics driver (version 173), gives a black screen after restart, at the point of loading ubuntu. Switching back to current version, through recovery mode, doesn't give me unity. Any ideas?

In addition, amongst others, installed foobillard, from software center, and google earth, as per this tutorial: [http://www.liberiangeek.net/2011/03/install-google-earth-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/install-google-earth-ubuntu-11-04-natty-narwhal/). Both though fail to launch, nothing happens when I click on them. Coud it be down to nvidia drivers malfunctioning?

Any help appreciated, I'm at a loss and the info I'm finding doesn't seem to be working. If you do have an idea, please explain even what u probably consider obvious, as I'm finding it hard understanding the advice given to others with similar problems. 

Many thanks!

---

### Post by sikander3786 on 2011-08-23
Hi. Welcome to Ubuntu and also the forums :)

Seems like all of your problems are related to your graphics card. If we get it working properly and able to run Unity (as it only runs when the proper drivers are installed and working), your other problems would be solved too.

So, please get to a Terminal from Applications > Accessories sub-menu and run these commands and post the outputs:

```
lshw -c video
```

```
/usr/lib/nux/unity_support_test -p
```

While posting, you can click the # icon in post menu and paste the text in between the generated [code] tags for better readability.

---

### Post by voodoompempe on 2011-08-23
wow, this was an extremely fast reply! thanks sikander3786 :P

ok, here is what I get:

```
voodoomaster@VoodooChild:~$ lshw -c video
WARNING: you should run this program as super-user.
PCI (sysfs)  



  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:b6000000-b6ffffff memory:d0000000-dfffffff memory:b4000000-b5ffffff ioport:2000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

I tried becoming a super user but I'm not getting this option under users and groups

```
voodoomaster@VoodooChild:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```

---

### Post by gandaran on 2011-08-23
for installing google-earth it's easier just to download the ubuntu .deb from google and click the package to install
[http://www.google.com/intl/en-us/earth/index.html](http://www.google.com/intl/en-us/earth/index.html)
try this package but remove the one built for your PC, also google-earth should run with any video card driver even with 2D drivers so I don't think the problem is related to video card.

---

### Post by gandaran on 2011-08-23
> **voodoompempe said:**
> wow, this was an extremely fast reply! thanks sikander3786 :P

ok, here is what I get:

```
voodoomaster@VoodooChild:~$ lshw -c video
WARNING: you should run this program as super-user.
PCI (sysfs)  



  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:b6000000-b6ffffff memory:d0000000-dfffffff memory:b4000000-b5ffffff ioport:2000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

I tried becoming a super user but I'm not getting this option under users and groups

```
voodoomaster@VoodooChild:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```
run the commands with 'sudo'
```
sudo lshw -c video
```

---

### Post by voodoompempe on 2011-08-23
Ah ok, this seems to have changed something. Cheers gandaran btw for the gearth tip, will try it once I've sorted out the graphics stuff

```
voodoomaster@VoodooChild:~$ sudo lshw -c video
[sudo] password for voodoomaster: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:b6000000-b6ffffff memory:d0000000-dfffffff memory:b4000000-b5ffffff ioport:2000(size=128)
voodoomaster@VoodooChild:~$ sudo /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```

---

### Post by sikander3786 on 2011-08-23
I suspect this as a problem:

> configuration: latency=0

Normally, it should list a driver there e.g, "driver=nvidia" or "driver=nouveau". And that's why you were even unable to run the Unity Support Test successfully.

So now from a Terminal, please post the output of these commands as well:

```
cat /etc/X11/xorg.conf
```

Note the capital 'X' for 'X11'.

```
dpkg -l | grep nvidia
```

In the meantime, you can try these steps for repairing your graphics. These shouldn't do any harm to your PC.

1. Go to System > Administration > Additional Drivers and remove any installed drivers.
2. Backup your existing xorg.conf by running:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

3. Reconfigure your graphics by running:

```
sudo dpkg-reconfigure xserver-xorg
```

4. Reboot.

5. From System > Administration > Additional Drivers, activate the current/recommended version of drivers.

6. Reboot. If that doesn't help, remove the current version of drivers and try installing an older version.

If you tried these steps and they didn't solve the problem, please run the above mentioned commands again and post the most recent results i.e. after trying the steps above.

---

### Post by voodoompempe on 2011-08-24
Good day. I tried the steps mentioned without much luck. When running the commands to backup and then reconfigure I got  the following:

```
                 
 voodoomaster@VoodooChild:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old  
 [sudo] password for voodoomaster:  
 voodoomaster@VoodooChild:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old  
 mv: cannot stat `/etc/X11/xorg.conf': No such file or directory  
 voodoomaster@VoodooChild:~$ sudo dpkg-reconfigure xserver-xorg
 voodoomaster@VoodooChild:~$
 
```Installing the current/recommended driver again didn't do anything, and I don't get any previous drivers listed under additional drivers, just an experimental one, which I'm guessing is not what you meant. Running the additional tests I get:

```
voodoomaster@VoodooChild:~$ sudo cat /etc/X11/xorg.conf
[sudo] password for voodoomaster: 

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

voodoomaster@VoodooChild:~$ sudo dpkg -l | grep nvidia
ii  nvidia-173                            173.14.30-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver
voodoomaster@VoodooChild:~$ 

```Sorry to be a pain, any further ideas?

---

### Post by sikander3786 on 2011-08-24
Thanks for the outputs.

Again from a Terminal, run this command:

```
sudo apt-get purge nvidia-173 nvidia-common nvidia-current nvidia-settings && sudo rm /etc/X11/xorg.conf
```

Reboot.

Now from Additional Drivers, activate the 'nvidia-173' drivers yet again and reboot. Ok if it is fixed otherwise remove the current driver and activate 'current' one this time.

Don't forget to remove your older drivers and reboot prior to trying to install another version of drivers.

For some older graphics cards, older versions of Nvidia drivers work better and are capable of running Unity in 11.04 than the newer current versions.

Good Luck!

---

### Post by voodoompempe on 2011-08-24
From zenith to nadir.

Cheers again sikander3786. Followed your advice and although with nvidia_173 I got the black screen at start up, I logged in through recov mode, uninstalled, install nvidia_current, and unity worked perfectly! For a bit at least. Checked that foobillard was working, and installed google earth as per the advice above. All worked fine. Then I restarted and when I logged back in, got the classic look and both software were again not working. Thought I'll try switching drivers again just in case it solved it, uninstalled current, installed 173 and now the machine freezes on start up no matter what version I select. (normal, recovery, previous or previous recovery)

Probably should have mentioned it before, I've got a winXP OS running alongside. Could that be causing the conflict? And one more, probably irrelevant, thought. I see in my first code earlier a line that says width: 64bits. Could I be running a 32bit version on a 64bit machine?

---

### Post by sikander3786 on 2011-08-24
So there is a problem with Google Earth that whenever you install it, it breaks your graphics.

Remove Google Earth.

Remove and re-install graphics drivers and when you get everything working, try installing Google Earth by following a bit different method:

[http://www.tuxgarage.com/2011/06/easy-installation-of-popular-apps-that.html](http://www.tuxgarage.com/2011/06/easy-installation-of-popular-apps-that.html)

Lets hope it doesn't get messed up this time.

---

### Post by voodoompempe on 2011-08-24
Nice one. Will do. But any idea how I can get in to the linux OS as all methods (normal, recovery, previous or previous recovery) freeze on the purple login screen (using XP now)? I got the option of opening up the limited grub command box in the beginning. Any way of removing the nvidia driver from there?

---

### Post by sikander3786 on 2011-08-24
> **voodoompempe said:**
> Nice one. Will do. But any idea how I can get in to the linux OS as all methods (normal, recovery, previous or previous recovery) freeze on the purple login screen (using XP now)? I got the option of opening up the limited grub command box in the beginning. Any way of removing the nvidia driver from there?
Press and hold down <Shift> key from Bios screen until you see the Grub menu.

Highlighting the normal boot entry there, press 'e' to edit it. Navigate to words 'quiet splash', delete them and type 'nomodeset' (without quotes) in their place. Press Ctrl + X to continue boot. Can you see the desktop? If yes just remove the drivers and reboot.

The changes you make to your Grub entry are just temporary and automatically revert to the original one's on a reboot.

You don't need to edit the Grub entry when you successfully reboot after removing the drivers.

---

### Post by voodoompempe on 2011-08-25
Hi again! 

Ok, managed to log in to ubuntu, and as suggested removed google earth and de-activated 173. Rebooted. Activated current driver, rebooted and nothing. So re-entered the code: 
```
sudo apt-get purge nvidia-173 nvidia-common nvidia-current nvidia-settings && sudo rm /etc/X11/xorg.conf 
```

Rebooted, activated the current driver, rebooted again and it worked. Then i rebooted straight away, before doing anything. And I was back to classic mode. It doesn't seem to be related to google earth after all, something happens when restarting the pc. Checked the additional drivers section and Nvidia current, although activated, says at the bottom: This driver is activated but not currently in use. I can see a lot of people are having the same problems but there are a lot of different suggestions on google. Any ideas what has worked so I don't mess things up further?

---

### Post by sikander3786 on 2011-08-25
This is just a false reporting in Natty as far as I know.

> This driver is activated but not currently in use

In the previous cases I've seen, the driver continues to work even if the jockey states the above quoted message.

Looking at your logs might help. Please attach the 'Xorg.0.log' and 'boot.log' files from /var/log directory.

---

### Post by voodoompempe on 2011-08-26
Thanks once again for getting back to me. 

I couldn't see how to attach those files, so I've attached an office doc with the logs inside them. Hope that helps.

---

### Post by sikander3786 on 2011-08-28
Sorry, I couldn't get back to you on this, earlier.

I've looked at your attached logs but wasn't able to find anything concerning there.

I've requested another experienced member to look at your problems, please hang in there.

---

