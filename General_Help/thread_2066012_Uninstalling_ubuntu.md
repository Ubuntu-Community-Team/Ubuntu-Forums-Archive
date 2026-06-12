---
title: "Uninstalling ubuntu"
date: 2012-10-03
forum: General Help
---

### Post by NicolasTX on 2012-10-03
Hello, so I downloaded ubuntu and Im not really caring much for it so I wanted to switch back to my old operating system. But Im unable to figure out how to do so, Ive tried looking up how I would go about uninstalling ubuntu but I have not had much luck. The information I did find was not very helpful as I dont know how to use ubuntu. If anyone has any information on how I would go about uninstalling ubuntu, or just switching to my old os, as I dont necessarily want to uninstall ubuntu as I would like to check it out, but I have to do alot of work for school and I want to stick to my old os as Im very familiar with it. So if there is a way I can switch between the os's without having to uninstall one or the other that would be great. Any and all help is appreciated. :cool:

---

### Post by offgridguy on 2012-10-03
This link will help.[http://www.makeuseof.com/tag/how-to-...t-environment/]("http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/")

... and scroll to the heading 'Restore MBR

---

### Post by Frogs Hair on 2012-10-03
Hello and Welcome

Please provide some information about your computer, the other operating system, and the Ubuntu installation. I dual boot with Win 7 mainly for school. many computers come with preloaded Windows and include a recovery partition. I built my desktop and there were no preloaded partitions and I installed Windows from disk. What you need to do may vary depending on the computer and the other operating system.

---

### Post by oldfred on 2012-10-03
You can use this repairCD to uninstall one system and it will add the boot loader for the other. But if you have to totally reinstall it will not do that.

Yanni has created a easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)

---

### Post by NicolasTX on 2012-10-03
@offgridguy
I checked out that page earlier, if I understood it correctly I need my windows 7 cd to revert to my old os? Which I dont have unfortunately.

@Frogs Hair dont know much on the specs but the other OS is windows 7. And I installed Ubuntu desktop 12.04 LTS

---

### Post by NicolasTX on 2012-10-03
@oldfred I checked out that thread and followed the steps but Im unable to find the uninstaller on my computer. I guess I could take another crack at the steps provided but it seemed really simple and Im pretty sure I followed it correctly but with no results.

---

### Post by oldfred on 2012-10-03
Its not built into your system, you have to use LiveCD or USB and download it.

One of the ways to install this is a full repairCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

But you will need your Windows 7 DVD to reinstall. Or if installed and not working a Windows 7 RepairCD or USB to fix it. Boot repair can put a Windows type boot loader into the MBR if your Windows 7 otherwise works.

---

### Post by offgridguy on 2012-10-03
You also mentioned you didn't want to uninstall but be able to switch between windows7 and
ubuntu,   What is happening now when you boot up your computer?

---

### Post by YannBuntu on 2012-10-04
Hi
Seems like your current problem is that you have no access to Windows.
Removing Ubuntu won't fix it.

Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") --> Recommended repair, and indicate the URL that will appear.
Then reboot the PC and tell us what you observe.

---

