---
title: "Help on installing ubuntu"
date: 2009-07-14
forum: General Help
---

### Post by atulbamne on 2009-07-14
Dear Community,

This may be a very simple question, but i dont want to proceed un-informed about it.

I have a Dell branded PC Core2deo 2.8 with 2 GB RAM with Vista preloaded. The present partitions are 150 GB(OS) and 2 GB(receovery). I want to install ubuntu on my PC. The questions is how should i go? which will be better option? 

Shall i install ubuntu by making a dedicated partition by vista on my c drive? or i may ask ubuntu CD to make such partition? which one is better option if i want to use ubuntu with full advantages like graphics and speed? My colleague uses vista so i will keep it for him.

Please help..

---

### Post by nothingspecial on 2009-07-14
It makes no difference what you use to create the partitions.

Just make sure you install ubuntu to the right one.

And defrag your windows before you partition.

---

### Post by coffeecat on 2009-07-14
But it does matter what you use to shrink your Vista C: partition.

You will need to shrink your Vista partition so that there is some unallocated space on the hard drive in which the Ubuntu installer can create the partitions needed for Ubuntu. **Do not use the Ubuntu partitioner to shrink the Vista partition**. You risk making Vista unbootable if you do. Use the [Vista resizing tool]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") to shrink the Vista partition, and then boot up from the live Ubuntu CD, start the installer and under 'guided' choose 'use unallocated/free space' (or something like that - I'm going from memory).

[More information about shrinking a Vista partition]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"). See under 'Using Linux to Resize' for what may happen if you do.

**Edit:** by the way, if you use Vista to make partitions, it will make NTFS (a Microsoft filesystem) ones, which are not suitable for Linux. You need a Linux filesystem such as ext3 for your Ubuntu root partition. And you'll also need a separate swap partition with its own special filesystem. Use the partitioner in the Ubuntu installer as above and you should be OK.

---

### Post by lisati on 2009-07-14
I think coffecat's experience was different to mine: I had the opposite problem, sort of - I wasn't able to use Vista's partitioner to shrink its partition (possibly from unfamiliarity) and ended up using Ubuntu's partitioner to do the job, which, other than taking several hours to resize a 140Gb partition, worked flawlessly.

My own preference is to use the partitioner of choice to free up some space (say, for example, 10-20 Gb), and to tell the Ubuntu installer to use the "Guided - use the largest continuous free space" option. 

Either way, it's always a good idea to make backups of important data, and to defrag your Windows partitions a few times before making changes to your system.

---

### Post by coffeecat on 2009-07-14
> **lisati said:**
> I think coffecat's experience was different to mine:

Actually, I didn't directly experience this business of Gparted making Vista unbootable - I'd already been forewarned by posts all over this forum and on other parts of the web about this problem. But the Vista resizing tool is very inadequate. See my second link above for all the gory details.

I can't remember the details, but this Vista unbootable-after-Gparted business is something to do with partition boundaries and cylinders. You must have been one of the lucky ones. It seems that many people's experience is something like this:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Which is fine if you've got a proper MS Vista install DVD to repair Vista, but most people only have an OEM image disk or, more likely, just a restore partition, neither of which will do at all.

---

### Post by lisati on 2009-07-14
> **coffeecat said:**
> Actually, I didn't directly experience this business of Gparted making Vista unbootable - I'd already been forewarned by posts all over this forum and on other parts of the web about this problem. But the Vista resizing tool is very inadequate. See my second link above for all the gory details.

I can't remember the details, but this Vista unbootable-after-Gparted business is something to do with partition boundaries and cylinders. You must have been one of the lucky ones. It seems that many people's experience is something like this:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Which is fine if you've got a proper MS Vista install DVD to repair Vista, but most people only have an OEM image disk or, more likely, just a restore partition, neither of which will do at all.
Good point, my bad. Now that I think back, I vaguely remember Vista complaining some time about something being missing, which was easily fixed (almost without thinking) using a recovery DVD I'd made from the recovery partition when I first purchased the computer. I hadn't made the connection at the time.

---

### Post by atulbamne on 2009-07-15
Thanks for giving timely help. I have created a new partition and installed ubuntu on new partition using option " install inside Windows". It is working perfectly..

Thanks for your time and consideration.....

---

### Post by coffeecat on 2009-07-15
> **atulbamne said:**
> I have created a new partition and installed ubuntu on new partition using option " install inside Windows".

**atulbamne**, it sounds as though you have used Wubi to install Ubuntu. All the previous posts were giving advice on the assumption that you were going to do a standard Windows/Ubuntu dual-boot with Ubuntu on its own native partition with a Linux filesystem. The two methods are fundamentally different. Wubi is fine, but has its own limitations, one of which is that Ubuntu will run slower than in a native install.

If you find all that baffling, or need any more information, just post back.

Enjoy your Ubuntu!

---

### Post by atulbamne on 2009-07-15
Actually I did not want to take any risk of loosing windows. I am very new to the Linux World. Anyway, thanks for your advice. If you have some more time to spend on my PC, can you tell me how do install network? I have Intel 82567-LM3 network card. I have downloaded intel e1000e linux driver from intel website but do not know how to install it. My ubuntu is not showing network.

---

### Post by 3rdalbum on 2009-07-15
> **atulbamne said:**
> Thanks for giving timely help. I have created a new partition and installed ubuntu on new partition using option " install inside Windows". It is working perfectly..

EDIT: Found your later post, Wubi was what you wanted.

Just thought you should be aware that if your Windows partition becomes corrupted, then you might not be able to access Ubuntu.

---

### Post by coffeecat on 2009-07-15
> **atulbamne said:**
> can you tell me how do install network? I have Intel 82567-LM3 network card. I have downloaded intel e1000e linux driver from intel website but do not know how to install it.

I presume that's an Intel ethernet network device. If so, you don't need to download or install anything. The drivers are already there in the installation; they are part of the kernel or are loadable kernel modules. If everything's gone OK with the installation, your hardware will be autodetected and everything will "just work".

With an ethernet connection, if you've got your ethernet card connected to a working router, it should simply connect automatically. If not, have a look on top gnome panel, near to the right of the screen, for the Network Manager icon. Right-click on it and make sure "Enable Networking" is ticked. If it is, click on "Connection Information" and see what that says. You could already be connected without knowing it.

---

### Post by 3rdalbum on 2009-07-15
> **atulbamne said:**
> Actually I did not want to take any risk of loosing windows. I am very new to the Linux World. Anyway, thanks for your advice. If you have some more time to spend on my PC, can you tell me how do install network? I have Intel 82567-LM3 network card. I have downloaded intel e1000e linux driver from intel website but do not know how to install it. My ubuntu is not showing network.

According to what I've read, the driver should already be preinstalled in Ubuntu 9.04. Is Network Manager (one of the icons at the right of your top panel) showing your card? Is it showing a little picture of an Ethernet cable and a cross?

---

### Post by atulbamne on 2009-07-16
Dear 3rdalbum and coffeecat,

Thanks for your useful advice. 

Sorry I am little late at replying. After not getting network to my PC, i started searching google and found that there is a specific Linux Base driver avilable on intel site called e1000e driver. I was not having any idea of installing the driver. Then somehow i could install the driver and my PC is connected to network now. However, still my problem is not solved. I have my PC on LAN internet for which i have to enter IP address/DNS/Gateway and all. I dont know how to do that. I have one advice to insert the same through VIM but i dont have VIM on my PC. i cant download anything directly as no net. Driver also I downloaded on another PC and then copied on my Ubuntu.

Please advice me easiest way to enter network things like IP/DNS/Gateway so that i will connect to net and update my ubuntu.

---

### Post by atulbamne on 2009-07-20
Dear all who have helped me in this issue,

Finally i could install driver for my network card and now ubuntu is working like a charm !

Thanks all for your support, Sirs...

---

