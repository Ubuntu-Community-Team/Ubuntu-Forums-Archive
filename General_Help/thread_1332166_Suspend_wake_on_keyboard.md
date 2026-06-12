---
title: "Suspend wake on keyboard"
date: 2009-11-20
forum: General Help
---

### Post by Gorlist on 2009-11-20
Though ive been using Ubuntu for a few years I tend to forget details on setting up the system, so anything useful that im bound to forget ive been posting here :) Most of the suggestions below come from other threads, so when I remeber ive added credit or a link back to the original topic. Some of this also covers my Ubuntu 8.04LTS dedicated remote server.  

**[COLOR="RoyalBlue"]Disable login screen coming out of suspend:[/COLOR]**

Terminal:

```
gconf-editor
```

Go to "/apps/gnome-power-manager/lock", and disable the suspend checkbox.


**[COLOR="RoyalBlue"]USB Keyboard wake from suspend:[/COLOR]**

([http://ubuntuforums.org/showthread.php?t=711747&page=2](http://ubuntuforums.org/showthread.php?t=711747&page=2))

Type into the terminal to list the devices:

```
cat /proc/acpi/wakeup
```

You will probably find your USBX is disabled, to enable it create a file in /etc/init.d by going:

```
sudo nano /etc/init.d/wake.sh
```

Then add the following to the new file (making sure you update the USB number):

```
sudo -s
echo USB4 > /proc/acpi/wakeup
```

CHMOD the file to excute:

```
sudo chmod +x /etc/init.d/wake.sh
```

Lastly tell Ubuntu to excute on boot:

```
sudo update-rc.d wake.sh defaults
```


**[COLOR="RoyalBlue"]Disable 60 second shutdown/reboot/logout warning:[/COLOR]**


Terminal:

```
gconf-editor
```

Go to, and enable "/apps/indicator-session/suppress_logout_restart_shutdown".


**[COLOR="RoyalBlue"]Monitor log files:[/COLOR]**

```
tail --help
```

example (displays last 10 lines):

```
tail -f /var/log/auth.log
```


**[COLOR="RoyalBlue"]Add user:[/COLOR]**

```
useradd
```
Will create a new user without a password or associated home directory. 


```
adduser
```
Recommended, will allow you create a password straight away, setup a home directory and enter some user details should you wish to.


**[COLOR="RoyalBlue"]Change file or directory owner and permissions:[/COLOR]**

```
chmod --help
```

Example (group:user, normally the group is the same as the user):

```
chmod usergroup:newuser file.sh
```
```
chmod 777 file.sh
```

**[COLOR="RoyalBlue"]RAID array still being listed during install[/COLOR]**

If you've recently disabled your RAID array you will need to reformat the drives before attemptting to install. Gpart fails to list the drives correctly. The below command gives mixed results.

```
sudo dmraid -r -E
```

Best solution ive found is to reformat the drives before running the Live CD.

**[COLOR="RoyalBlue"]Delay the startup of programs:[/COLOR]**

In your "Startup Applications" GUI you can define programs to load on boot, sometimes you may want to delay or stagger the launch of the apps to help system load. 

Todo this on your command add the following:

```
sh -c "sleep 10 && skype &"
```
```
sh -c "sleep 20 && empathy &"
```

**[COLOR="RoyalBlue"]Rabbitvcs:[/COLOR]**

An easy to use SVN client similar to Tortoise integrated into Nautilus.

[http://rabbitvcs.org]("http://rabbitvcs.org")


**[COLOR="RoyalBlue"]Wacom Graphics tablets:[/COLOR]**

Easy to use driver install script:

[http://ubuntuforums.org/showthread.php?t=1327867]("http://ubuntuforums.org/showthread.php?t=1327867")

After installing the drivers, then download "wacom-tools" through the package manager, open a terminal and run:

```
wacomcpl
```

**[COLOR="RoyalBlue"]Force install a deb package:[/COLOR]**

```
sudo dpkg --force-overwrite -i <filename>
```


**[COLOR="RoyalBlue"]SSH connection using the terminal:[/COLOR]**

Man SSH.

```
ssh -l username -p port 192.168.0.1
```

---

### Post by creatxr on 2009-12-01
> **Gorlist said:**
> USB Keyboard wake from suspend: it seems that it doesn't work after reboot system i "cat" again, i found that it has been reset. (i 'm sorry , i tried it on suse)

---

### Post by Gorlist on 2009-12-30
updated

---

### Post by Melk79 on 2010-05-04
Thanks for posting this summary. I don't like having to write a script for waking my pc with a keyboard, but am glad you posted this to help me find the steps again.  Is there a way to wake on keyboard more easily with Lucid yet?  Seems like most people would want this-- desktop or laptop.

---

### Post by Gorlist on 2010-05-09
ive not had a chance to look into it yet, but I had noticed it stopped working. On holiday at the moment so won't until I get back. Regards,

---

### Post by flmommens on 2012-11-05
my /proc/acpi/wakeup does not contain any USB entry.
cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
UAR1      S4    *disabled  pnp:00:09
P0P1      S4    *disabled  
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  
RP02      S4    *disabled  
PXSX      S4    *disabled  
RP03      S4    *disabled  
PXSX      S4    *disabled  
RP04      S4    *disabled  
PXSX      S4    *disabled  
RP06      S4    *disabled  pci:0000:00:1c.5
PXSX      S4    *disabled  
BR10      S4    *disabled  pci:0000:04:00.0
RP07      S4    *disabled  
PXSX      S4    *disabled  
RP08      S4    *disabled  
PXSX      S4    *disabled  
PEG0      S4    *disabled  pci:0000:00:01.0
PEGP      S4    *disabled  
PEG1      S4    *disabled  
PEG2      S4    *disabled  
PEG3      S4    *disabled  
RP05      S4    *disabled  pci:0000:00:1c.4
PXSX      S4    *enabled   pci:0000:03:00.0
GLAN      S4    *disabled  
EHC1      S4    *enabled   pci:0000:00:1d.0
EHC2      S4    *enabled   pci:0000:00:1a.0
XHC      S4    *enabled   pci:0000:00:14.0
HDEF      S4    *disabled  pci:0000:00:1b.0
PWRB      S4    *enabled   

Any idea what I'm supposed to do to achieve wakup from usb keyboard?

---

### Post by wildmanne39 on 2012-11-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

