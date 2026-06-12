---
title: "ubuntu doesn't boot"
date: 2010-10-15
forum: General Help
---

### Post by the_storm on 2010-10-15
hey guys,
 I have a big problem with my Ubuntu. First I installed Ubuntu on my computer and it worked perfectly, and then I decided to install Windows 7, so I should have dual boot ubuntu and windows 7, but what happened is that I can't run my ubuntu anymore. After the installation of windows 7 i cant see my ubuntu and I haven't a dual boot. So what is the solution to get my ubuntu back ? and to have a dual boot ?

---

### Post by 3Miro on 2010-10-15
Windows 7 overwrites Grub (the program that Linux uses to boot and dual-boot). Since there is no optin in windows to prevent that, every time you reinstall it, you have to reinstall grub afterwards. Here is the official tutorial on how to do it:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Scroll almost to the bottom, you want only the section about "Reinstalling GRUB 2". You probably need to follow the second method mentioned (however, the first one should work as well).

Note: I am writing this under the assumption that you are using Ubuntu 9.10 or 10.04 or 10.10. Earlier versions used Grub 1 as opposed to Grub 2 and the reinstallation method was different.

---

