---
title: "dual bootoot"
date: 2012-04-14
forum: General Help
---

### Post by drklunk on 2012-04-14
made the switch from ubuntu 12.04 beta to xubuntu 12.04 beta and wanted to take the opportunity to set up a dual boot with a minimalist Windows 7. I installed the two on separate partitions, Xubuntu before Windows. now that Ive finished the Windows install I cant figure out how to boot into Xubuntu as it seems to boot Windows by default. 

hoping this is easy enough to figure out

---

### Post by Elfy on 2012-04-14
You need to reinstall grub - [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by PhantomTurtle on 2012-04-14
You normally install Windows first since it overwrites grub. To get it back follow the guide on this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by drklunk on 2012-04-14
thanks fellas! all I needed

---

### Post by drklunk on 2012-04-14
alright, came across another problem but didnt wanna start a new thread: how can I install Windows drivers (graphics, wireless card, etc.) from Xubuntu? is it possible just to copy files from the archive manager into the proper Windows installation folder?

---

### Post by PhantomTurtle on 2012-04-14
Do you mean you want to install Windows drivers in Xubuntu? You will have to find Linux drivers if they weren't installed already. Usually most things work out of the box in Ubuntu

---

### Post by rhss6-2011 on 2012-04-14
I can't say for sure, but I don't think that is possible. I think you can only install drivers onto your windows machine if you are actually logged in to windows.
You can of course, copy the files and everything if you download the drivers in Linux but you still need to login to windows in order to install them...

*I think*

---

### Post by drklunk on 2012-04-14
> **rhss6-2011 said:**
> I can't say for sure, but I don't think that is possible. I think you can only install drivers onto your windows machine if you are actually logged in to windows.
You can of course, copy the files and everything if you download the drivers in Linux but you still need to login to windows in order to install them...

*I think*
the option I overlooked, even made my storage NTFS so I could do stuff like that xD

my Windows installation needs drivers, but I didnt think to just download them, launch Windows, and install them that way. shoot, another solution made easy, must be my day

---

