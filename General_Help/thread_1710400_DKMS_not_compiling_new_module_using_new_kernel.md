---
title: "DKMS not compiling new module using new kernel"
date: 2011-03-19
forum: General Help
---

### Post by CharlesA on 2011-03-19
Hiya,

I'm trying to set it up so that I don't have to recompile the driver for my RAID card manually every time there is a kernel upgrade.

I found a thread on it, [here]("http://ubuntuforums.org/showthread.php?t=1633597") and a help page [here]("https://help.ubuntu.com/community/RocketRaid"), and it looks like it builds the module fine, but for some reason it's not being inserted into the new kernel, or something. It's like the new kernel doesn't know it exists, even tho modprobe -l shows the newly built module exists (and is in the correct place)

Here's the script that I wrote up to get the drivers set up in DKMS:

```
#!/bin/bash

set -e

RAID=rr2640-linux-src-v1.2-090925-0932.tar.gz

apt-get install build-essential linux-headers-$(uname -r) dkms --assume-yes
wget http://www.support-highpoint-tech.com/Main/rr26xx/264x/Linux/opensrc/$RAID && ${BIN}tar -xf $RAID
cd rr2640-linux-src-v1.2
cd inc/linux
cp Makefile.def Makefile.def.orig
sed -i -e 's/^CFLAGS/EXTRA_CFLAGS/' -e 's/(CFLAGS/(EXTRA_CFLAGS/' Makefile.def
cd ../..
echo 'MAKE[0]="make"
BUILT_MODULE_NAME[0]=rr26xx
DEST_MODULE_LOCATION[0]=/kernel/drivers/scsi
PACKAGE_NAME=rr26xx
PACKAGE_VERSION=1.2
AUTOINSTALL=yes
POST_BUILD="do_Module.symvers rr26xx save $dkms_tree/$module/$module_version/build/Module.symvers"
REMAKE_INITRD=yes' > dkms.conf
cp product/rr2640/linux/* .
mv Makefile Makefile_orig
sed 's/HPT_ROOT := ..\/..\/../HPT_ROOT := \/var\/lib\/dkms\/rr26xx\/1.2\/build/' Makefile_orig >Makefile
cd ..
mv rr2640-linux-src-v1.2 /usr/src/rr26xx-1.2
mv /usr/src/rr26xx-1.2/lib /usr/src/rr26xx-1.2/real_lib
ln -s /usr/src/rr26xx-1.2/real_lib /usr/src/rr26xx-1.2/lib
dkms add -m rr26xx -v 1.2
dkms build -k $(uname -r) -m rr26xx -v 1.2
dkms install -k $(uname -r) -m rr26xx -v 1.2
mkinitramfs -o /boot/initrd.img-$(uname -r) $(uname -r)

```

After booting into the new kernel, and running this:

```
sudo modprobe rr26xxp
```
All it spits back is "invalid module format"

If I try the same command on the previous kernel, it returns no error.

Any ideas on this? It's quite frustrating, that's for sure.

EDIT: It looks like KDMS is compiling the module for the new kernel using the old kernel headers (or something):

Non-working module:
```
charles@ThorTest:~$ cat kernel26
[COLOR="Red"]filename:       /lib/modules/2.6.32-26-server/updates/dkms/rr26xx.ko[/COLOR]
license:        Proprietary
description:    RAID driver
author:         HighPoint Technologies, Inc.
alias:          pci:v00001103d00002620sv*sd*bc*sc*i*
alias:          pci:v00001103d00002640sv*sd*bc*sc*i*
depends:
[COLOR="Red"]vermagic:       2.6.32-24-server SMP mod_unload modversions[/COLOR]
parm:           autorebuild:int
```

Working module:
```
charles@ThorTest:~$ modinfo rr26xx
[COLOR="Blue"]filename:       /lib/modules/2.6.32-24-server/updates/dkms/rr26xx.ko[/COLOR]
license:        Proprietary
description:    RAID driver
author:         HighPoint Technologies, Inc.
alias:          pci:v00001103d00002620sv*sd*bc*sc*i*
alias:          pci:v00001103d00002640sv*sd*bc*sc*i*
depends:
[COLOR="Blue"]vermagic:       2.6.32-24-server SMP mod_unload modversions[/COLOR]
parm:           autorebuild:int
```

I'm not quite sure why it's doing it that way.

EDIT2: It seems like the headers it uses to compile is hardcodeded into markfile.def. No idea if they can be changed or not.

---

### Post by AllGamer on 2011-04-25
This is exactly what i did [http://ubuntuforums.org/showpost.php?p=10718563&postcount=4](http://ubuntuforums.org/showpost.php?p=10718563&postcount=4)

like you, i did originally follow the same Wiki which lead people to believe using the DKMS was "*easier*" ...IMO big mistake.

after repeatedly doing this for 5 servers, and a combination of rr174x and/or rr26xx 

I actually figured out the cleanest + easiest way was simply to:

1. download open source driver for your model from Highpoint
2. untar the downloaded driver
3. cd to /<your home dir>/downloads/<driver filename dir>/products/linux...
4. sudo make install 
5. wait
6. you might see an error about missing "could not find /usr/src/<driver version>/.build/.him_<driver model>.o.cmd"
example [http://ubuntuforums.org/showthread.php?t=1612915](http://ubuntuforums.org/showthread.php?t=1612915)
it's safe to ignore it.
7. proceed with installing the HighPoint RAID Management software [http://ubuntuforums.org/showthread.php?t=1737847](http://ubuntuforums.org/showthread.php?t=1737847)
8. done

enjoy! :) ;)

---

### Post by CharlesA on 2011-04-25
Glad I am not alone.

I ended up just running the script I had originally that would download the drivers, and install it.

Previously I would reboot to load the modules automagically, but this time I just did:

```
sudo modprobe rr26xx
```

To load the driver. Everything worked fine including the web interface software.

Note: In order to install the web interface originally, I had to reboot into the updated kernel in order to get it to detect the driver that was being used. Not sure if it was something I was doing wrong, but I had used alien to convert the rpm to a deb in order to install.

---

### Post by AllGamer on 2011-04-26
yes, i didn't have much luck with the web interface

it would have been ideal to get the web version of the highpoint RAID management working to run on headless servers remotely

my current work around is to use VNC on gnome-desktop just so i can run the GUI version of the RAID management 

the CLI version was also failing to install properly and it causing problems with the automatic updates

perhaps one day i get more time i'll try to get the web version working again.

i was pressed for time, and i had to get the server up & running ASAP, didn't have the luxury of time to fix the web version bugs

I do notice many RPM packages seems to not be properly converted with alien, even when you use alien -c to also convert the scripts, which many times ends up going to the wrong path or something of that sort.

i was able to manually install the CLI at one point, by manually extracting the files and placing them where they were supposed to go with the necessary libraries, by analyzing both the original RPM and the converted DEB and comparing both of its scripts; however that's a dirty install, and i don't like that on my full time servers.

i'm planning to do something similar with the web version to see if i can get it install

---

### Post by CharlesA on 2011-04-26
Good luck.

I recall if I had to convert the web interface rpm using -c in order to convert the scripts. The funny thing is that it installed fine after a reboot - but not if I loaded the module manually.

*shrug*

---

