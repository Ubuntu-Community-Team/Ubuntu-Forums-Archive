---
title: "Wired connection not working"
date: 2011-02-07
forum: General Help
---

### Post by mistavipa on 2011-02-07
Ok. I tried to install Ubuntu 10.10 with the live CD and it kept freezing at creating ext4 file system for /. I finally got it installed using the alternate cd method. Now, my internet connection is not working. I am connected to a router with DHCP. When I boot up with windows, everything works fine. Ubuntu says that I'm connected with a wired connection but I can't access anything on the internet. Any help would be appreciated. Please let me know if you need any more information.

---

### Post by mistavipa on 2011-02-07
Anyone??

---

### Post by ahsan101 on 2011-02-07
What is the status of eth0 in the Network connections, also which network manager are you using? I will say better to get wcid network manager, it works like a charm!

> 
anyone? 

Also, try to wait a bit while someone reads and answers. Hope you don't mind :) 

Tell me the final results.

---

### Post by mistavipa on 2011-02-07
> **ahsan101 said:**
> What is the status of eth0 in the Network connections, also which network manager are you using? I will say better to get wcid network manager, it works like a charm!



Also, try to wait a bit while someone reads and answers. Hope you don't mind :) 

Tell me the final results.

Ok. Forgive me for posting too quickly. I posted something before and no one ever responded so I just wanted it to go back to the top. I'm new to Ubunut and linux so I'm not sure how to check the network manager or the status. However, it says that wired connection is established. I can't even connect to my router using the 192.168.2.1 address. I type that in and it asks for the username and password and I type them in then it just sits there saying transferring data from 192.168.2.1...

---

### Post by amsterdamharu on 2011-02-07
Could you post the output of the following commands?

```
ifconfig -a
sudo dhclient eth0
lspci -v
```
for lspci we need the "Ethernet controller" part. 

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by mistavipa on 2011-02-07
Ok. I will try that however, how am I supposed to copy and paste if I can't access the internet on ubuntu? My internet only works when I boot windows.

---

### Post by mistavipa on 2011-02-07
Ok. Since I don't have internet access on Ubuntu, I took screenshots and saved them on my other drive. The commands will be posted here. Sorry about the inconvenience.

---

### Post by toolzen on 2011-02-07
It looks like you're getting a lot of frame errors. Have you tried using a different cable? Also, do you have a switch on your network, or are you going directly from the computer to a router?

---

### Post by mistavipa on 2011-02-07
> **toolzen said:**
> It looks like you're getting a lot of frame errors. Have you tried using a different cable? Also, do you have a switch on your network, or are you going directly from the computer to a router?

I have tried another cat5 cable with no change. No. I'm not using a switch. Cable modem to wireless router, wired to my computer. I have a laptop that is wireless.

---

### Post by josh6190 on 2011-02-07
Hey guys, just jumping in on the conversation here, It is very possible your drivers are not working. Might I suggest finding out the model of your network card and then with the help of fellow forumers to find the appropriate drivers? I know that drivers might not be the problem, but I think we should give it a shot.

---

### Post by mistavipa on 2011-02-07
> **josh6190 said:**
> Hey guys, just jumping in on the conversation here, It is very possible your drivers are not working. Might I suggest finding out the model of your network card and then with the help of fellow forumers to find the appropriate drivers? I know that drivers might not be the problem, but I think we should give it a shot.

It's an onboard card. If I use Windows XP Device Manager, I can see it's a SiS190 10/100 Ethernet Device. I'm willing to try just about anything to make it work. How does Ubuntu go about flash drives? Can I just plug it in the USB port and mount the drive? Will it recognize it? Where can I get the Linux drivers for this card? Thank you all for your help!

---

### Post by josh6190 on 2011-02-08
@[mistavipa]("http://georgia.ubuntuforums.org/member.php?u=1239197") , ok we are on to something, all we need to do is get the drivers, I will start searching for them and post a link if I find a page. Is there a manufacturer brand-name? That might help. Anyways, I'll post anything new I see in future.

---

### Post by mistavipa on 2011-02-08
> **josh6190 said:**
> @[mistavipa]("http://georgia.ubuntuforums.org/member.php?u=1239197") , ok we are on to something, all we need to do is get the drivers, I will start searching for them and post a link if I find a page. Is there a manufacturer brand-name? That might help. Anyways, I'll post anything new I see in future.

Like I said, its an sis onboard card. Silicon Integrated Systems. I took a screenshot of my windows device manager with the card in it.

---

### Post by josh6190 on 2011-02-08
Ok try this [http://www.linuxforums.org/forum/coffee-lounge/43477-sis-190-driver-linux.html](http://www.linuxforums.org/forum/coffee-lounge/43477-sis-190-driver-linux.html)

this was forums disccussion on linux forums regarding the sis 190. I havent had a chance to read through the whole thread though. When I get more time I will try to post a link to the driver with the instructions for you later today.

---

### Post by mistavipa on 2011-02-08
> **josh6190 said:**
> Ok try this [http://www.linuxforums.org/forum/coffee-lounge/43477-sis-190-driver-linux.html](http://www.linuxforums.org/forum/coffee-lounge/43477-sis-190-driver-linux.html)

this was forums disccussion on linux forums regarding the sis 190. I havent had a chance to read through the whole thread though. When I get more time I will try to post a link to the driver with the instructions for you later today.

Cool. Thanks alot. I'm gonna look through it and see what I can find.

---

### Post by josh6190 on 2011-02-08
Ok, a little bit later today I will post a link to the driver if I can find it so stay tuned!

---

### Post by josh6190 on 2011-02-08
[http://www.sis.com/download/download_step1.php](http://www.sis.com/download/download_step1.php)

Okay heres the drivers! These are some instructions in how to compile the driver, this could be anpther challenge on its own though. I dont know what this really means but here it is


In the "Readme" text :


1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)

2. Download Linux kernel 2.6.9 or latter version from [http://www.kernel.org](http://www.kernel.org). The follwing examples are based on linux-2.6.9.

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
will be called sis190. This is recommended.

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

---

### Post by mistavipa on 2011-02-08
> **josh6190 said:**
> [http://www.sis.com/download/download_step1.php](http://www.sis.com/download/download_step1.php)

Okay heres the drivers! These are some instructions in how to compile the driver, this could be anpther challenge on its own though. I dont know what this really means but here it is


In the "Readme" text :


1. Install Fedora Core 3. (Currently only FC3 can be installed on 965 demo board.)

2. Download Linux kernel 2.6.9 or latter version from [http://www.kernel.org](http://www.kernel.org). The follwing examples are based on linux-2.6.9.

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
will be called sis190. This is recommended.

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

I looked up the kernel version 2.6.9 or later and only saw 2.6.37 as the latest. If thats the latest kernel, how can i get a 2.6.9? And what is Fedora Core 3 and where can I get it?

---

### Post by mistavipa on 2011-02-09
Ok. I tried the above steps using the most current, stable, kernel, 2.6.37. I got up to the step of using ```
make menuconfig
``` and this is my result.

---

### Post by amsterdamharu on 2011-02-09
The make and model of the card and the drivers it uses was posted before as output of lspci -v command.

The sis190 driver that is in use has many posts but can't find frame errors as one of them. There are also threads that are fixed so it can't be the driver. I see somewhere that that driver didn't work with a kernel used in 9.04 64 edition.

One thing to try is the following:
Try the following commands:
```
sudo ifconfig eth0 mtu 1492
ping google.com
ifconfig -a

```

You can copy and paste into a text file (press alt + f2 type gedit and click run). That's easier to read than print screens.

---

### Post by mistavipa on 2011-02-09
> **amsterdamharu said:**
> The make and model of the card and the drivers it uses was posted before as output of lspci -v command.

The sis190 driver that is in use has many posts but can't find frame errors as one of them. There are also threads that are fixed so it can't be the driver. I see somewhere that that driver didn't work with a kernel used in 9.04 64 edition.

One thing to try is the following:
Try the following commands:
```
sudo ifconfig eth0 mtu 1492
ping google.com
ifconfig -a

```You can copy and paste into a text file (press alt + f2 type gedit and click run). That's easier to read than print screens.

Well this seemed to work. I've got internet now. :). Thanks much guys!!

---

### Post by josh6190 on 2011-02-09
Your welcome. I can't say I've done much in the past while...but regardless, glad that you are on the internet and it is working well!

---

