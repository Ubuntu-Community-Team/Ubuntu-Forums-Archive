---
title: "Will I lose my raid array if I reinstall Ubuntu?"
date: 2011-06-21
forum: General Help
---

### Post by Roasted on 2011-06-21
So I've been having some issues with my Ubuntu install ever since I put in the Gnome 3 PPA to use Gnome Shell... to the point that I'm putting Ubuntu/XFCE on my critical boxes and Fedora 15/Gnome Shell on my laptops and stuff I want to use Gnome Shell on, since Ubuntu is clearly not there yet with supporting it (come on, 11.10 supporting Gnome 3 out of the box...) I'm doing this since the PPA purge, while it removed Gnome 3/Shell, I'm still getting a little weirdness... I'd rather just do a fresh install and stop tinkering with it for now.

Anyway, here's my setup:

250gb SATA - OS/Ubuntu 
1TB SATA - Raid 1 via mdadm
1TB SATA - Raid 1 via mdadm

if I format and reinstall Ubuntu on the 250gb drive, would I lose my array or will I be able to select the array to mount as my home directory when I do advanced partitioning?

---

### Post by qx48 on 2011-06-28
I've run into a similar problem. 

I like the idea of the Gnome 3 (shell) interface, but it isn't yet exactly the most seamless UI integration with Ubuntu I've ever used, to say the least.

I am also looking to reinstall another OS onto this machine (Probably Mint 11) until the shell is ready, but I don't want to jeopardize the data in my mdadm-configured RAID5 array. I would also rather not have to rebuild the array, since something about my setup made it rather difficult the last time around, not to mention the time it would take to transfer ~1TB of data off and back on. Hopefully there's a way to maintain the integrity of the array while reinstalling the OS (which is on a completely different HDD).

While I am not at all an expert on how mdadm facilitates the software raid configuration, it would make sense that (since it is *software* raid) that reinstalling the OS upon which all other software is based would also cause the mdadm software mechanisms that maintain the integrity of the array to be lost as well. That is unless the information in mdadm.conf (or a similar object) is saved on the array itself and can be used by grub or an OS installation client to correctly identify the array. However, it's also quite probable that I'm missing something else entirely. 

If anyone knows something about this type of issue, I would also appreciate any information or advice on how to proceed.

---

### Post by Roasted on 2011-06-28
Well, I kind of had a borked install of Ubuntu and Gnome Shell. Long story short, I just reinstalled Ubuntu and put Gnome Shell back on. You see, I have 3 systems, and 2 of them were acting up with Gnome Shell, so I thought it was Gnome Shell. Turns out my laptop had a bad hard drive (which I only figured out after Mint 11 and Fedora 15 duplicated the same results) and my desktop had a corrupt install from a CD that was verified to be problematic (take notes, kids. check your CD PRIOR to installing... not AFTER you have problems).

I'm back on Ubuntu with the Gnome Shell PPA and it seems to be working fine.

HOWEVER: About the RAID thing, just to recap I'm using Raid 1 with MDADM in Ubuntu 11.04. I installed Ubuntu and fired it up and, no raid. Crap! But on a hunch I just did an apt-get install mdadm and sure enough, it installed it. I thought it was pre-installed? Regardless, I rebooted then and bingo bango - my array was there working beautifully, just like that.

I just had to get the UUID of the array and mount that as my home directory. One more reboot later I was back in business.

A user in the Ubuntu chat said that's the one beauty of software raid in Linux. I can take the raid drives out and drop them in any Linux box. Once MDADM is installed and you reboot, you can retrieve any data you need to, as opposed to hardware raid where, say, your hardware controller dies and... dum dum dum..... bye data.

I'm diggin this software raid in Linux. It truly wasn't hard to set up, and it seems very versatile...

---

### Post by txducker on 2011-06-29
Thanks for following up with the RAID information. I just installed a RAID 1 for my backup data and this answers some questions I had. I have had a difficult time finding information out about linux software raid.


> **Roasted said:**
> 
HOWEVER: About the RAID thing, just to recap I'm using Raid 1 with MDADM in Ubuntu 11.04. I installed Ubuntu and fired it up and, no raid. Crap! But on a hunch I just did an apt-get install mdadm and sure enough, it installed it. I thought it was pre-installed? Regardless, I rebooted then and bingo bango - my array was there working beautifully, just like that.

I just had to get the UUID of the array and mount that as my home directory. One more reboot later I was back in business.

A user in the Ubuntu chat said that's the one beauty of software raid in Linux. I can take the raid drives out and drop them in any Linux box. Once MDADM is installed and you reboot, you can retrieve any data you need to, as opposed to hardware raid where, say, your hardware controller dies and... dum dum dum..... bye data.

I'm diggin this software raid in Linux. It truly wasn't hard to set up, and it seems very versatile...

---

### Post by Roasted on 2011-06-29
> **txducker said:**
> Thanks for following up with the RAID information. I just installed a RAID 1 for my backup data and this answers some questions I had. I have had a difficult time finding information out about linux software raid.

I think the part I got messed up on was I did my original install from the alternate CD, which of course has the capability of configuring RAID right there, whereas the LiveCD does not. This time around, I redid my OS install from the LiveCD, however my array was still intact on the two target drives. That's where I got confused. LiveCD = no mdadm. Alternate CD = mdadm.

That's why when I booted up, I had no raid. A quick install and edit to fstab later and I was in business with my home directory mirror. :guitar:

---

