---
title: "Trouble installing an internet connection."
date: 2011-11-16
forum: General Help
---

### Post by linux_beg on 2011-11-16
Hello ppl. I'm a newbie on everithing about Linux and I'm a very basic computer user. I'm trying a Lubuntu distro (latest relase, downloaded yesterday) from a USB stick, and i'm trying to configure my wireless internet connection without success. When I enter to "Network configuration" no network is shown  I tried a few commands, sudo "iwconfig" and "sudo lspci", and it seems that I need some driver, supposedly the VT6102. I downloaded the driver, followed the instructions for linux and everithing went fine until I had to compile the source code. It says that some location didn't exist and that I had to install the kernell headers. I typed the command it suggested and it said that i must explicitly say which i wanted to install from a list. I can't remmember all af the list except two, which were something like "Linux Virtual" and "Linux Generic". I don't know what to do now. I would appreciate some help.

---

### Post by MG&amp;TL on 2011-11-16
Wow, that's harsh for a newbie. :shocked: Mucking about with the kernel is considered 'not for mere mortals'

Firstly, what hardware do you have?

Secondly, have you gone to 'additional drivers' in LxMenu -> Preferences -> Additional Drivers and tried there first?

---

### Post by linux_beg on 2011-11-16
Hello MG&TL, thanks for your answer. My hardware is [http://alturl.com/y5qy4](http://alturl.com/y5qy4). I don't know if you can get any usefull info from the outuput of the commands i typed, so here they are:

For iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

```

00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
04:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
04:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

```

And for the option of "Aditional Drivers" no, i haven't tried. I will try with that one and will coma back later to tell you how it went.

---

### Post by linux_beg on 2011-11-16
Hello, I tried again following the instruction provided in the driver's folder and here's what happened:

```

ubuntu@ubuntu:~$ mkdir temp
ubuntu@ubuntu:~$ cd temp
ubuntu@ubuntu:~/temp$ mount -t msdod /dev/fd0/mnt
mount: only root can do that

###### COMMENT: Here i copied the driver manually to temp. ######

ubuntu@ubuntu:~/temp$ tar xvf linuxfet.tar
Makefile
linux.txt
linuxfet.c
linuxfet.h
ubuntu@ubuntu:~/temp$ make install
The program 'make' is currently not installed.  You can install it by typing:
sudo apt-get install make
ubuntu@ubuntu:~/temp$ sudo apt-get insltall make
E: Invalid operation insltall
ubuntu@ubuntu:~/temp$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
 make-doc
The following NEW packages will be installed:
make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/116 kB of archives.
After this operation, 319 kB of additional disk space will be used.
Selecting previously deselected package make.
(Reading database ... 120902 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.1ubuntu1) ...
ubuntu@ubuntu:~/temp$ make install
***  Clean up older object files  ***
rm -f core *.o *~
*****  Sorry, the kernel header files path /usr/src/linux/include doesn't exist.

*****  We can't compile this driver successfully without it.
*****  Please install kernel header files before you compile this driver.
ubuntu@ubuntu:~/temp$ sudo apt-get install headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package headers
ubuntu@ubuntu:~/temp$ sudo apt-get install headers /usr/src
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package headers
E: Unable to locate package /usr
ubuntu@ubuntu:~/temp$ sudo apt-get install headers /usr/src/linux-headers-3.0.0-12

###### COMMENT: This route is where i found the headers. ######

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package headers
E: Unable to locate package /usr/src
ubuntu@ubuntu:~/temp$

```

Still dont know what to do :(

---

### Post by MG&amp;TL on 2011-11-16
You HAVE tried additional drivers?
Can you try this?

Run:

```
uname -a
```

Then copy the 3.xxxxx bit in to this:

```
sudo apt-get install linux-headers-3.xxxxxx
```

And try the make again.

---

### Post by linux_beg on 2011-11-16
I tried and look what it says:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
ubuntu@ubuntu:~$ sudo apt-get install linux-headers-3.0.0-12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-12 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

¿Any idea?

---

### Post by MG&amp;TL on 2011-11-16
Can you post the contents of the 'Makefile'-and you're sure there is no entry in 'additional drivers'?

---

