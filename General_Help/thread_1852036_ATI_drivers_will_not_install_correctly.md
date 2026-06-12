---
title: "ATI drivers will not install correctly"
date: 2011-09-29
forum: General Help
---

### Post by girlrepellent on 2011-09-29
Hello.

I am trying to install the ATI catalyst driver 8.881 on my linux system, but I am getting an error. The first thing is when I try to install it, it says, "DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for detail" The fglrx-install.log file says,

> Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Installation with force option.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Errors during DKMS module removal
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0

Creating symlink /var/lib/dkms/fglrx/8.881/source ->
                 /usr/src/fglrx-8.881

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you
 could install the linux-headers-2.6.39.4 package.
[Error] Kernel Module : Failed to build fglrx-8.881 with DKMS
[Error] Kernel Module : Removing fglrx-8.881 from DKMS

------------------------------
Deleting module version: 8.881
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfsany ideas what to do about the DKMS and fglrx? I am running a 64bit boot of unbuntu.

---

### Post by girlrepellent on 2011-09-29
root@bt:~/Desktop# apt-get install linux-headers-2.6.39.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.39.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

is what I get when I try to update the linux headers

---

### Post by girlrepellent on 2011-09-29
Additionally, the video card that I have is an ATI radeon HD 4200. I have preformed all updates that I can think of, both for video and not, to the system. The kernel version is 2.6.39.4.

---

### Post by Claus7 on 2011-09-29
Hello,

this is supposed to be a quick one:

since you are doing a forced installation, some things might not work properly. Have you tried, before the installation of the new driver, to remove completely the old one? Do it manually and don't allow the new one to take charge. Then boot in command line mode and try to install the new driver. Reboot once again, and see what you will get.

Regards!

---

### Post by girlrepellent on 2011-09-29
I used the apt-get to purge the directory and tried to install it from the command line before the gui interface came up with the same result. It tells me the same thing about DKMS and fglrx. I have gone through a bunch forums, but they are tailored to an older version of the catalyst with hot fixes that ATI has put out.

---

### Post by girlrepellent on 2011-09-30
Bump

---

### Post by girlrepellent on 2011-10-01
Bump again

---

### Post by sumski on 2011-10-01
What about
```
sudo apt-get install linux-headers-2.6-$(uname -r|sed 's,[^-]*-[^-]*-,,')
```

---

### Post by girlrepellent on 2011-10-01
> **sumski said:**
> What about
```
sudo apt-get install linux-headers-2.6-$(uname -r|sed 's,[^-]*-[^-]*-,,')
```


~# sudo apt-get install linux-headers-2.6-$(uname -r|sed 's,[^-]*-[^-]*-,,')
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6-2.6.39.4

I also tried installing the newer version of the ati drivers that came out on the 28SEP the 11.9 and still getting the same error.

---

### Post by StevenWR on 2011-10-01
sudo aticonfig --uninstall 

is the proper way to remove the proprietary previous version of the ati/amd driver after that reboot
Im currently running Kubuntu/Natty 32bit the 11.9 packages built sucessfull for me after installing dependencies with 

sudo apt-get -y install debhelper dh-modaliases execstack 

just found your thread to try and get the packeages posted or at least get the word out that proprietary 11.9 package Ubuntu/Natty will build without errors. I havent tried the install just yet

---

### Post by Dangertux on 2011-10-01
If this is for BT5 which it looks like you might want to try this method, it worked for me.

Download the following ATI Proprietary Driver :  [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

*I would recommend 11.8 , 11.9 is new however when I installed it under BT5 R1 it caused issues with Firefox. 11.8 works just fine.

Step 2 : Uninstall other ATI drivers if they are there

```

cd /usr/share/ati
./fglrx-uninstall.sh

```

After it's done it will tell you to reboot. Then do the following

```

sh ati-driver-installer-11-8-x86.x86_64.run

```

After a few seconds the installer should pop up, instead of choosing create distro specific installation package choose install on Xorg 6.9 or greater. It will go through it's install process and tell you to reboot.

After reboot your new drivers should be working properly, verify with lsmod etc etc.

if you need an xorg.conf run ati-config --initial

Hope that helps.

---

### Post by girlrepellent on 2011-10-01
> **Dangertux said:**
> If this is for BT5 which it looks like you might want to try this method, it worked for me.

Download the following ATI Proprietary Driver :  [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

*I would recommend 11.8 , 11.9 is new however when I installed it under BT5 R1 it caused issues with Firefox. 11.8 works just fine.

Step 2 : Uninstall other ATI drivers if they are there

```

cd /usr/share/ati
./fglrx-uninstall.sh

```After it's done it will tell you to reboot. Then do the following

```

sh ati-driver-installer-11-8-x86.x86_64.run

```After a few seconds the installer should pop up, instead of choosing create distro specific installation package choose install on Xorg 6.9 or greater. It will go through it's install process and tell you to reboot.

After reboot your new drivers should be working properly, verify with lsmod etc etc.

if you need an xorg.conf run ati-config --initial

Hope that helps.

When I tried it with the Xorg 6.9 install, I get an error that says 

>  DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details 

---

### Post by Dangertux on 2011-10-01
> **girlrepellent said:**
> When I tried it with the Xorg 6.9 install, I get an error that says


What does the entry in the log say?

---

### Post by girlrepellent on 2011-10-01
~# more /usr/share/ati/fglrx-install.log
Uninstalling any previously installed drivers.
Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.881/source ->
                 /usr/src/fglrx-8.881

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you
 could install the linux-headers-2.6.39.4 package.
[Error] Kernel Module : Failed to build fglrx-8.881 with DKMS
[Error] Kernel Module : Removing fglrx-8.881 from DKMS

------------------------------
Deleting module version: 8.881
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs

Also, a new thing happened. When I logged in, I got a pop-up saying that I have to go into low-graphics mode.

---

### Post by Claus7 on 2011-10-01
Hello,

the low graphics mode is not necessarily a bad thing as in most cases it means that you have to make some adjustments and configurations.

I have one question: did you get the same result with older proprietary fglrx drivers from amd? Or every time you try to install them you get the DKMS issue?

Also, is dkms installed via synaptic package manager? Because during the installation of the driver is seems that dkms path is missing. Do you think that you might have installed it manually? One quick thing you could do, is open synaptic and check if it is installed. While checking, I saw that this package is installed. You could try a re-installation just in case...

edit: are you running all these commands via command line as root?

Regards!

---

### Post by girlrepellent on 2011-10-01
The only drivers I have tried to install were the 11.8 and 11.9. I could not find any of the older drivers for my specific video card (ATI radeon HD 4200) to test with. I am doing all of this as root in the command line. I reinstalled the dkms via command "apt-get install DKMS" and got that it is up-to-date and nothing was installed. I have updated everything I can think of that would be related to the graphics (anything that is in the log file for the installation) and for some reason, when I run ./ati* --force and go through the gui that pops up, I get the DKMS error. This does only happen when I try to install on Xorg 6.9 or greater, it does not happen when I try to make a specific distro. The specific distro does nothing when I reboot.

---

### Post by Dangertux on 2011-10-01
Is this on backtrack (or is your hostname just bt)? Because if so you made need to install jockey-gtk it doesn't come by default with backtack and is a dependency of the proprietary drivers (in regards to the distro specific compile)

---

### Post by girlrepellent on 2011-10-01
Yes, this is backtrack r1. I ran the apt-get install jockey-gtk and got:

root@bt:~# sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  xfonts-75dpi xfonts-scalable xorg-docs-core xfonts-100dpi
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Dangertux on 2011-10-01
Have you tried fully removing dkms and reinstalling?

```

sudo apt-get remove --purge dkms
sudo apt-get install dkms

```

Then retrying the installation?

---

### Post by girlrepellent on 2011-10-01
I purged the dkms, installed, and rebooted then installed the graphics driver again and same error.

root@bt:~/catalyst11.3# more /usr/share/ati/fglrx-install.log
Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Installation with force option.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0

Creating symlink /var/lib/dkms/fglrx/8.892/source ->
                 /usr/src/fglrx-8.892

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you
 could install the linux-headers-2.6.39.4 package.
[Error] Kernel Module : Failed to build fglrx-8.892 with DKMS
[Error] Kernel Module : Removing fglrx-8.892 from DKMS

------------------------------
Deleting module version: 8.892
completely from the DKMS tree.
------------------------------
Done.

---

### Post by girlrepellent on 2011-10-01
There is no /var/lib/dkms/fglrx/8.892/source directory on my computer.

---

### Post by girlrepellent on 2011-10-01
Uninstall log

more /etc/ati/fglrx-uninstall.log
*** AMD Catalyst(TM) Proprietary Driver Uninstall Log 2011-10-01 12:45:11 ***
File is missing from system /usr/share/doc/ati/LICENSE.TXT.
File is missing from system /usr/share/doc/ati/user-manual/index.html.
File is missing from system /usr/share/doc/ati/examples/etc/init.d/atieventsd.sh
.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-ac-ati
config.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/events/a-lid-at
iconfig.
File is missing from system /usr/share/doc/ati/examples/etc/acpi/ati-powermode.s
h.
File is missing from system /usr/share/doc/ati/articles/1gbhang.html.
File is missing from system /usr/share/doc/ati/articles/4461.html.
File is missing from system /usr/share/doc/ati/articles/4462.html.
File is missing from system /usr/share/doc/ati/articles/4463.html.
File is missing from system /usr/share/doc/ati/articles/4464.html.
File is missing from system /usr/share/doc/ati/articles/4469.html.
File is missing from system /usr/share/doc/ati/articles/4470.html.
File is missing from system /usr/share/doc/ati/articles/4475.html.
File is missing from system /usr/share/doc/ati/articles/4478.html.
File is missing from system /usr/share/doc/ati/articles/4479.html.
File is missing from system /usr/share/doc/ati/articles/4480.html.
File is missing from system /usr/share/doc/ati/articles/4481.html.
File is missing from system /usr/share/doc/ati/articles/4482.html.
File is missing from system /usr/share/doc/ati/articles/4483.html.
File is missing from system /usr/share/doc/ati/articles/4484.html.
File is missing from system /usr/share/doc/ati/articles/4485.html.
File is missing from system /usr/share/doc/ati/articles/corruptstereo.html.
File is missing from system /usr/share/doc/ati/articles/corruptvtswitch.html.
File is missing from system /usr/share/doc/ati/articles/devshm.html.
File is missing from system /usr/share/doc/ati/articles/dga3dhang.html.
File is missing from system /usr/share/doc/ati/articles/doom3corrupt.html.
File is missing from system /usr/share/doc/ati/articles/dualheadvideo.html.
File is missing from system /usr/share/doc/ati/articles/laptopsuspend.html.
File is missing from system /usr/share/doc/ati/articles/missingdrmheaders.html.
File is missing from system /usr/share/doc/ati/articles/mousecursorhang.html.
File is missing from system /usr/share/doc/ati/articles/no3d-aiw8500dv.html.
File is missing from system /usr/share/doc/ati/articles/no3d-kt400.html.
File is missing from system /usr/share/doc/ati/articles/nomembercount.html.
File is missing from system /usr/share/doc/ati/articles/pcie3dmemoryleak.html.
File is missing from system /usr/share/doc/ati/articles/r420blankdisplay.html.
File is missing from system /usr/share/doc/ati/articles/rv280dviblankdisplay.htm
l.
File is missing from system /usr/share/doc/ati/articles/rv350springdale.html.
File is missing from system /usr/share/doc/ati/articles/secondheadcorruption.htm
l.
File is missing from system /usr/share/doc/ati/articles/xf86_enodev.html.
File is missing from system /usr/share/doc/ati/articles/xrestartpcie.html.
File is missing from system /usr/share/doc/ati/articles/xvsatshift.html.
File is missing from system /usr/share/doc/ati/configure.html.
File is missing from system /usr/share/doc/ati/driverfaq.html.
File is missing from system /usr/share/doc/ati/index.html.
File is missing from system /usr/share/doc/ati/installer.html.
File is missing from system /usr/share/doc/ati/issues.html.
File is missing from system /usr/share/doc/ati/linuxfaq.html.
File is missing from system /usr/share/doc/ati/tips-linux.html.
File is missing from system /usr/share/man/man8/atieventsd.8.
File is missing from system /usr/lib64/xorg/modules/linux/libfglrxdrm.so.
File is missing from system /usr/lib64/xorg/modules/drivers/fglrx_drv.so.
File is missing from system /usr/lib64/xorg/modules/glesx.so.
File is missing from system /usr/lib64/xorg/modules/amdxmm.so.
File is missing from system /usr/lib32/libAMDXvBA.cap.
File is missing from system /usr/lib32/libAMDXvBA.so.1.0.
File is missing from system /usr/lib32/libatiadlxx.so.
File is missing from system /usr/lib32/libaticalcl.so.
File is missing from system /usr/lib32/libaticaldd.so.
File is missing from system /usr/lib32/libaticalrt.so.
File is missing from system /usr/lib32/libatiuki.so.1.0.
File is missing from system /usr/lib32/libfglrx_dm.a.
File is missing from system /usr/lib32/libfglrx_dm.so.1.0.
File is missing from system /usr/lib32/libXvBAW.so.1.0.
File is missing from system /usr/lib32/fglrx/fglrx-libGL.so.1.2.
md5sum integrity check failed for /usr/lib64/fglrx/switchlibGL.
md5sum integrity check failed for /usr/lib64/fglrx/switchlibglx.
File is missing from system /usr/lib32/dri/fglrx_dri.so.
File is missing from system /usr/lib64/xorg/modules/extensions/fglrx/fglrx-libgl
x.so.
File is missing from system /usr/lib64/libAMDXvBA.cap.
File is missing from system /usr/lib64/libAMDXvBA.so.1.0.
File is missing from system /usr/lib64/libatiadlxx.so.
File is missing from system /usr/lib64/libaticalcl.so.
File is missing from system /usr/lib64/libaticaldd.so.
File is missing from system /usr/lib64/libaticalrt.so.
File is missing from system /usr/lib64/libatiuki.so.1.0.
File is missing from system /usr/lib64/libfglrx_dm.a.
File is missing from system /usr/lib64/libfglrx_dm.so.1.0.
File is missing from system /usr/lib64/libXvBAW.so.1.0.
File is missing from system /usr/lib64/fglrx/fglrx-libGL.so.1.2.
File is missing from system /usr/lib64/dri/fglrx_dri.so.
File is missing from system /usr/include/GL/glATI.h.
File is missing from system /usr/include/GL/glxATI.h.
File is missing from system /usr/include/ATI/GL/glxext.h.
File is missing from system /usr/include/ATI/GL/glx.h.
File is missing from system /usr/bin/fgl_glxgears.
File is missing from system /usr/bin/fglrxinfo.
File is missing from system /usr/bin/aticonfig.
File is missing from system /usr/bin/atiodcli.
File is missing from system /usr/bin/atiode.
File is missing from system /usr/src/ati/fglrx_sample_source.tgz.
File is missing from system /usr/sbin/amdnotifyui.
File is missing from system /usr/sbin/atieventsd.
File is missing from system /usr/sbin/atigetsysteminfo.sh.
File is missing from system /etc/ati/amdpcsdb.default.
File is missing from system /etc/ati/atiogl.xml.
File is missing from system /etc/ati/authatieventsd.sh.
File is missing from system /etc/ati/control.
File is missing from system /etc/ati/logo_mask.xbm.example.
File is missing from system /etc/ati/logo.xbm.example.
File is missing from system /etc/ati/signature.
File is missing from system /usr/X11R6/lib/modules/dri/fglrx_dri.so.
File is missing from system /usr/X11R6/lib64/modules/dri/fglrx_dri.so.
File is missing from system /usr/bin/amdconfig.
File has been removed, //usr/lib64/libGL.so.1.2, since last install.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.

---

### Post by Claus7 on 2011-10-01
Hello,

> **girlrepellent said:**
> ...This does only happen when I try to install on Xorg 6.9 or greater, it does not happen when I try to make a specific distro. The specific distro does nothing when I reboot.

then, why don't you use the built option for your specific distro? If this is working then stick to it for a start. 

What do you mean that it does nothing when you reboot? Do you see a black screen, do you have low graphics mode? Because, afterwords you have to configure manually a file called xorg.conf, yet this is another issue. Could you be more specific on what is happening when you reboot? 

Don't know if this is the best way to follow, yet you might find there a solution.

Regards!

---

### Post by Claus7 on 2011-10-01
Hello once again,

I use a different post because I will cover different things than previously posted:

1) here is a link with previous ati linux 64 bit catalyst drivers from amd's website. If I were in your shoes, I would try something like version 11.6 and below. See if you have the same errors.
[http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

2) Taking a look in the error log file you provide, I checked out e.g. if
 cd /usr/share/doc/ati
folder exists and I got 
bash: cd: /usr/share/doc/ati: No such file or directory

which means that it is not necessary this file for my configuration to work. I use catalyst 11.6. I think that versions 11.7 and higher use difficulties to users with ubuntu versions that older than maverick.

I guess that the newest catalyst might work differently and it creates those folders.

As a result I would propose you to use an older driver. Here could you remind us the ubuntu version you are using?

And one more thing: if you are not able to follow the link directly, you could go to amd's website and when you choose to download the driver for your specific version (e.g. linux 64 bit) click on the web-page that will show up the option: previous drivers.

Regards!

---

### Post by girlrepellent on 2011-10-01
I did once get a prompt saying that it was switching to low graphics mode, but never got it again after that one time. Everything is fine when I reboot. When I say fine, the GNOME interface works just fine.

---

### Post by girlrepellent on 2011-10-02
I tried install catalysts 11.1- current with the command ./ati* --force (Force to uninstall the previous version and force a new install) and it still fails every time at the DKMS portion of the install.

---

### Post by girlrepellent on 2011-10-02
> **Claus7 said:**
> Hello,



then, why don't you use the built option for your specific distro? If this is working then stick to it for a start. 

What do you mean that it does nothing when you reboot? Do you see a black screen, do you have low graphics mode? Because, afterwords you have to configure manually a file called xorg.conf, yet this is another issue. Could you be more specific on what is happening when you reboot? 

Don't know if this is the best way to follow, yet you might find there a solution.

Regards!

When I rebooted the first time after I used the specific distro option, I got a pop-up saying that it was going to use low graphics mode. After that, I did the initial config on ati using the aticonfig --initial to which I got "aticonfig: command not found"

---

### Post by Claus7 on 2011-10-02
Hello,

not a solution you are seeking, but is it possible to install fglrx from synaptic? Or this is failing as well?

Regards!

---

### Post by girlrepellent on 2011-10-02
> **Claus7 said:**
> Hello,

not a solution you are seeking, but is it possible to install fglrx from synaptic? Or this is failing as well?

Regards!

I was just about to post about that. When I was trying that, I noticed that the packages were broken. So I tried to reinstall them through synaptic package manager and I am getting "E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu5_amd64.deb: subprocess new pre-installation script returned error exit status 1" To this, I ran an apt-get -f install to make sure there is nothing that I missed and also ran an apt-get update and it didn't help. When I try to manually install the dependencies using

```
 sudo dpkg -i *.deb 
```I get
 Errors were encountered while processing:
 fglrx_8.861-0ubuntu1_amd64.deb
 fglrx-amdcccle
 fglrx-dev

I am also doing as much research on the side as I can about this so hopefully someone will find this post useful if they run into the same problem :D

---

### Post by Claus7 on 2011-10-02
Hello,

glad that at least we found something that might solve your problem.

Check this link here and see if you can fix the issue with broken packages. I think that this should be fixed first, before you try anything else.
[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)
(post 9)

Regards!

---

