---
title: "Can't Install ATI drivers"
date: 2012-03-06
forum: General Help
---

### Post by Bloodyuki on 2012-03-06
I know this was solved before, but I can't manage to do this.

I've tried uninstalling all fglrx packages, then reinstall them using : sudo dpkg -i fglrx*.deb
Which doesn't work resulting in :

[PHP]
yuki@yuki:~/catalyst12.1$ sudo dpkg -i fglrx*.deb
Selecting previously deselected package fglrx.
(Reading database ... 201029 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.930-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.930-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.930-0ubuntu1_i386.deb) ...
Preparing to replace fglrx-modaliases 2:8.930-0ubuntu1 (using fglrx-modaliases_8.930-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Setting up fglrx (2:8.930-0ubuntu1) ...
update-alternatives: error: alternative link /usr/bin/aticonfig is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.930-0ubuntu1) ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
[/PHP]

Ubuntu 11.10

---

### Post by Gremlinzzz on 2012-03-06
Simply go to System Settings and search for "Additional Drivers."
Now you should see a box that shows that the "ATI/AMD proprietary FGLRX graphics driver" is not activated. Now for the tricky part: hit the activate button, enter your password when prompted, let it do it's thing, then restart your computer!:popcorn:

Option 2: Manually Download/install/Configure the ATI Driver

This method is a bit more tricky and, in my opinion, a little less likely to work. So here are the steps:

    Download your driver from AMD's website: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
    Right click on the downloaded file. Go to Properties and allow it to be executed as a program.
    Now double click the file, let it run in Terminal, and enter you password when and if required.
    Once done, open up another Terminal and enter the following command: sudo aticonfig --initial
    Reboot


Troubleshooting

I see a black screen upon reboot, what do I do!?!

First, reboot into recovery mode, in low graphics mode. Then enter this again into a Terminal: sudo aticonfig --initial. If you see nothing again on the reboot, go back into low graphics mode to uninstall the driver.

How do I uninstall the ATI driver?

This method only works by removing the drivers and not reimplimenting the old one. Here's the tutorial to uninstall, reinstall and configure the default ATI drivers to the way it was.

Once again, reboot into safe mode in low graphics mode and open up a Terminal. Enter this: cd /usr/share/ati

and this: sudo sh ./fglrx-uninstall.sh

---

### Post by QIII on 2012-03-06
An important thing to remember:

After installing the driver and BEFORE you shut down, run the following in the terminal

```
sudo aticonfig --initial
```

I do that when I install it even from the repo.  You MUST do it if you install from the binary.

---

### Post by Bloodyuki on 2012-03-06
Thanks for answering, but both of these doesn't work for me, the additional drivers one just stucks after I press active(it really stucks, doesn't download anything). This worked before, but after trying to manually install, Nothing seems to work now.

As I've stated in my first post, I get these :

when I manually try to install latest drivers ::

[PHP]
Errors were encountered while processing: 
 fglrx 
 fglrx-amdcccle 
 fglrx-dev  
[/PHP]

---

### Post by Gremlinzzz on 2012-03-06
Not sure but this site might be helpful:popcorn:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

### Post by Gremlinzzz on 2012-03-06
NOTE: If you enter your card information on AMD/ATI's driver page, it will offer you the Catalyst 9-3 driver to download. However, the Catalyst 9-3 driver doesn't support X servers past 1.5, and it will not work with Oneiric (or anything later than Lucid/10,04)! !!!SO BE CAREFUL!!! If you tried to install Catalyst on a system with one of these cards, see the 'Removing the Driver' section to restore the default/pre-installed drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

