---
title: "RT5390 wireless help"
date: 2011-11-07
forum: General Help
---

### Post by rolltide101x on 2011-11-07
Im using Debian. (Yes I realize im not in the Debian forums lol)

Im trying to follow the steps here
[http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/)

But I cant get it to work without getting errors. Any help?

clate@debian:~$ cd Desktop
clate@debian:~/Desktop$ cd driver
clate@debian:~/Desktop/driver$ cp RT2860STA.dat RT5390STA.dat
cp: cannot create regular file `RT5390STA.dat': Permission denied
clate@debian:~/Desktop/driver$ su
Password: 
root@debian:/home/clate/Desktop/driver# cp RT2860STA.dat RT5390STA.dat
root@debian:/home/clate/Desktop/driver# mkdir -p /etc/Wireless/RT5390STA
root@debian:/home/clate/Desktop/driver# cp RT5390STA.dat /etc/Wireless/RT5390STA
root@debian:/home/clate/Desktop/driver# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/clate/Desktop/driver/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/clate/Desktop/driver/os/linux'
rm -rf os/linux/Makefile
root@debian:/home/clate/Desktop/driver# make
make -C tools
make[1]: Entering directory `/home/clate/Desktop/driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/clate/Desktop/driver/tools'
/home/clate/Desktop/driver/tools/bin2h
cp -f os/linux/Makefile.6 /home/clate/Desktop/driver/os/linux/Makefile
make -C /lib/modules/2.6.32-5-686/build SUBDIRS=/home/clate/Desktop/driver/os/linux modules
make: *** /lib/modules/2.6.32-5-686/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
root@debian:/home/clate/Desktop/driver# make install
make -C /home/clate/Desktop/driver/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/clate/Desktop/driver/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/clate/Desktop/driver/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.32-5-686/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/2.6.32-5-686/kernel/drivers/net/wireless/
install: cannot stat `rt5390sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/clate/Desktop/driver/os/linux'
make: *** [install] Error 2
root@debian:/home/clate/Desktop/driver# modprobe rt5390sta
FATAL: Module rt5390sta not found.
root@debian:/home/clate/Desktop/driver#

---

### Post by wildmanne39 on 2011-11-07
Hi a few things I noticed if you are using 11.04 you do not need the patch go into the directory and run this command and get rid of that drivers
```
make clean
make
sudo make uninstall
sudo depmod -a
sudo update-initramfs -u
```
Run the commands one line at a time.

The command with sudo you need to enter your password.

Then do this please:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 

```Run the commands one at a time and some will take a long time to complete, when they are done unplug your wired connection and reboot.
Thank you

---

### Post by rolltide101x on 2011-11-07
Thank you so much!!!!

Do you mind if I post your steps on the Debian forum? I will give you full credit. Your steps worked perfectly on Debian as well =)

Link to where I gave you full credit. Thanks again!

[http://forums.debian.net/viewtopic.php?f=7&t=72265&p=402471#p402471](http://forums.debian.net/viewtopic.php?f=7&t=72265&p=402471#p402471)

---

### Post by wildmanne39 on 2011-11-07
Hi, your welcome! I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

