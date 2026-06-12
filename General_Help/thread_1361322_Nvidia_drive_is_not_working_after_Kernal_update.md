---
title: "Nvidia drive is not working after Kernal update"
date: 2009-12-21
forum: General Help
---

### Post by Kdar on 2009-12-21
I installed my Nvidia driver (190.xx) manually.

But after kernel update on my Ubuntu 9.10 it would not let me use my nvidia driver.

How do I reconfigure my X11?

I tried to run this in termanl "sudo nvidia-xconfig", however, it didn't do anything to me. I still have this problem.

---

### Post by steveneddy on 2009-12-21
With manually installed video drivers the user must recompile the kernel module to run that software.

Basically just reinstall the driver like you did initially.

Most choose to use Envy (in the repos) to install the latest Nvidia drivers and keep them up to date after a kernel update.

I myself prefer to run Nvidia drivers from the repos so they stay working after a kernel update. I don't have time to play with this stuff all the time anymore, I just want my laptop to work, period.

---

### Post by Kdar on 2009-12-22
oh i see. So I just need to reinstall it again?

I have a question about this: If I will do this, will this waste space? Or it will over write the old files with new?

---

### Post by starcraft.man on 2009-12-22
> **Kdar said:**
> oh i see. So I just need to reinstall it again?

I have a question about this: If I will do this, will this waste space? Or it will over write the old files with new?

You can only have one version of the NVIDIA binary driver at a time. Every time to reinstall you will completely uninstall the existing verison, same if you upgrade. I've done it tonnes of times.

---

### Post by pbrane on 2009-12-22
if you add this script to /etc/kernel/postinst.d

```

#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0

```

you won't have to manually re-install your nvidia drivers any more. However you need to install the driver from /usr/src/ for this to work.  The script compiles the new driver everytime there is a kernel update. This is what I do. Envy does not always have the latest drivers.

this is what I do to install the nvidia driver to begin with. In a terminal:
```

sudo -s
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
dpkg-reconfigure -phigh xserver-xorg

**May have to use aptitude instead of apt-get**
apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')
apt-get --purge remove $(dpkg -l | grep xorg | grep nv | awk '{print $2}')

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run -O NVIDIA-Linux-190.53.pkg.run
**Change the driver location to the one you want. For instance I am using the 190.53 drivers**
install NVIDIA-Linux-190.53.pkg.run /usr/src
ln -s /usr/src/NVIDIA-Linux-190.53.pkg.run /usr/src/nvidia-driver

**log out, go to tty 2 CTRL+ALT+F2**
/etc/init.d/gdm stop

**may have to: **
	sudo killall Xorg
	
sh /usr/src/nvidia-driver

    [B]* Don't worry about pre-compiled binaries, just let the script compile the drivers itself.
    * If you run a 64bit OS, then let NViDIA install the 32bit backward compatibility modules.
    * When asked, double check to ensure you select 'NO' when the NViDIA installer asks to reconfigure the xorg.conf file.
      We don't want to change the xorg.conf file just yet, at least not until we are back in X.
[/B]
reboot

**Use a tty:**
sudo -s
cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
nvidia-xconfig

**May have to, but probably not:**
	sed -i '/^\s*Load\s*"type1"\s*$/d' /etc/X11/xorg.conf
	sed -i '/^\s*Load\s*"freetype"\s*$/d' /etc/X11/xorg.conf

**If the nvidia splash screen starts:**
sed -i '/Driver\s*.nvidia./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf

**Restart the X server**

gedit update-nvidia
	**Add this:**
	
#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0

**Save the file.**

install update-nvidia /etc/kernel/postinst.d

**Done!**

```

---

### Post by Kdar on 2009-12-22
> **starcraft.man said:**
> You can only have one version of the NVIDIA binary driver at a time. Every time to reinstall you will completely uninstall the existing verison, same if you upgrade. I've done it tonnes of times.
So even if version number of Nvidia binary driver will be different (newer driver) it will uninstall the old stuff first? right?

---

### Post by starcraft.man on 2009-12-22
> **Kdar said:**
> So even if version number of Nvidia binary driver will be different (newer driver) it will uninstall the old stuff first? right?

Correct. The installer of the .run works well like that. Any old version of an NVIDIA binary will be removed at beginning of install, unavoidable, prevents trouble.

---

### Post by Kdar on 2009-12-24
Thanks for all your help. I got it working now.

---

