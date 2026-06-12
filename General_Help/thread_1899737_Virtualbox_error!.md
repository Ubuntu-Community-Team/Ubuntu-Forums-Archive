---
title: "Virtualbox error!"
date: 2011-12-24
forum: General Help
---

### Post by linuxuser12345 on 2011-12-24
Every time I try to start a virtual machine in Virtualbox, I get this error message:

```
Failed to open a session for the virtual machine Linux.

The device helper structure version has changed.

If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

```
and it doesn't start. How do I fix this problem? 

How do I completely remove Virtualbox and all of it's files, folders, etc., also? Maybe that will fix the problem?

---

### Post by Habitual on 2011-12-24
["upgraded any extension packs"]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack")

---

### Post by BC59 on 2011-12-24
```

sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by linuxuser12345 on 2011-12-24
How to I delete my extension packs instead?

---

### Post by BC59 on 2011-12-24
What do you mean? Did you try the commands I posted?

---

### Post by linuxuser12345 on 2011-12-24
Same thing:
```
Failed to open a session for the virtual machine linux.

The device helper structure version has changed.

If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

```


And I think that if I delete the extension packs, everything will work fine: My extension packs are up to day and everything was fine beforehand

---

### Post by BC59 on 2011-12-24
Yes but you have to update the extension packs. The best way is through the commands I posted.

---

### Post by h3hound on 2011-12-24
I was working on enabling USB stuff and got this error on a mac osx guest.  I turned **off** "Enable USB 2.0 (ECHI) Controller" and the machine started up normally.

---

### Post by Fudaraku on 2012-01-15
I had the same problem. I was moving from a Natty installation to an Oneiric one. In Natty I was using virtualbox-4.1 package from virtualbox.org but I forgot about that. So my Natty was on 4.1.8 while Oneiric's native virtualbox package is 4.1.2.

When installing Virtualbox extension pack in Oneiric I went to virtualbox.org and took the latest one, ie 4.1.8. It was possible to install it over 4.1.2 but when starting a machine with USB enabled I got the helper version mismatch error.

The solution was to configure Oneiric to use packages from virtualbox.org as described here:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

remove virtualbox package by synaptic and install virtualbox-4.1 instead. Now I can use my old virtual machines with USB enabled.

---

### Post by biodiesel-bri on 2012-03-03
> **h3hound said:**
> I was working on enabling USB stuff and got this error on a mac osx guest.  I turned **off** "Enable USB 2.0 (ECHI) Controller" and the machine started up normally.

That fixed it for me.  Thank you!

---

### Post by 2beanet on 2012-05-10
> **h3hound said:**
> I was working on enabling USB stuff and got this error on a mac osx guest.  I turned **off** "Enable USB 2.0 (ECHI) Controller" and the machine started up normally.


Yeah, the problem appears after I turn on 'Enable USB 2.0 (EHCI) Controller',

and I turn off it again and the virtual machine start correctly.

---

### Post by zoltan08 on 2012-05-12
Hello,

I've been through all sorts of threads regarding a similar issue that I have and I just can't seem to fix it.

In short, I have an IPAD 2 that i'd like to update to IOS 5 (finally) but since i'm running on UBUNTU, the only way is through virtualbox. Problem is, the USB MASS STORAGE DEVICE driver can't be recognized, so no connections are possible.
I have all the latest extensions for my virtualbox, here's my settings:

- Ubuntu version: 11.10
- OS: 64 bit
- Virtualbox version: 4.1.2_Ubuntu
- Extension package: Oracle VM VirtualBox Extension Pack, v. 4.1.14rxxxxx
- Virtual Machine: Windows 7 Ultimate (32 bit)
- I already had the vboxusers assigned to my groups.
- Added Ipad to virtualbox usb device filters.

Whenever I check the "Enable USB 2.0 (EHCI) Controller", my virtualbox gives me the following error:

--------------------------------------------------
Failed to open a session for the virtual machine Windows 7.
The device helper structure version has changed.
If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH)

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
---------------------------------------------------

Seems like a version mismatch problem, but there's no other version that works with my latest virtualbox version!

When I uncheck the USB 2.0 EHCI box, it works fine. However, windows 7 does not recognize the usb input from the ipad (ie. usb mass storage device isn't available when trying to connect it manually).

Any help on this would be appreciated. I don't want to uninstall my virtualbox since I have a few apps installed in my virtual machine that i wouldn't like to reinstall all over again.

Thanks in advance!

---

### Post by Docmero on 2012-05-18
I have the same error , Any solution ?

---

### Post by mortez on 2012-11-06
> **h3hound said:**
> I was working on enabling USB stuff and got this error on a mac osx guest.  I turned **off** "Enable USB 2.0 (ECHI) Controller" and the machine started up normally.

Thanks a bunch, I've searched the ups and downs of the Internet for such a simple solution.](*,)

---

### Post by pkadeel on 2012-11-06
> **zoltan08 said:**
> Hello,

I've been through all sorts of threads regarding a similar issue that I have and I just can't seem to fix it.

In short, I have an IPAD 2 that i'd like to update to IOS 5 (finally) but since i'm running on UBUNTU, the only way is through virtualbox. Problem is, the USB MASS STORAGE DEVICE driver can't be recognized, so no connections are possible.
I have all the latest extensions for my virtualbox, here's my settings:

- Ubuntu version: 11.10
- OS: 64 bit
- Virtualbox version: 4.1.2_Ubuntu
- Extension package: Oracle VM VirtualBox Extension Pack, v. 4.1.14rxxxxx
- Virtual Machine: Windows 7 Ultimate (32 bit)
- I already had the vboxusers assigned to my groups.
- Added Ipad to virtualbox usb device filters.

Whenever I check the "Enable USB 2.0 (EHCI) Controller", my virtualbox gives me the following error:

--------------------------------------------------
Failed to open a session for the virtual machine Windows 7.
The device helper structure version has changed.
If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH)

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
---------------------------------------------------

Seems like a version mismatch problem, but there's no other version that works with my latest virtualbox version!

When I uncheck the USB 2.0 EHCI box, it works fine. However, windows 7 does not recognize the usb input from the ipad (ie. usb mass storage device isn't available when trying to connect it manually).

Any help on this would be appreciated. I don't want to uninstall my virtualbox since I have a few apps installed in my virtual machine that i wouldn't like to reinstall all over again.

Thanks in advance!
Latest VirtualBox is 4.2.4 with new extenssions pack whereas you have 4.1.2

---

### Post by PHP_Learner on 2013-09-09
I have similar problem:](*,)
Installed VirtualBox using "Ubuntu Software Center"---> version= 4.2.10
Downloaded Extension Pack from virtualbox.org---> version= 4.2.18
After adding extension pack to VB and activating USB2.0 on a machine, the machine could not start. The error was as follows:
        
>          Failed to open a session for the virtual machine Linux.
        
        The device helper structure version has changed.
        
        If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

        Result Code: NS_ERROR_FAILURE (0x80004005)
        Component: Console
        Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

THE SOLUTION I FOUND:
1) removing VB version 4.2.10
2) downloading appropriate *.deb package of version 4.2.18 from virtualbox.org
3) installing that *.deb file using dpkg command
4) adding same version extension pack to new VB (4.1.18)
Now my USB2.0 works properly with my guest machine!!!:P

---

