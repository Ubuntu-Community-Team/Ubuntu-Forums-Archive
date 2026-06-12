---
title: "Keeping driver software"
date: 2011-07-07
forum: General Help
---

### Post by Waff1es on 2011-07-07
Hey guys!

First I want to say that this the first time I am using Ubuntu as my primary operating system (w/ Win 7 on the side for comfort). After 3 years of Uni. CS and now a co-op term where all I use is Linux, I thought it was time to embrace my inner programmer :P. 

Anyways, I am living in student housing right now and the only source of Internet is wireless. Unfortunately I was suffering from chicken and egg scenario where I needed to download drivers from the Internet to get my wireless up and running in order to access the internet. After hours of running around town a friend offered their hard connection  so I could download the drivers. I am a big fan of reformatting so there is an obvious issue each time as I need to find a hard connect in order to download the driver.

Is there a way to extract the driver and store it in a storage device so that next time I reformat I can install the driver from off the disk instead of downloading it? I used Additional Drivers instead of downloading the driver package from the web. Is it as easy as copying a folder (I assuming not but its nice to dream)?

Ideas, help?

---

### Post by coldraven on 2011-07-08
I'm not sure about the hardware drivers but packages you download with the Software centre are kept here /var/cache/apt/archives
If you open Nautilus (the file manager) press Ctrl+L and you can paste that path straight in.
I've lost the link to Ububtu packages online but this one is handy [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Edit: If you know the package name this might be a good link [URL="http://packages.ubuntu.com/"]http://packages.ubuntu.com/
[/URL]

---

### Post by coldraven on 2011-07-08
HaHa! I've done some investigating and found this out.
Open System>Admin>Synaptic Package Manager.
Click on the "Installed" section in the left pane.
Click on the "Search" icon on the top right.
I have a Broadcom card so I entered "Broadcom"
Then on the search result, right click and select "Properties"
Voila! That is the name of the package, see the screenshot.

---

### Post by Waff1es on 2011-07-08
I will definitely try it out when I get home from work. Keep you posted if it works for me or not.

---

### Post by coldraven on 2011-07-09
While I think of it, a useful tool is "lshw". It lists your hardware!
If you open a terminal (Ctrl+Alt+T) and do this
```
sudo lshw
```
The "sudo" part gives you temporary root access, that's why it will ask for your password.
You will get all the info for your machine, but if you do this instead
```
sudo lshw >my_hardware.txt
```
It will send the output to a text file in your home folder which you can keep for future reference.
Just double click the file to open it in a text editor.

---

### Post by Waff1es on 2011-07-09
Kind of off topic but since you brought up sudo, Ubuntu doesn't support the "su" command right?

---

### Post by Waff1es on 2011-07-09
So I just search for that software package, download it and store it for later?

(It's weird, I have a Dell wireless card but have Broadcom drivers installed for it.)

Anyways, thanks for the help. Much appreciated!


Edit: Anyway to "thank you" or mark this thread as "answered" on the Ubuntu Forums?

---

### Post by spiky001 on 2011-07-09
Dont know if aptoncd is of any use for you?
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

---

### Post by coldraven on 2011-07-09
Have a think about it, Dell just buy from manufactures and assemble stuff. Have Dell ever invented anything?
If you do the lshw command as I suggested you will see something like this ```
*-network
                description: Wireless interface
                product: BCM4312 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:30:00.0
                logical name: eth1
                version: 02
                serial: 00:21:00:4f:c3:0c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:18 memory:c8000000-c8003fff
```Which will tell you everything you ever wanted to know about your wi-fi card.
If you have read enough then mark the thread as solved using the thread tools on the upper right side of the screen. Happy Ubuntuing :)

---

