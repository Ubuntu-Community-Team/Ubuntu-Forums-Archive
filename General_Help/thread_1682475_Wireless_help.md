---
title: "Wireless help"
date: 2011-02-05
forum: General Help
---

### Post by mc228608 on 2011-02-05
Trying to set up my wireless connection and I have no means of Internet access so I found my Card\Driver jazz with :
  lspci -vvnn | grep 14e4
   
  -which gave me the following::
   
  04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
   
  Using this I went to [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) Downloading the firmware files, i loaded them to a flashdrive and put them on the computer that i need to fix, then load the iles to the HomeFolder. However i pretty new to the terminal sys. On Ubuntu so i need help with the following command list
  b43-fwcutter is located on the Ubuntu install media under **[FONT=&quot]../pool/main/b/b43-fwcutter/[/FONT]** and patch is located under **[FONT=&quot]../pool/main/p/patch/[/FONT]** **[FONT=&quot]or[/FONT]** both in the official repositories online. 
  Double click on the package to install **[FONT=&quot]or[/FONT]** in a **[FONT=&quot]terminal[/FONT]** (under the desktop menu **[FONT=&quot]Applications > Accessories > Terminal[/FONT]**) navigate to the folder containing the package and issue the following command: 
  **[FONT=Courier]:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*[/FONT]**
   
  when I enter the command I get 
  bash: :/b43-fwcutter/$: No such file or directory
    So what folder do I need to navigate to/how? 
  I'm really getting confused 
   
  This is all info that I have retrieved from Ubuntu,
  and in an abstract heres what I'm doing:
  “If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch packages from the install media. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up).”

---

### Post by DanneStrat on 2011-02-06
You have a "broadcom BCM 43XX" card which is supported

"out of the box". The broadcom drivers are "restricted" drivers and 

cannot be packaged with ubuntu. All you have to do is

Go to: System > Administration > Hardware drivers

There you should have a "broadcom b43" driver.

Just activate it there and the necessary packages will be downloaded.

Now reboot your computer and try to connect.

Good luck!;)

---

### Post by DanneStrat on 2011-02-06
> This is all info that I have retrieved from Ubuntu,
and in an abstract heres what I'm doing:
“If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch packages from the install media. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up).”

Basically when you do what I mentioned above,

what is really happening is that the "b43-fwcutter"

package is being installed to make your broadcom card work. 

It is also possible to install it from synaptic.

Hope this made it a little easier.;)

---

### Post by TBABill on 2011-02-06
I believe the optimal driver for the BCM4311 is the STA (wl) driver, not the b43. Have you installed the driver and the firmware already? If you have, can you try ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` and then do ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and enter the following to the end of the file ```
blacklist b43
blacklist ssb
blacklist b43legacy

``` Then restart the computer and see if it's up and running.

---

