---
title: "W inside Ubuntu"
date: 2011-02-26
forum: General Help
---

### Post by rva1945 on 2011-02-26
OK, I got tired of having to boot in Windows XP to run a couple of apps that don't run in Wine.

I've heard a bout a virtual machine, virtualbox and all of that. Sorry, I need a crash course. What do I need to download/install?

Do I need a WXP live CD or something like that?

PLS HLP

Thanks

---

### Post by seawolf167 on 2011-02-26
Open a terminal 

Applications -> Accessories -> Terminal

```
sudo apt-get install virtualbox
```

or search through the software center for virtualbox. It'll be in your menu items Applications -> System Tools -> VirtualBox

Once it installs, it'll prompt you through installing a new OS, you'll need your Windows install media (either a cd/dvd or .iso image on your computer).

You'll then be able to install Windows inside the virtualbox just like normal

---

### Post by Jetso on 2011-02-26
It is a pretty simple process. Once you get Virtual Box, you make the virtual hard drive, then you boot it with the CD of XP in your tray or whatever and install it like you would a real computer.

---

### Post by Yellow Pasque on 2011-02-26
Just a warning: If you're trying to run games, you'll probably be disappointed in the video performance.

---

### Post by rva1945 on 2011-02-26
> **Jetso said:**
> It is a pretty simple process. Once you get Virtual Box, you make the virtual hard drive, then you boot it with the CD of XP in your tray or whatever and install it like you would a real computer.

Thanks, I just installed from Virtualbox OSE. Seems as if I have to follow the wizard to create a new machine, right?

How much disk space do I need?

I have a Wxp boot and installer CD, not ISO or live CD. Wil I have to run an installation inside the machine, that's the idea?

---

### Post by rva1945 on 2011-02-26
> **seawolf167 said:**
> Open a terminal 

Applications -> Accessories -> Terminal

```
sudo apt-get install virtualbox
```or search through the software center for virtualbox. It'll be in your menu items Applications -> System Tools -> VirtualBox

Once it installs, it'll prompt you through installing a new OS, you'll need your Windows install media (either a cd/dvd or .iso image on your computer).

You'll then be able to install Windows inside the virtualbox just like normal

Done the iso image of the WXP install cd

robert@rvasystem:~$ dd if=/dev/cdrom of=winxp.iso
1265748+0 records in
1265748+0 records out
648062976 bytes (648 MB) copied, 182.163 s, 3.6 MB/s
robert@rvasystem:~$ 

now where is it? How do I tell Virtualbox where to find it?

---

### Post by Jetso on 2011-02-26
If your using XP for games and on;y some applications. I would suggest 10gb. Dynamically Expanding is the best choice.

---

### Post by rva1945 on 2011-02-26
> **Jetso said:**
> If your using XP for games and on;y some applications. I would suggest 10gb. Dynamically Expanding is the best choice.

Well I had to aborty the installation because I didn't have the Windows XP key.

I deleted the machine and created a new one. I couldn't create a new hard disk because the one I previously created exists, well, I used that, but now the install doesn't launçch from the beginning, the previous installation resumes. I want a new one (professional XP instead of Home edition).

I can I delete the hard disk to create a new one?

---

### Post by seawolf167 on 2011-02-26
[VirtualBox's documentation]("http://www.virtualbox.org/manual/ch01.html#gui-createvm") has a step-by-step guide to installing, running and using a virtual machine.

---

### Post by seawolf167 on 2011-02-26
> **rva1945 said:**
> I can I delete the hard disk to create a new one?

There is a Virtual Disk Manager where you can add/delete/modify your virtual disks. [Here]("http://www.screenshots-archive.com/virtualbox-virtual-disk-manager") is a screenshot of it. Just delete your old one[s], then the easiest way to make a new on is to simply follow the wizard when creating a new virtual OS.

There is also a section for OS images where you can mount or unmount your install disks to be used/accessible from VirtualBox

---

### Post by rva1945 on 2011-02-26
> **seawolf167 said:**
> There is a Virtual Disk Manager where you can add/delete/modify your virtual disks. [Here]("http://www.screenshots-archive.com/virtualbox-virtual-disk-manager") is a screenshot of it. Just delete your old one[s], then the easiest way to make a new on is to simply follow the wizard when creating a new virtual OS.

There is also a section for OS images where you can mount or unmount your install disks to be used/accessible from VirtualBox

WELL THANK YOU GUYS I just installed my first VM. It runs fine, and connects to the Internet without configuring anything.

Question: everytime I start the VM it asks for pressing any key to boot from CD, then after a few seconds Windows starts ok. That's because the CD is "virtually inserted" as the iso image?

---

### Post by Jetso on 2011-02-26
Yes, it is because the .iso is mounted virtually. I beleive their is a way to unmount at the top, but I haven't used VB in a while and I don't have it anymore

---

### Post by seawolf167 on 2011-02-26
> **rva1945 said:**
> Question: everytime I start the VM it asks for pressing any key to boot from CD, then after a few seconds Windows starts ok. That's because the CD is "virtually inserted" as the iso image?

Look around in the settings - I think its something like "media manager" or "disk images" or similar. Its essentially the same layout as the drive manager layout, you select the media that you used to install (i.e. your Windows .iso file), and then click to select, and remove it. Then since it isn't being virtually mounted, you won't have that boot option.

---

### Post by rva1945 on 2011-02-26
WXP in the VM connects to Internet God knows how. I didn't configure any internet connection, in IE options, Connections, there is none, in LAN settings, nothing, no automatic detection, no nothing. And if I disable networking in Ubuntu so I can't navigate, then I launch the VM and start the Wxp, I can navigate, which connection is it using? I have ADSL model connected to the Ethernet via a RJ45 wire. In the Wxp partition (that ceased to work), I had to click the ADSL connection to connect to the Internet.

Thanks

---

### Post by seawolf167 on 2011-02-26
VirtualBox uses something called NAT to create its connections from the host to the virtual machine. You can read more about it [here]("http://www.virtualbox.org/manual/ch06.html"). As long as you don't change the default settings, your virtual machine will keep receiving your inbound internet connection until you disable the adapter on the host (or change the VBox network settings)

---

### Post by gerowen on 2011-02-26
I recommend using the version of virtualbox you can download from Oracle's website.  Last time I tried, the version in the Ubuntu repos did not include the "Guest Additions" ISO.  When you install the guest additions it allows you to move your mouse from the guest os to your host os without using key combinations to lock/unlock your mouse.  You can put the guest OS into "Seamless" mode where the taskbars and stuff from it appear on your host OS desktop.  The version in the repos works just fine, it's just that it doesn't include those "Guest Additions" drivers.

---

