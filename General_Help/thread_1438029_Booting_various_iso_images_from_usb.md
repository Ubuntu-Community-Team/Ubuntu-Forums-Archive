---
title: "Booting various iso images from usb"
date: 2010-03-24
forum: General Help
---

### Post by ryniek on 2010-03-24
I've searched for answers in google, but get not i wanted. I wanted to prepare bootable iso from usb under Ubuntu. Fine, there's **UNetBootin**, **dd if= of=** command etc. But I am concerned and the specific type of iso images booting - AntiVirus rescue cd's.

Using UNetBootin i could only prepare thumb drive to boot Dr. Web Rescue CD, but neither Kaspersky Rescue Disk nor F-Secure Rescue CD couldn't be preapred well (NOTE that my BIOS can boot livecd from usb drive!). Using dd if= of= command also didn't worked, cause prepared thumb couldn't boot - get errors: "Missing operating system" or "Could not find kernel image: linux". Is it that i must install grub/lilo or syslinux on thumb, then edit .cfg file and then copy image, or what? I'm concerned only on AV Rescue Disk's, like: Kaspersky, F-Secure, GData Boot CD, BitDefender Rescue Disk etc. I've booted (and it worked) Symantec boot cd but it's based on WinPE and i had prepared thumb under Windows 7, so it's a completely different story.

I have **Bootable USB Drive Assistant** in my Ubuntu 9.04 but when i try to choose some of those cd's, i get error that "It isn't installable CD image, so application can't use it" or something like that. What application do i have to use then?

Thanks for help

---

### Post by C.S.Cameron on 2010-03-25
You could try BootMyISO-v0.2
It works with some iso's I've tried but not others.

Pendrivelinux website also might have some suggestions.

Nimblex is a small distro that comes with vbox, but I'm not sure if you can run an anti-virus program from a virtual machine to cure an external O/S.

---

