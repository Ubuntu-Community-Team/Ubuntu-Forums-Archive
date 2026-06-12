---
title: "Linux Distro Issues."
date: 2011-04-08
forum: General Help
---

### Post by burntflowers on 2011-04-08
Hi,

I have been searching a while for a flavor of Linux to try before I settled on one but I have had nothing but problems. I recently had to format one of my desktops back into Windows 7 because Fedora 14 (Distro) had an issue I couldn't resolve that it just randomly locked up whenever it wanted. I had a majority of issues with software under Wine. 

I have tested all the hardware and its reporting back fine, it does not overheat as the computer had one of those hydrocool units from corsair the hottest it gets is 32c at full load. The memory tested fine. I have asked people who used Fedora and they claim it is my computer not the distro. 

I have very little experience with Linux, each distro is on it's own and before I go and format my computer again which if I do I want it to be the last time. I am hoping to get some help/information from users of Ubuntu because I would rather be spending my weekend getting the computer setup and running rather than keep researching which is better and driving myself a bit more crazy.

The computer specs are AMD x6 1090t, 8gb ddr3-1333mhz, 3 internal drives, 1x1tb, 2x2tb, rocketraid pci-e card to drive cage through esata connection, with onboard video. I don't sit in front of this computer often typically I would VNC into it if possible and if anything needed to be done I would do it from another machine in my house. basically the computer I want Linux on is a giant media server, anyone in the house can watch what they want off WDTV Live, or gaming console. The only problem is Windows Vista/7 has some issues with networking that Linux doesn't. That and I have to reboot that machine at least once daily because units will tell me the network cannot be accessed. Samba is a quick command line restart.

So which would benefit x32 or x64?. I know x32 has a PAE kernel. I would also need to install the -devel portion as well to compile drivers for at least one device. I have used the live CD and it did not freeze although their was not a lot I could do to force the machine to freeze up.  I run two maybe three apps under Wine. But before I completely redo the machine their are several drives that will be NTFS to EXT4. Also good support from people who can help a noob and be patient with me.

Any ideas to help a noob?

---

### Post by cottfcfan on 2011-04-08
I'd recommend Linux Mint 10 to start with. Its based on Ubuntu but with all the codecs preinstalled. Pretty Newbie friendly too.

---

### Post by dnguyen1963 on 2011-04-08
If you want a safe distro that would work on almost every computer (old and new) then try PCLinuxOS/Xfce.  Mint 10 is fine, but I would also recommend ArtistX.  This distro is also based on Ubuntu.  ArtistX comes with many software packages (great for newbie), which could be a plus or minus depending on your perception.

---

### Post by 3Miro on 2011-04-08
```
rocketraid pci-e card to drive cage through esata connection, with onboard video
```

What does that mean? Are you saying that you have setup a raid system trough the PCI-E slot and you are using the on-board ATI video?

Lockup like what you are describing are usually due to graphics. This is currently the weakest part of Linux. I have two machines with similar specs to you, but different video cards. The ATI one works great, but sometimes it will crash during YouTube videos. The Nvidia one, never crashes.

I am also not familiar with RAID, there may be an issue there too. RAID issues can be resolved with newer kernel. Fedora 14 uses the older kernel 2.6.35, Fedora 15 will use the newest 2.6.38. Latest Ubuntu 11.04 and Mint-Gnome will come with 2.6.38, however, Mint-XFCE comes with a very old one (2.6.32 I think). Fedora, Ubuntu and Mint are still in either alpha or beta stages. If you want something stable that comes with the latest kernel, you can give Arch a try (although setting up Arch is somewhat more challenging then Fedora).

---

### Post by burntflowers on 2011-04-09
> **3Miro said:**
> ```
rocketraid pci-e card to drive cage through esata connection, with onboard video
```What does that mean? Are you saying that you have setup a raid system trough the PCI-E slot and you are using the on-board ATI video?



I have a Sans Tower Array drive cage with 5 drives that can be configured as RAID 1,5,10 or JBOD, or the drives mounted separately, this, I have found this to be a lot easier than trying to stack drives inside a computer case if your going for storage. The unit itself comes with a PCI-E card that is configurable for building a raid array if people want too, personally,  I think this was designed for small businesses that want to do nightly back-ups.  [http://www.newegg.com/Product/Product.aspx?Item=N82E16816111139&cm_re=sans_tower-_-16-111-139-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111139&cm_re=sans_tower-_-16-111-139-_-Product) that is what I have. I don't use it as a RAID but the card is useful some motherboards (older) do not have eSata connections. Running raid over eSata would be horribly slow, and its not a *real* RAID I compare it to Windows that allows the OS "software" to configure drives in raid were you can combine disks together through disk management. I use each drive as a separate partition or mount points. Its nice if you want to drop heat out of your case. I have had this unit for almost 6 months, it has 5 2tb samsung f4's in it and works perfectly. 

And yes I am using the on-board video. I remote into the machine by putty or vnc if I need to use the graphical interface. the linux computer sits in another part of the house its designed to be something that shares via samba and maybe I can download a few things too, i'm typically in front of another computer most of the time. Intel Core I-7, that will be my next project for linux,  if I can get Linux running on the first machine, then I will start to change out all computers as well and be Windows free. I'm sick of rebooting, formatting and installing, running windows update that has another 800-1GB to download and install because of some crap malware/rootkit.

---

