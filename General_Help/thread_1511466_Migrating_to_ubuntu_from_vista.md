---
title: "Migrating to ubuntu from vista"
date: 2010-06-16
forum: General Help
---

### Post by 987a654 on 2010-06-16
Hi

I am moving from vista to ubuntu 10.04 and this is the process I am following.

1 Clone my vista partition.

2 Backup the following data

[INDENT][LIST]
[*]Zimbra email accounts

[*]back up of my user account (where all my data is)
[/LIST]
[/INDENT]
3 Use gparted to create three partitions (it's a 80GB drive)
[INDENT]
[LIST]
[*]10GB for ubuntu root
[*]30Gb for Home
[*]40Gb to restore vista back
[/LIST]

I do not want a SWAP partition as I have 4GB of RAM. and if I need it in the future I can always switch it back on. Right?
[/INDENT]
4 Install Ubuntu 

5 move my data to Ubuntu - this is where I need some help. What is the best way to move my data to Ubuntu form vista?

I mostly use my system for surfing net, email, VOIP, watching TV, and some low level programming. 

It is a DELL m1210 laptop with intel C2D, nvidia gpu, and 4GB ram. 

I tried the live disk and found my system to be very stable. Only bluetooth is not working. How hard is it to get it working because I have a bluetooth headset which I use a lot.

I have an external monitor and I was able to use it in dualview mode when using the live disk. Everything seems ok and do I really need the nvidia restricted graphics driver?

Thank you
Yudi

---

### Post by ba_saish on 2010-06-18
hi copying data from vista to ubuntu is really easy, once you have installed ubuntu, you can  mount the vista partition in the ubuntu and copy the data to ubuntu. Mounting is also pretty easy generally, you just have to select he parition you want to mount from the places menu in the menu bar.

---

### Post by jarviser on 2010-06-18
You don't say exactly when you plan to install/clone the Vista but I would do it between steps 3 and 4. Make sure Vista boots, do any adjustments and shut down. 
Then run the install of Ubuntu from the CD. Grub should detect Vista and add it to the boot list.
When asked, select the Manual partition (Advanced) path to mount your partitions to / and /home and don't specify swap. It should ask for confirmation.

Installing/repairing Windows after Linux installation usually screws the grub boot in my experience.

---

### Post by marshmallow1304 on 2010-06-18
> **987a654 said:**
> 
I do not want a SWAP partition as I have 4GB of RAM. and if I need it in the future I can always switch it back on. Right?

Yes, though one inconvenience is that you won't be able to hibernate (suspend to disk) since the Swap partition is used to store the contents of RAM.

> **987a654 said:**
> I have an external monitor and I was able to use it in dualview mode when using the live disk. Everything seems ok and do I really need the nvidia restricted graphics driver?

You don't really need the restricted driver unless you need 3D acceleration for desktop effects (compiz) or games.

---

### Post by 987a654 on 2010-06-18
thanks for the replys guys.

i have a dualboot system now.

10gb sda1 - / 
35gb sda2 - /home
35gb sda3 - vista

was able to trim vista down to 28gb, resized and moved it to the end using gparted. repaired the boot record using vista repair disk. Installed ubuntu. went really smooth. 

By leaving vista on the disk I was able to use ubuntu migration assist. This was what I was lookin for. Copying manually is tedious and outdated.  I keep all my files in sub directories in my user account, especially documents, music, pictures. All these were copied over with out any glitch. 

Pretty happy. I wish there was a tool to do the same after install. 

The only thing thats not working is the Bluetooth. Any suggestions?

I do not use hibernation often, but if I really need I will switch SWAP on. That should not be an issue. So far Ubuntu has not even used 1GB ram.

I am very glad everything went so smooth.

Thanks once again.
yudi

---

### Post by ankit singh on 2010-06-18
install blueman bluetooth manager from System>Admin..>Synaptic  search for blueman and install it, everything will be fine

---

