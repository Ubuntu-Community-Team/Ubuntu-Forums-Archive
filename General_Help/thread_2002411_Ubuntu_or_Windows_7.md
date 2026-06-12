---
title: "Ubuntu or Windows 7"
date: 2012-06-12
forum: General Help
---

### Post by atkol29a on 2012-06-12
Hello all,

Before I ask my question, I understand I am in the Ubuntu forum and most likely everyone answer will be Linux over windows, but I hope whoever answers has an appreciation for both OS. 

At work and at home I mostly use Windows 7 and Server 2008. I am working on a lot of security stuff like penetration testing. I have a workstation I build (2TB HD, 12GB RAM, Quad AMD Processor…) that I use for testing. The workstation had server 2008 and I was using Hyper-V to host my labs. There were some issues and I wiped and installed Windows 7 with VirtualBox for my labs. I like this setup better.

Most of my testing are tested using Linux like BackTrack but also use it to test new products and use it when I get certified in Microsoft products. I am familiar with Linux but not as much as I would like to be. 

So, to my question/s.
Should I keep windows 7 as my host for my labs and Install Ubuntu as a virtual and get familiar with Linux or should I install Ubuntu and have Ubuntu host my virtual labs? If I go with Ubuntu, would I install desktop or server version?

Please feel free to give other options. I just really need to get my labs setup so I can start testing and prep for my next certifications and at the same time get better at using Linux.

Thanks!

---

### Post by Bromden on 2012-06-12
From my point of view the best configuration is installing the distro that you prefer (Xubuntu/Backtrack/Ubuntu....) directly on the machine, and then use Win7 on VmWare Player or VirtualBox.

Vmware player is awesome because it's free, faster than VirtualBox, it lets you drag&drop files from linux to windows and viceversa, and there is an option called Unity (lol XD) that let you fuse/integrate Windows desktop with linux, so you can work on two machines at the same time.

Unfortunately I still have to use Winblows 7, but it happens rarely. I can find almost everything I need in Open Source/Free software :)

If you want a fast distro go for Xubuntu or Linux Bridge/Arch Linux. :D

---

### Post by dino99 on 2012-06-12
as i understand your needs, lets say:
- virtual is good for testing unknown code or new tests, but you cant get the full testing like with real install

- seems you need w7/wx anyway for certification
- linux  is  a hardening OS system

So i think you should install a dual boot & virtualbox/vmware on both OS

---

### Post by Lauscher on 2012-06-20
It is possible to install a dualboot system and run the physical installed system in VirtualBox. You can run a physical installed Ubuntu in VirtualBox in Windows, and you can run a physical installed Windows in VirtualBox in Ubuntu. I wrote a [german guidance]("http://wiki.ubuntuusers.de/Dualboot-Windows_virtualisieren"), if you are interested, you can translate it using google or anything else like that.

---

### Post by taz1232 on 2012-06-20
You have just to experiment and see what works best for you! :)

---

### Post by Mopar1973Man on 2012-06-20
> **dino99 said:**
> as i understand your needs, lets say:
- virtual is good for testing unknown code or new tests, but you cant get the full testing like with real install

- seems you need w7/wx anyway for certification
- linux  is  a hardening OS system

So i think you should install a dual boot & virtualbox/vmware on both OS

I tend to agree with Dino99 because it just easier to dual boot so you have full version of both and no problems with working out of virtualbox that way. But it would be nice to experiment with the two products listed here. ;)

---

### Post by mastablasta on 2012-06-21
> **atkol29a said:**
>  If I go with Ubuntu, would I install desktop or server version?

 
i am not the expert in virtualisation and such but desktop or server.... they are actually both the same. except that desktop has a desktop environment (DE) and less packages used in servers. while server has all necessray server packages but doesn't have any DE (it's a command line install only). however you can get packages you need from repositories. so you can install a DE on server or you can install server packages you need for server on the desktop.
 
you can also do a minimum install of basic OS and then add what you want and need form internet. it keeps the system light.: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
install tutorial if you need it for minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
for example maybe you don't need picture viewer so you simply don't install it. but you need LAMP or whatever and you do install that.

---

### Post by cybergalvez on 2012-06-21
I would install ubuntu as the host and then use virtualbox to run windows7/2003 whatever you want. I often run multiple VM's various version of windows and ubuntu at the same time on an ubuntu host

---

### Post by sammiev on 2012-06-21
Dual boot and have the best of both worlds. :) They both have their Pros and cons.

---

### Post by fmmarzoa on 2012-06-21
> **dino99 said:**
> but you cant get the full testing like with real install

That could be true several years ago (when Romanov rules Russia, or so...), but nowadays is not true, indeed. From the guest OS point of view there is no difference at all between running on a physical hardware or virtualized one.

---

### Post by jllipke on 2012-06-21
windows usually has more sources but Ubuntu is usually a more sturdy.

But it totally depends on what u are using it for. There are also plenty of other sites to check on for a good comparison

---

### Post by Mark Phelps on 2012-06-21
The problem you're going to run into using Ubuntu as your base system and Virtualbox for the MS Windows systems is twofold:
1) You will have to COMPLETELY reinstall each of the Windows OSs to use VB.  You can't simply point VB at an existing installation.  This means all the apps, and all the Windows Updates. Windows generally sees VB installations differently than regular installations, so this often requires "reactivating" the OS instances and some apps.  In some cases, this can be a nightmare.
2) VB can not do everything exactly the same way as a native Windows installation.  If you're just experimenting with Windows versions and don't care about that, then VB may be your best solution.  But, if you are dependent on the discrete details of Windows configuration and performance, then native installations are the way to go.

Most folks follow the practice of installing their most used and most critical OSs in native form, and the others in VB.  Which one you do depends on how you use the OSs.  From what you've said, it may be best to leave the Windows OSs installed in native form.

---

