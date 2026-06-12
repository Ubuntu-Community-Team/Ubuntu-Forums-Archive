---
title: "Is there a virtual version of ubuntu?"
date: 2010-02-03
forum: General Help
---

### Post by Ledus on 2010-02-03
I was wondering if there is a virtual version of ubunbtu which I could run in a window like mirocsoft's XPM.

and no don't tell me about Wubi as it doesn't even work (when I run the app a error message comes up saying "windows no disk" which I can't close so I have to restart)

If there isn't a virtual machine for ubuntu is there a free one for any other Linux OS?

---

### Post by mkvnmtr on 2010-02-03
There is Virtual Box by Sun. You can install it on Windows and then install Ubuntu or pretty much anything else in it. You can also install Virtual Box on Ubuntu and install Windows in it. There is also VMWare that works pretty much the same way.

---

### Post by Bradj47 on 2010-02-03
> **mkvnmtr said:**
> There is Virtual Box by Sun. You can install it on Windows and then install Ubuntu or pretty much anything else in it. You can also install Virtual Box on Ubuntu and install Windows in it. There is also VMWare that works pretty much the same way.

VMware isn't free though. 

Here's VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Ledus on 2010-02-03
> **mkvnmtr said:**
> There is Virtual Box by Sun. You can install it on Windows and then install Ubuntu or pretty much anything else in it. You can also install Virtual Box on Ubuntu and install Windows in it. There is also VMWare that works pretty much the same way.

Links and more info please!

---

### Post by Ledus on 2010-02-03
> **Bradj47 said:**
> VMware isn't free though. 

Here's VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Instructions?

---

### Post by zeroseven0183 on 2010-02-03
Yes, there is. 

You can download the VMWare Player [here]("http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0") or [Sun VirtualBox]("http://www.virtualbox.org/wiki/Downloads"). Both are very good virtualization application.

Then get the Ubuntu "appliance" at [http://www.vmware.com/appliances/directory/435013](http://www.vmware.com/appliances/directory/435013)

Hope that helps.

---

### Post by zeroseven0183 on 2010-02-03
VMWare Player 3 is free. Actually, it has a feature wherein you can now create a new virtual machine. Meaning, if you have the Ubuntu ISO with you, plug it as if you are plugging a CD to install it.

---

### Post by Ledus on 2010-02-03
> **zeroseven0183 said:**
> Yes, there is. 

You can download the VMWare Player [here]("http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0") or [Sun VirtualBox]("http://www.virtualbox.org/wiki/Downloads"). Both are very good virtualization application.

Then get the Ubuntu "appliance" at [http://www.vmware.com/appliances/directory/435013](http://www.vmware.com/appliances/directory/435013)

Hope that helps.

is VMware free?

---

### Post by zeroseven0183 on 2010-02-03
> **Ledus said:**
> is VMware free?

Yes, it is but you will have to register first. Download the latest version here: [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

---

### Post by Ledus on 2010-02-03
> **zeroseven0183 said:**
> Yes, it is but you will have to register first. Download the latest version here: [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Brings me to this page
[https://www.vmware.com/tryvmware/?p=player&lp=1](https://www.vmware.com/tryvmware/?p=player&lp=1)

---

### Post by Ledus on 2010-02-03
can't i just use the app from  [http://www.vmware.com/appliances/directory/435013](http://www.vmware.com/appliances/directory/435013)

and use it on sun's Virtual Box?

---

### Post by gungrog on 2010-02-03
try this: [http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA==](http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA==)

---

### Post by zeroseven0183 on 2010-02-03
Yup, that's right. Go ahead and register. Then after completing the registration, an e-mail will be sent to you for confirmation.

---

### Post by pirateghost on 2010-02-03
> **Ledus said:**
> I was wondering if there is a virtual version of ubunbtu which I could run in a window like mirocsoft's XPM.

and no don't tell me about Wubi as it doesn't even work (when I run the app a error message comes up saying "windows no disk" which I can't close so I have to restart)

If there isn't a virtual machine for ubuntu is there a free one for any other Linux OS?


if you install virtualbox all you need is an iso of a linux distro.  you point the virtualbox to the iso and it will install just like it was a real computer.  you dont NEED appliances or preconfigured virtual machines.

---

### Post by zeroseven0183 on 2010-02-03
> **gungrog said:**
> try this: [http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA==](http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA==)

Yes. And from this link, choose the right one for you.

---

### Post by Bradj47 on 2010-02-03
> **Ledus said:**
> Instructions?

[LIST=1]
[*]Go to [http://virtualbox.org/](http://virtualbox.org/)
[*]Click on the **Downloads** link
***If on Windows:***
[*]Click the link next to **VirtualBox 3.1.2 for Windows hosts**
[*]Wait for the .exe to download
[*]Run the .exe
***If on Linux:***
[*]Click on **VirtualBox 3.1.2 for Linux hosts**
[*]Select your distro and version of Linux and your type of processor
[*]Wait for the .deb to download
[*]Double click on the .deb package when you're done
[*]A window will come up. Click the install button. 

[*][Download Ubuntu]("http://www.ubuntu.com/") if you haven't done so already.
[*]Run VirtualBox (Type **VirtualBox** in the command line if on Linux.)
[*]Click **New**
[*]Click **Next >**
[*]Fill out the form as follows: 
     Name: Ubuntu
     Operating System: Linux
     Version: Ubuntu

[*]Select how much RAM you want to allow Ubuntu to have. (More than half is not recommended.)
[*]Select **Create New Hard Disk**. This is the virtual hard drive where Ubuntu's files will be stored.
[*]A new window will open. Click **Next >**.
[*]Select **Dynamically expanding storage**. Click **Next >**.
[*]Input how much hard drive space you want to allow Ubuntu to have. Click **Next >**.
[*]Now it should display the information you gave it about the virtual hard drive. Click **Finish** and that window should close. 
[*]Now you should be back to the **Create New Virtual Machine ** window. Click **Finish**.
[*]Highlight the item in the list labeled **Ubuntu** to start up the virtual machine. 
[*]A window will come up asking you about the boot source. Browse for the Ubuntu .iso file you just downloaded. 
[*]Install Ubuntu like you would on a normal computer. 
[/LIST]

---

### Post by Ledus on 2010-02-03
> **pirateghost said:**
> if you install virtualbox all you need is an iso of a linux distro.  you point the virtualbox to the iso and it will install just like it was a real computer.  you dont NEED appliances or preconfigured virtual machines.

Ok thanks

---

### Post by Bradj47 on 2010-02-03
> **zeroseven0183 said:**
> Yes, it is but you will have to register first. Download the latest version here: [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

VirtualBox doesn't require you to register. It only recommends it.

---

### Post by Ledus on 2010-02-03
> **Bradj47 said:**
> [LIST=1]
[*]Go to [http://virtualbox.org/](http://virtualbox.org/)
[*]Click on the **Downloads** link
***If on Windows:***
[*]Click the link next to **VirtualBox 3.1.2 for Windows hosts**
[*]Wait for the .exe to download
[*]Run the .exe
***If on Linux:***
[*]Click on **VirtualBox 3.1.2 for Linux hosts**
[*]Select your distro and version of Linux and your type of processor
[*]Wait for the .deb to download
[*]Double click on the .deb package when you're done
[*]A window will come up. Click the install button. 

[*][Download Ubuntu]("http://www.ubuntu.com/") if you haven't done so already.
[*]Run VirtualBox (Type **VirtualBox** in the command line if on Linux.)
[*]Click **New**
[*]Click **Next >**
[*]Fill out the form as follows: 
     Name: Ubuntu
     Operating System: Linux
     Version: Ubuntu

[*]Select how much RAM you want to allow Ubuntu to have. (More than half is not recommended.)
[*]Select **Create New Hard Disk**. This is the virtual hard drive where Ubuntu's files will be stored.
[*]A new window will open. Click **Next >**.
[*]Select **Dynamically expanding storage**. Click **Next >**.
[*]Input how much hard drive space you want to allow Ubuntu to have. Click **Next >**.
[*]Now it should display the information you gave it about the virtual hard drive. Click **Finish** and that window should close. 
[*]Now you should be back to the **Create New Virtual Machine ** window. Click **Finish**.
[*]Highlight the item in the list labeled **Ubuntu** to start up the virtual machine. 
[*]Now just install Ubuntu like you would on a normal computer.
[/LIST]


Ok lets say I don't want it anymore...

Will there be any problems like the original way of un-installing unbuntu?

---

### Post by pirateghost on 2010-02-03
> **Ledus said:**
> Ok lets say I don't want it anymore...

Will there be any problems like the original way of un-installing unbuntu?

no, you just turn off the virtual machine.  this isnt like WUBI

---

### Post by Ledus on 2010-02-03
If i was to use Xubuntu or any other family member of ubuntu would i still select the option Ubuntu or would i select other linux?

---

### Post by zeroseven0183 on 2010-02-03
It depends. You can setup a separate virtual machine for Xubuntu (given that you have the ISO and installed it) or you can just install xubuntu-desktop, or kubuntu-desktop inside your Ubuntu VM.

If you set up a separate VM for Xubuntu, then select it from the VM choices. If you set up Xubuntu/or other derivates inside your Ubuntu VM, you just need to log out from your GNOME session.

---

### Post by Bradj47 on 2010-02-03
> **Ledus said:**
> If i was to use Xubuntu or any other family member of ubuntu would i still select the option Ubuntu or would i select other linux?

You would still select Ubuntu, if you're talking about the **Version** option in VirtualBox. If you want to create multiple virtual machines like [zeroseven0183]("http://ubuntuforums.org/showpost.php?p=8771449&postcount=22") is talking about, all you have to do is use a different name. 

> **Ledus said:**
> Ok lets say I don't want it anymore...

Will there be any problems like the original way of un-installing unbuntu?

No, you just right-click the virtual machine in the list and select **Delete**. Then you could even uninstall all of VirtualBox if you wanted to.

---

### Post by Ledus on 2010-02-03
> **Bradj47 said:**
> You would still select Ubuntu, if you're talking about the **Version** option in VirtualBox. 



No, you just right-click the virtual machine in the list and select **Delete**. Then you could even uninstall all of VirtualBox if you wanted to.

Even after deleting the VM in the list, would it create a partition 
or it "adds" it back to the original hard drive?

the reason I'm asking all these questions is because I don't want to get the same errors and stuff which happened last time but it was a full install

---

### Post by Ordes on 2010-02-03
> **Ledus said:**
> I was wondering if there is a virtual version of ubunbtu which I could run in a window like mirocsoft's XPM.

and no don't tell me about Wubi as it doesn't even work (when I run the app a error message comes up saying "windows no disk" which I can't close so I have to restart)

If there isn't a virtual machine for ubuntu is there a free one for any other Linux OS?

You dont need "virtual versions" of a OS. You only need a virtual machine software, like others already said, virtual box or VMware. In this virtual machine you can than install any OS that you like.

---
A virtual machine handles the virtual OS as a folder/file, which represents the whole HDD of your virtual machine. No need for paritioning or anything. Therefore uninstalling a virtual OS does not affect your current running OS, as the virtual OS only resides in a folder.
----
I dont know wy so many think of wubi as virtual. Wubi is not virtual. Its just an application that helps you to install Ubuntu as dual-boot with Windows...

----
So to close up. After installing your virtual software, create a virtual machine in the settings (how much RAM, how big the HDD, CPU, etc); than mount the image of the OS you want to install (e.g Ubuntu...iso) load up the virtual machine and install the OS. Which will be installed in the FOLDER, that you assigned as "virtual hard drive" before. 
If you dont want the virtual OS anymore you can just delete it.

---

### Post by Bradj47 on 2010-02-03
> **Ledus said:**
> Even after deleting the VM in the list, would it create a partition 
or it "adds" it back to the original hard drive?

the reason I'm asking all these questions is because I don't want to get the same errors and stuff which happened last time but it was a full install

VirtualBox doesn't create any partitions when making virtual hard drives. If you want to be sure to clear all data when you're done, go to **File -> Virtual Media Manager...** and highlight the name of the virtual hard disk and click the **Release** button. Then click the **Remove** button. Then everything you had saved on Ubuntu's virtual hard drive should be gone. 

Also - perhaps you're misunderstanding what VirtualBox is. It runs a guest operating system on top of another host operating system. No partitions are created and you don't have to reboot every time you want to switch operating systems.

---

### Post by Bradj47 on 2010-02-03
> **Ordes said:**
> 
I dont know wy so many think of wubi as virtual. Wubi is not virtual. Its just an application that helps you to install Ubuntu as dual-boot with Windows...


I had never even heard of Wubi until today. But I guess that's because I have no intention of dual-booting Windows. It's bloatedness hogs my hard drive and doesn't give Ubuntu enough room.

---

### Post by Bradj47 on 2010-02-03
I'm heading to bed now. If you need any more help with VirtualBox you can send me a private message and I'll answer tomorrow.

---

### Post by Ledus on 2010-02-03
> **Bradj47 said:**
> I'm heading to bed now. If you need any more help with VirtualBox you can send me a private message and I'll answer tomorrow.

Thanks for the help!

I assure you that I will pm!

---

