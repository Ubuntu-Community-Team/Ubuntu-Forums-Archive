---
title: "nvidia issue"
date: 2009-12-18
forum: General Help
---

### Post by Gosujii-sama on 2009-12-18
While mucking around trying to fix a bug came up with another problem. any help is welcomed. This happens when attempting to run wine with war3. (war3 unable to start)

NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
construct@Diabolic:~$ X Error of failed request:  GLXBadContext
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  6920

---

### Post by yavoh on 2009-12-18
You can always download fresh (non-free) drivers from nvidia.com.  Make sure you select the version for your flavor of Ubuntu.

After you download, remember the path to the download.  Type "stop gdm" in the terminal.  This will kill your X session, putting you back at the command line.

Log in and navigate to the directory where you saved the NVIDIA**.run  file.  Then, type "sudo sh ./NVIDIA***.run" where "NVIDIA***.run" is the full file name (it varies).

That will allow you to reinstall your NVIDIA drivers.  Hopefully that will solve your problems.  If not, it may be a compatibility problem with Wine.

---

### Post by Gosujii-sama on 2009-12-18
Well I reinstalled the driver using the method you stated and this issue seems to still be there. Trying to boot up morrowind TES: III I get the same error about
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
this seems to be root authorized for some reason and not letting me use from current user.
I cant chmod it or anything either being a device file.

---

### Post by yavoh on 2009-12-18
[This thread]("http://ubuntuforums.org/showthread.php?t=1031127") suggests running
```
sudo nvidia-xconfig
```and then rebooting after installing new drivers, then trying again.

[This Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/288852") suggests (at the very bottom) an addition to the xorg.conf file (/etc/X11/xorg.conf).

Hopefully one of these will help!  I'm not familiar with the issue, nor have I had permissions problems with my Nvidia-wine setup, but it looks like many other people have.

---

