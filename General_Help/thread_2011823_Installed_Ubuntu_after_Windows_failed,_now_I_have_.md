---
title: "Installed Ubuntu after Windows failed, now I have three copies?"
date: 2012-06-27
forum: General Help
---

### Post by Shrunk on 2012-06-27
Hi! I'm very new to this OS so please bear with me! I've got multiple issues, so I had no idea where to place this! Mods: please move this if I'm wrong!

A few days ago I put ubuntu on my Asus K53SV Laptop because I had a pretty nasty virus on windows 7. Long story short: Windows 7 ended up crashing entirely and it led to a black screen with a blinking underscore cursor, never to even begin starting windows. I took it back to the shop I bought it at, and even under warrenty, wanted to charge me like 160 big ones just to install windows back on. I said no, took the computer back home and tried to install windows three separate times to no avail. I said forget it and just installed Ubuntu alongside of windows to see if I could actually use windows at all.

When I finally installed Ubuntu, I wanted to see if anything was still usable in windows. So when I choose windows instead of Ubuntu as my OS, I am taken to a screen where I have three different "Windows 7"'s to choose from. All of them appear to be the same thing. (no drivers installed, completely fresh versions of windows)

My questions are these... How can I remove all but one version? I want to use windows instead of Ubuntu for playing games, and it seems like a waste of space if I really do have three separate versions of windows. However, I do have my windows key still. Optimally, I would like to just have Ubuntu for schoolwork, using the internet, graphic design, art, etc. Then use Windows 7 for video games. Can anyone help me work around my problem?

---

### Post by Brad55 on 2012-06-27
To start off I hope you have your Windows 7 DVD and the key, if so you can clean the HD by formatting it for a clean install of Windows 7. Trying to clean 2 different installs of Windows 7 could take some time.

If it was me I would format the HD then install Windows 7 then Ubuntu. Here are 3 sites that will help you installing Ubuntu along side Windows 7.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")
[http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/")

---

### Post by oldfred on 2012-06-27
Are you sure you have three installs? 

Windows normally only installs to the active partition or the one with the boot flag. So it is unlikely it installed three times unless you manually moved boot flag first.

Sometimes grub2 reports the recovery partition and mahbe the vendor partition as bootable and does not separately rename them. Some times boot flag moves from the 100MB boot/repair partition to main partition and then you have two bootable (from grub) but really only one install.

Post link to Bootinfo report that you can create from this:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

