---
title: "Running Ubuntu in Windows for Secure Internet?"
date: 2011-06-20
forum: General Help
---

### Post by Metalious on 2011-06-20
As the title says, I need to know if I can run Ubuntu inside the Windows environment and use it to connect to the internet securely while leaving Windows offline.

I have come to the point where I simply don't trust Windows to even access the internet. I still use it though for audio production. So I am wondering, specifically, if I can disable Windows network completely, including not instaling drivers for my nic card, and use Ubuntu to go online.

Currently, I have a dual boot setup but this is a constant pain as I have some apps that run in Windows only. So switching back and forth all the time is tedious.

---

### Post by haqking on 2011-06-20
> **Metalious said:**
> As the title says, I need to know if I can run Ubuntu inside the Windows environment and use it to connect to the internet securely while leaving Windows offline.

I have come to the point where I simply don't trust Windows to even access the internet. I still use it though for audio production. So I am wondering, specifically, if I can disable Windows network completely, including not instaling drivers for my nic card, and use Ubuntu to go online.

Currently, I have a dual boot setup but this is a constant pain as I have some apps that run in Windows only. So switching back and forth all the time is tedious.


you can run a live CD or install Ubuntu or any other distro into a Virtual Machine and do your browsing from there.

I always carry a DSL (damn small linux) around on a USB drive to do that when i am on other peoples machines for secure browsing

---

### Post by Monotoko on 2011-06-20
If it's just audio production and your computer is powerful enough to do a virtual machine, why don't you use Linux natively and put Windows in a virtualbox?

---

### Post by Metalious on 2011-06-20
> **Monotoko said:**
> If it's just audio production and your computer is powerful enough to do a virtual machine, why don't you use Linux natively and put Windows in a virtualbox?

Not sure what you mean by "just audio". Depending on the song, I can just about bring any system to its knees. lol. I really only need Ubuntu to surf the net. So I would rather have my production apps running natively. Even though I prefer Ubuntu to Windows in every respect.

---

### Post by Metalious on 2011-06-20
> **haqking said:**
> you can run a live CD or install Ubuntu or any other distro into a Virtual Machine and do your browsing from there.

I always carry a DSL (damn small linux) around on a USB drive to do that when i am on other peoples machines for secure browsing

Thnks haqking. Just to confirm, is the VM your talking about Wubi or whatever I saw under "options" when I installed Ubuntu (I seem to remember seeing an option to install inside Windows)?

And is my XP install secure when surfing through a VM of Ubuntu?

Thanks again for the info.

---

### Post by haqking on 2011-06-20
> **Metalious said:**
> Not sure what you mean by "just audio". Depending on the song, I can just about bring any system to its knees. lol. I really only need Ubuntu to surf the net. So I would rather have my production apps running natively. Even though I prefer Ubuntu to Windows in every respect.

VMware or Virtual Box and set up a virtual machine.

Done ;-)

---

### Post by Metalious on 2011-06-21
> **haqking said:**
> VMware or Virtual Box and set up a virtual machine.

Done ;-)

Thanks again haqking. I'm sorry but I am still trying to figure out if I should use Wubi or should use VMware or Virtual Box.

My biggest concern is idiocy proof-ness. Which of these are going to cause me the least hassle.

Any guidance would be appreciated.

---

### Post by Metalious on 2011-06-21
Actually, I answered my own question here for anyone who stumbles on this thread

[http://ubuntuforums.org/showthread.php?t=1364155](http://ubuntuforums.org/showthread.php?t=1364155)

[INDENT]The main difference is performance.  Wubi does NOT run Ubuntu in a VM,  but simply encapsulates the root filesystem for Ubuntu within the  Windows NTFS filesystem, and then plays tricks with the startup sequence  to boot Ubuntu using that encapsulated filesystem.

There's some overhead from this (having the ext3/4 filesystem  encapsulated within the NTFS filesystem), but this is only on disk  access, and should be substantially less than the overhead from a full  host OS with a virtualization setup.
[/INDENT]

---

### Post by jocko on 2011-06-21
Wubi will let you install ubuntu within a virtual hard drive that is stored as a file on your windows partition. You have to reboot to start ubuntu, and reboot again to get into windows.
The only benefits of using wubi instead of a normal install is that you don't have to change the partitioning of your hard drive, and that you can uninstall ubuntu from within windows if you decide you don't want to keep it. Ubuntu would have complete access to your hardware.
There's probably some loss of performance of running ubuntu in a wubi install compared to a normal install, due to the extra overhead of running from a virtual hard drive on a windows file system. When you run ubuntu, windows would be safe. If you consider a wubi install, my advice would be to do a normal install instead, unless you are very uncomfortable with making changes to your partitions.

A virtual machine (virtualbox or vmware) will let you install any "guest" operating system and run in a window from within your normal "host" operating system. The guest os would not have access to your hardware, but would only run on simulated (virtual) hardware. You would start ubuntu just like you start any other program in windows, and windows would be safe from anything that tries to infect you through the web browser or anything you download. If you set up the networking and internet connection correctly you should be able to have windows completely isolated from internet, but still be able to transfer files that you decide are safe between ubuntu and windows.

I think a virtual machine would create much less hassle. You can save a state of the virtual machine when you know it works, and if you mess it up you can restore it from that saved state. Nothing that happens in your virtual machine will cause any harm to windows.

---

### Post by mastablasta on 2011-06-21
also if you have wubi it's like having dual boot you need to go out and back in. while wiht virtual box or any other virutalization it's like having the system on the click of an icon. only you need plenty ram for it. but if you use it just for net surfing you will be fine.
 
a benefit of virtual OS is that IF it gets infected you just delete the file thta has the virtual system :-) also infection stays within the virtual os.
 
note that even using encryption for your data (like truecrypt for example) does not safeguard us against our own stupidity.

---

### Post by lavinog on 2011-06-21
To access the net in a virtualized ubuntu environment within windows, you will need to have internet access in windows.
You may have better security in ubuntu, however if your windows machine is already compromised with some sort of packet sniffing malware, then using ubuntu virtualized would be pointless.

Depending on the circumstance, you may want to consider getting a separate machine for browsing.  You can get a kvm switch and use that to switch between machines using the same keyboard mouse and monitor.

What software do you use on windows?  Have you checked to see if it works in linux/wine?

---

