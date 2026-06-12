---
title: "New starter trying to install drivers"
date: 2010-02-13
forum: General Help
---

### Post by kron00 on 2010-02-13
Hi,
 
I've just started using Linux and am having troubles getting various drivers to work/install
 
i've tried to install an nvidia 32bit linux graphics driver which fails once you right click it, display/run it and the progress bar gets to the end and just comes up red saying failed (can't remember what it exactly says)
 
i've also tried to install my pci wireless driver, the readme that came with it is very confusing, i tried to run the autorun.sh file, which doesnt seem to-do anything. i think i got somewhere by putting in code to the terminal which i got from the readme, but no luck.
 
Also is their a chipset driver i have to install? as with windows, when my comp starts all the fans come on at 100% then software throttles them once in windows, wheras with ubuntu their just 100% all the time.
 
Any help would be greatly appreciated 
 
i've tried looking for other threads to cure my problem with no luck. But did notice alot of people ask to see lspci results, here it is....
 
Mobo: Gigabyte P35-DS4 v1.1
 
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by squareff255 on 2010-02-13
Hey.

Pretty new to Linux myself, but I did install an NVIDIA graphics driver not to long ago... and I believe... ooh... My memory sucks, but I know I had to boot up Ubuntu in recovery mode and login to the root user to do it... didn't it come with a shell script or something? Like "install.sh"?

---

### Post by audiomick on 2010-02-13
It sounds a bit like you haven't tried using the hardware drivers utility

system> administration> hardware drivers

it should offer you drivers (for nVidia for sure, I think also for the broadcom card) which you can enable from there.

To set up your nVidia card once the driver is installed, do
```
gksu nvidia-settings
```
in the terminal to start the setup application.

---

### Post by Jive Turkey on 2010-02-13
You need to exit X and install the driver from a shell. there is a guide on the forums here.  Basically:
1. put the downloaded file in your home directory.
2. press ctrl+alt+F1 and log in to the shell.
3. Type sudo /etc/init.d/gdm stop
4. Type chmod +x NV  <...and then press the tab key to auto complete the file name>
5. Type sudo ./NV <press tab agian> and hit enter this should run the installer.  
6. when the installer finishes type sudo /etc/init.d/gdm start
... or you could just reboot with "sudo reboot now"

You will need to do this every time you update the kernel.  Search for the guide to "Install latest nvidia driver" in these forums for more info.

---

### Post by kron00 on 2010-02-13
i tried running the hardware driver utility, nothing is found saying "no propriatry devices are found"
 
i will try installing from the shell.
 
Thanks

---

### Post by kron00 on 2010-02-13
Thanks for everyone's help. Installing the graphics driver is now done but im still having problems with the wireless pci card. its now shown in the hardware driver bit in system but states "Activated but not in use"
 
i followed the instructions up to a certain point as i beleive its not working properly... (i did this in the shell)
 
Instructions i followed...
Unpack the tarball :  # tar vjxf r8168-8.aaa.bb.tar.bz2
Change to the directory:  # cd r8168-8.aaa.bb
 If you are running the target kernel, then you should be able to do : # ./autorun.sh (as root or with sudo)
 
Here is where nothing seems to happen...
 
You can check whether the driver is loaded by using following commands.
  # lsmod | grep r8168
  # ifconfig -a 
 If there is a device name, ethX, shown on the monitor, the linux driver is loaded.
 
There is alot more instructions about setting an IP/Gateway/Connection speed etc but shouldnt this be assigned to me by my router?
 
I believe i got the right driver, i searched for realtek 8168, should i have searched for broadcom instead?
 
Thanks

---

### Post by marshag63 on 2010-02-13
kron00, looking at your first post, your ethernet is Realtek and your wireless is Broadcom.  You will need B43-fwcutter to get wireless working.  I don't know how much of what you have already done will impact negatively on wireless setup of B43-fwcutter. b43-fwcutter exists in the Ubuntu repositories, but you will need a working wired Internet connection in Ubuntu in order to locate it and install it.
 
Do this in a terminal:

sudo aptitude update
sudo aptitude install b43-fwcutter

I would suggest shutting the computer completely down after running these commands and then rebooting.  

Let us know how this works.

Regarding the Realtek ethernet problem:  

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)  (See Post #1 and follows instructions)

MarshaG.

---

### Post by colobix on 2010-02-13
Ah that one is easy.
Synaptic has the B43-fwcutter driver.
Just go to System>admin>synaptic package manager and search for B43-fwcutter, and there u go.

---

### Post by kron00 on 2010-02-13
Found a tutorial to get b43-fwcutter installed with no net connection, now working perfectly :p

Thanks for all your help.

I just need to get my sound working then everything should be working great

But, as i mentioned earlier, both my CPU & graphics fans are running at 100%, how can i get ubuntu to dynamically change the rpm depending on load/heat like windows?

---

