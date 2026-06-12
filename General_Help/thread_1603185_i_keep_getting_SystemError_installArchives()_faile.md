---
title: "i keep getting SystemError: installArchives() failed on almost every application"
date: 2010-10-22
forum: General Help
---

### Post by Guirgis on 2010-10-22
Hello All,
I know this has been discussed a lot, but my problem is that i get this error on almost every application, not only broadcom drivers, but also virtualbox, skype and many other applications that it made me think that all of this because of a common problem, i always get the the same message:
```
 SystemError: installArchives() failed
```Actually this may force me to return to Lucid release (10.04), So please if you can help in solving that problem, i'd be grateful.
I'm using Ubuntu Maverick Meerkat on a Dell Vostro 1015,

---

### Post by Sef on 2010-10-22
> not only broadcom drivers

I have the same problem, yet all installs fine (except the broadcom drivers.) The problem is the broadcom drivers. The drivers are kept trying to be reinstalled. All works fine, but for that one problem. I put up with it, and hopefully broadcom will fix the problem soon.

---

### Post by sikander3786 on 2010-10-22
Follow this thread.

[http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

What is the output when you try

```
sudo apt-get install skype
```

---

### Post by Guirgis on 2010-10-22
> **sikander3786 said:**
> Follow this thread.

[http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)


Actually , i tried that before i posted this thread, but still the Broadcom B43 wireless driver is disabled, only the STA driver is enabled, see
```
$ jockey-text -l
firmware:b43 - Broadcom B43 wireless driver (Proprietary, Disabled, Not in use)
kmod:wl - Broadcom STA wireless driver (Proprietary, Enabled, In use) [auto-install]

```> 
What is the output when you try, 
```
sudo apt-get install skype
```I reinstalled skype again (i double-clicked a .deb package), now it is running.

And here's the output:
```
skype is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Although skype is running now, virtualbox isn't, even updates fails with the same errors. Any suggestions why this happens with 10.10 and not 10.04? 
Thanks.

---

### Post by Guirgis on 2010-10-30
Looking through the logs of the errors I faced while installing most of the applications, i think all the errors results from the broadcom driver.

---

### Post by sikander3786 on 2010-10-30
If you no longer want to install that broadcom drivers, you can get rid of that error by manually editing some files.

Your apt cache has got corrupted. Time for some clean up. Follow with caution, keep a close eye and your mind on what you are doing and double check before deleting any files/text as advised.

Type
```

gksu nautilus /var/lib/dpkg/info

```

Find firmware-b43-installer, any files relating to it and rename them, delete them or move them to some other location whatever you prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

```

sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak

```

Now edit the file

```

gksu gedit /var/lib/dpkg/status

```

Search for firmware-b43-installer and delete any lines relating to it. There might be more than one so go keep on searching until the end of the file.

Now type

```

sudo apt-get update

```

And tell me that the error message is gone. :-)


[COLOR="Red"]**EDIT:**[/COLOR] **You are doing everything as root, the system might not ask you to double check or even single check if deleting something. Be cautious or you might mess up your system.**

---

### Post by Guirgis on 2010-11-01
> **sikander3786 said:**
> If you no longer want to install that broadcom drivers, you can get rid of that error by manually editing some files.

Your apt cache has got corrupted. Time for some clean up. Follow with caution, keep a close eye and your mind on what you are doing and double check before deleting any files/text as advised.

Type
```

gksu nautilus /var/lib/dpkg/info

```Find firmware-b43-installer, any files relating to it and rename them, delete them or move them to some other location whatever you prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

```

sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak

```Now edit the file

```

gksu gedit /var/lib/dpkg/status

```Search for firmware-b43-installer and delete any lines relating to it. There might be more than one so go keep on searching until the end of the file.

Now type

```

sudo apt-get update

```And tell me that the error message is gone. :-)


[COLOR=Red]**EDIT:**[/COLOR] **You are doing everything as root, the system might not ask you to double check or even single check if deleting something. Be cautious or you might mess up your system.**

Thanks
I followed your procedure and i got rid of this error. however as i have another problem with the video on my Dell Vostro 1015 - i think the Lucid release might be better for me, thinking about reverting ..

Thank you again for these valuable instructions, i feel happy when i know how ubuntu works :)

---

