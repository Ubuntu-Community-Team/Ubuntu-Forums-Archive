---
title: "HP SmartMedia Server Ubuntu 9.04"
date: 2009-08-23
forum: General Help
---

### Post by SteffJay on 2009-08-23
I am trying to install Ubuntu 9.04 onto HP SmartMedia Server EX470 but am having problems with the LAN (eth0) not working and the VGA is also bad. There are Linux drivers for this but i do not know how to install them. The LAN (eth0) driver is a sis190191_linux.tar and the VGA driver is a XG-762N_Windows_DnU. Can anybody give me an idea as to how i can install these to get the screen resolution right and get the LAN to work ?? Any help would be gratefully appreciated !! :(

---

### Post by P4man on 2009-08-23
Please open a terminal and type 

```
lspci
```

and copy/paste the output here, so we can see what videocard and lan you have.

---

### Post by SteffJay on 2009-08-23
> **P4man said:**
> Please open a terminal and type 

```
lspci
```

and copy/paste the output here, so we can see what videocard and lan you have.

Sorry for the delay. See below:

steff@server:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)

If you can make any sense out of all that, your a hidden Einstein !!

---

### Post by sandyd on 2009-08-23
> **SteffJay said:**
> Sorry for the delay. See below:

steff@server:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)

If you can make any sense out of all that, your a hidden Einstein !!
I can
video card: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

network card: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 01)

---

### Post by sandyd on 2009-08-23
> **SteffJay said:**
> I am trying to install Ubuntu 9.04 onto HP SmartMedia Server EX470 but am having problems with the LAN (eth0) not working and the VGA is also bad. There are Linux drivers for this but i do not know how to install them. The LAN (eth0) driver is a sis190191_linux.tar and the VGA driver is a XG-762N_Windows_DnU. Can anybody give me an idea as to how i can install these to get the screen resolution right and get the LAN to work ?? Any help would be gratefully appreciated !! :(
im assuming the tar is on your desktop k?
```

cd ~/Desktop
tar xvf sis190191_linux.tar
cd sis*
./configure
make
sudo make install

```

that video driver ain't compatible with linux. looking at [http://sis.com/download](http://sis.com/download) , there is no linux driver for that particular card. however, you can try either of the drivers and pray that they work for your card.

---

### Post by SteffJay on 2009-08-23
> **carlee said:**
> I can
video card: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

network card: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 01)

Not just a pretty face. Thank you for the heads up. Now can you tell me how to install the drivers ??? :confused:

---

### Post by sandyd on 2009-08-23
> **SteffJay said:**
> Not just a pretty face. Thank you for the heads up. Now can you tell me how to install the drivers ??? :confused:
assuming the network driver is on your desktop, running
```

cd ~/Desktop
tar xvf sis190191_linux.tar
cd sis*
./configure
make
sudo make install

```
in the terminal should get your network running.

i did a nice search on google, and my advice is to stick any other video card you have in the server. that card you have right now is useless and horrible in *nix.

---

### Post by SteffJay on 2009-08-23
> **carlee said:**
> assuming the network driver is on your desktop, running
```

cd ~/Desktop
tar xvf sis190191_linux.tar
cd sis*
./configure
make
sudo make install

```
in the terminal should get your network running.

i did a nice search on google, and my advice is to stick any other video card you have in the server. that card you have right now is useless and horrible in *nix.

Everything is fine up to the ./configure then it returns bash: ./configure: No such file or directory :(

---

### Post by SteffJay on 2009-08-23
> **carlee said:**
> assuming the network driver is on your desktop, running
```

cd ~/Desktop
tar xvf sis190191_linux.tar
cd sis*
./configure
make
sudo make install

```
in the terminal should get your network running.

i did a nice search on google, and my advice is to stick any other video card you have in the server. that card you have right now is useless and horrible in *nix.

Unfortunately, the GFX is onboard and there is no way of adding a new card. The HP SmartMedia Server EX470 is a mini server and the only extras it has is 3 x slots for hot-swap for esata hard drives.

---

### Post by sandyd on 2009-08-23
> **SteffJay said:**
> Everything is fine up to the ./configure then it returns bash: ./configure: No such file or directory :(
hmm...
i guess it doesn't follow the linux standrads.
could you post the output of
```

ls

```
while your in the folder?

---

### Post by SteffJay on 2009-08-23
> **carlee said:**
> hmm...
i guess it doesn't follow the linux standrads.
could you post the output of
```

ls

```
while your in the folder?

steff@server:~/Desktop/sis190_20041220$ ls
readme.txt  relnote.txt  sis190.c
steff@server:~/Desktop/sis190_20041220$

---

### Post by sandyd on 2009-08-23
im afraid your day is gonna get a little worse from reading this
```
//** Install sis190 module into linux kernel. **//

**1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)**

2. Download Linux kernel 2.6.9 or latter version from http://www.kernel.org. The follwing examples are based on linux-2.6.9.

3. copy the kernel source to the location /usr/src/linux-2.6.9.

4. cp sis190.c /usr/src/linux-2.6.9/drivers/net

5. Edit the file "/usr/src/linux-2.6.9/drivers/net/Kconfig".
    a. Serach for the string "config SIS900"
    b. Add the following item below the item of SIS190.

config SIS190
        tristate "SiS 191/190 PCI Gigabit/Fast Ethernet Adapter support"
        depends on NET_PCI && PCI
        select CRC32
        ---help---
          Say Y here if you have a SiS 191/190 PCI Gigabit/Fast Ethernet adapter.

          To compile this driver as a module, choose M here: the module
          will be called sis190.  This is recommended.

6. Edit the file "/usr/src/linux-2.6.9/drivers/net/Makefile".
    a. Search for the string "obj-$(CONFIG_SIS900) += sis900.o".
    b. Insert "obj-$(CONFIG_SIS190) += sis190.o" to next line.

7. cd /usr/src/linux-2.6.9

8. Input the command 'make menuconfig'. Then the Linux Kernel configuration menu will be popped.
    a. Select "Device Drivers -->", "Networking support -->", "Ethernet (10 or 100Mbit) -->".
    b. Goto the item "SiS191/190 PCI Gigabit/Fast Ethernet Adapter support".
    c. Press space key to make this item marked with <M>.
    d. Save and exit the kernel configuration menu.

9. Make kernel and modules. Input the command 'make bzImage modules modules_install install'.

10. Reboot and Select the boot item "2.6.9".


//** Probe sis190 module **//

1. Input the command 'rmmod sis190'.

2. Input the command 'modprobe sis190'.

3. Input the command 'ifconfig eth0 <ip_addr>'.
    a. <ip_addr> is the IP address of sis190.
    b. example: 'ifconfig eth0 192.168.209.1'.

```
which makes me wonder how old this driver is. Although it says to install fedora core 3, you could try the instructions in ubuntu... but it could also completely nuke your system. 
now, servers are never meant for desktop use, so im not suprised at the lack of support. (even though im typing from one at this very moment). If i were you, i would simply re-install windows on there and it **should** work as thats what i think it had in the first place. and no, this time its not ubuntu's fault. the manufacturer is just providing outdated, unusable drivers.

---

### Post by P4man on 2009-08-24
Im not sure if you intend to run this machine as desktop, or as server. For a server, video card performance doesn't really matter, for a desktop,
that videocard is always going to be crap, particularly on linux. Your best it probably using a bog standard vesa driver.

Open a terminal and type:

```
sudo nano /etc/X11.xorg.conf
```

find the device section that probably looks like this: (if not, please post your entire xorg.conf file):

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"**sis**"
	BusID		"PCI:1:0:0"
EndSection
```

change it to:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"**vesa**"
EndSection

```

press control+x and Y to save. Restart X or reboot for the changes to go in to effect.

This will mean sluggish 2D,  no 3D, no fancy effects, and probably even bad videoplayback. But it should work at least.

---

### Post by SteffJay on 2009-08-24
> **carlee said:**
> im afraid your day is gonna get a little worse from reading this
```
//** Install sis190 module into linux kernel. **//

**1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)**

2. Download Linux kernel 2.6.9 or latter version from http://www.kernel.org. The follwing examples are based on linux-2.6.9.

3. copy the kernel source to the location /usr/src/linux-2.6.9.

4. cp sis190.c /usr/src/linux-2.6.9/drivers/net

5. Edit the file "/usr/src/linux-2.6.9/drivers/net/Kconfig".
    a. Serach for the string "config SIS900"
    b. Add the following item below the item of SIS190.

config SIS190
        tristate "SiS 191/190 PCI Gigabit/Fast Ethernet Adapter support"
        depends on NET_PCI && PCI
        select CRC32
        ---help---
          Say Y here if you have a SiS 191/190 PCI Gigabit/Fast Ethernet adapter.

          To compile this driver as a module, choose M here: the module
          will be called sis190.  This is recommended.

6. Edit the file "/usr/src/linux-2.6.9/drivers/net/Makefile".
    a. Search for the string "obj-$(CONFIG_SIS900) += sis900.o".
    b. Insert "obj-$(CONFIG_SIS190) += sis190.o" to next line.

7. cd /usr/src/linux-2.6.9

8. Input the command 'make menuconfig'. Then the Linux Kernel configuration menu will be popped.
    a. Select "Device Drivers -->", "Networking support -->", "Ethernet (10 or 100Mbit) -->".
    b. Goto the item "SiS191/190 PCI Gigabit/Fast Ethernet Adapter support".
    c. Press space key to make this item marked with <M>.
    d. Save and exit the kernel configuration menu.

9. Make kernel and modules. Input the command 'make bzImage modules modules_install install'.

10. Reboot and Select the boot item "2.6.9".


//** Probe sis190 module **//

1. Input the command 'rmmod sis190'.

2. Input the command 'modprobe sis190'.

3. Input the command 'ifconfig eth0 <ip_addr>'.
    a. <ip_addr> is the IP address of sis190.
    b. example: 'ifconfig eth0 192.168.209.1'.

```
which makes me wonder how old this driver is. Although it says to install fedora core 3, you could try the instructions in ubuntu... but it could also completely nuke your system. 
now, servers are never meant for desktop use, so im not suprised at the lack of support. (even though im typing from one at this very moment). If i were you, i would simply re-install windows on there and it **should** work as thats what i think it had in the first place. and no, this time its not ubuntu's fault. the manufacturer is just providing outdated, unusable drivers.

Hmmm... It seems i'm in between a rock and a hard place here !! If it recomends loading Fedora Core 3 (which does'nt make sense to me at this stage) and kernal 2.6.9 (mine at present is 2.6.28-11 generic) it will surely break the system ?? I cannot see why the driver is so old as the machine is brand new plus if the driver **is** that old, surely it would have been implemented in previous Ubuntu distros ?? Confused.com !!!

---

### Post by SteffJay on 2009-08-24
> **P4man said:**
> Im not sure if you intend to run this machine as desktop, or as server. For a server, video card performance doesn't really matter, for a desktop,
that videocard is always going to be crap, particularly on linux. Your best it probably using a bog standard vesa driver.

Open a terminal and type:

```
sudo nano /etc/X11.xorg.conf
```

find the device section that probably looks like this: (if not, please post your entire xorg.conf file):

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"**sis**"
	BusID		"PCI:1:0:0"
EndSection
```

change it to:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"**vesa**"
EndSection

```

press control+x and Y to save. Restart X or reboot for the changes to go in to effect.

This will mean sluggish 2D,  no 3D, no fancy effects, and probably even bad videoplayback. But it should work at least.

I intend to run 9.04 as a server (with GUI) as my terminal expertise is totaly cr*p !! I can struggle along with the bad video output because i mainly remotely connect from a different computer using VNC. The video is fine doing it this way. My main concern is to get the LAN working. I am currently using a USB modem to do updates etc but the transfer rate is somewhat lacking, plus it would not be able to handle the traffic i intend for it.

---

