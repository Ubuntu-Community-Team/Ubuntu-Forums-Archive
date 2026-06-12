---
title: "Can't understand installation instructions for wifi adapter"
date: 2010-06-01
forum: General Help
---

### Post by d5j9 on 2010-06-01
I just bought a new Asus USB-N13 B/G/N wifi adapter and I cannot figure out the instructions for building the driver from the CD. Apparently the instructions are for Red Hat, and I cannot figure out how to make it work with Ubuntu. I attached the Readme file, just let me know if you need any other files to make sense out of it. (I added the .txt extension so I could upload it, not sure if it matters.) I am running Lucid. Thanks in advance.

---

### Post by lsmobrian on 2010-06-01
first make sure you can build
```
sudo apt-get install build-essential
```

After that it looks like just running this inside of the unpacked directory, most likely none of the config options will need to change, so running make on the default is probably the best option 
```
make
```
Then there is the config file for the driver, and likely the directory doesnt exist
```
sudo mkdir -p /etc/Wireless/RT2870STA
```
```
sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
```
Also might try and see if it does anything
```
sudo make install
```
After that, you can try loading the module(if the install didnt already)
```
sudo /sbin/insmod rt3070sta.ko
```
From there, hopefully networkmanager can handle it

If that worked out, then you'll need to make sure that the module is loaded every time you boot.
```
sudo echo "rt3070sta" >> /etc/modules
```

---

### Post by d5j9 on 2010-06-02
> **lsmobrian said:**
> first make sure you can build
```
sudo apt-get install build-essential
```After that it looks like just running this inside of the unpacked directory, most likely none of the config options will need to change, so running make on the default is probably the best option 
```
make
```Then there is the config file for the driver, and likely the directory doesnt exist
```
sudo mkdir -p /etc/Wireless/RT2870STA
``````
sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
```Also might try and see if it does anything
```
sudo make install
```After that, you can try loading the module(if the install didnt already)
```
sudo /sbin/insmod rt3070sta.ko
```From there, hopefully networkmanager can handle it

If that worked out, then you'll need to make sure that the module is loaded every time you boot.
```
sudo echo "rt3070sta" >> /etc/modules
```

Thanks a lot for all that, but it's still not quite there yet.

```
sudo /sbin/insmod rt3070sta.ko
```

didn't work, giving the error 

insmod: can't read 'rt3070sta.ko': No such file or directory

I was thinking that it may be step 2 that is the problem:

> 2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

Not sure about where the kernel source is, or why it needs to know, for that matter.

---

### Post by jocko on 2010-06-02
> **d5j9 said:**
> Not sure about where the kernel source is, or why it needs to know, for that matter.
You need to have the kernel headers installed:
```
sudo apt-get install linux-headers-generic

```
The kernel headers will be installed in /usr/src, so I guess that's the path you need to set.

---

### Post by lsmobrian on 2010-06-02
Maybe try insmod without the extension (.ko) also might try replacing the insmod command with modprobe

Also, I missed where they put it once it was built, so you probably weren't in the right directory

cd os/linux/
ls *.ko

Hopefully you should have rt3070sta.ko listed


Edit, I checked the Makefile, your mode and target are fine. Also the make install should have loaded the driver for you.
run 'make install' again and run this to see if its loaded
```
lsmod | grep -i sta
```

---

### Post by d5j9 on 2010-06-03
> **lsmobrian said:**
> Maybe try insmod without the extension (.ko) also might try replacing the insmod command with modprobe

Also, I missed where they put it once it was built, so you probably weren't in the right directory

cd os/linux/
ls *.ko

Hopefully you should have rt3070sta.ko listed


Edit, I checked the Makefile, your mode and target are fine. Also the make install should have loaded the driver for you.
run 'make install' again and run this to see if its loaded
```
lsmod | grep -i sta
```

Still doesn't appear to have worked right, so I'll just post the full log of what I just did. Not all of it is relevant but I didn't want to miss something that is.

>    	 	 	 	 	 	  ****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ cd os/linux
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ ls *.ko
rt3070sta.ko
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo /sbin/insmod rt3070sta
[sudo] password for ****: 
insmod: can't read 'rt3070sta': No such file or directory
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo /sbin/insmod rt3070sta.ko
insmod: error inserting 'rt3070sta.ko': -1 Invalid module format
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo /sbin/insmod rt3070sta
insmod: can't read 'rt3070sta': No such file or directory
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ cd ..
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os$ cd ..
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ make install
make -C /home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux'
rm -rf /etc/Wireless/RT2870STA
rm: cannot remove `/etc/Wireless/RT2870STA/RT2870STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux'
make: *** [install] Error 2
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ lsmod | grep -i sta
vgastate                8961  1 vga16fb
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ cd os/linux
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko): Operation not permitted
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko): Invalid module format
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo modprobe rt3070sta.ko
FATAL: Module rt3070sta.ko not found.
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko): Invalid module format
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ cd ..
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os$ cd ..
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ sudo make install
make -C /home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-22-generic
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko
make[1]: Leaving directory `/home/****/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux'
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ lsmod | grep -i sta
vgastate                8961  1 vga16fb
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ cd os/linux
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo /sbin/insmod rt3070sta.ko
insmod: error inserting 'rt3070sta.ko': -1 Invalid module format
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo /sbin/insmod rt3070sta
insmod: can't read 'rt3070sta': No such file or directory
****@*********:~/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt3070sta.ko): Invalid module format
 

---

