---
title: "Novell App Armor and Google Chromium web browser"
date: 2012-05-13
forum: General Help
---

### Post by Welly Wu on 2012-05-13
I have a heavily modified ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD. I installed Ubuntu 12.04 64 bit Long Term Support two days ago as my primary operating system. I also installed apparmor-profiles and I chose to set Samba (smbd and nmbd) to enforcing mode. I installed Google Chromium web browser. I tried to set its default app armor profile into enforcing mode, but it will not launch when I click it in Unity 3D. I made a backup copy of the default Novell App Armor profile for Google Chromium and I copied and pasted Bodhi Zazen's custom Novell App Armor profile for Google Chromium designed for Ubuntu 10.04 LTS. It will not let me put Google Chromium into enforcing mode.

I need help writing my own Novell App Armor profile for Google Chromium web browser. It must be able to launch properly without errors and I must be able to download folders and files to my /home/wellywu/Downloads directory.

If this is too much to ask, then can you point me to a specific custom Novell App Armor profile for Google Chromium web browser that will permit it to launch and save folders and files to the default Downloads directory within the /home partition here in Ubuntu Forums? I have been searching and all that I see is Bodhi Zazen's custom Novell App Armor profile and it is not what I am looking for. I am looking for a semi-hardened custom Novell App Armor profile that is fairly restrictive except for the capability to download folders and files from the Internet to the /home/wellywu/Downloads directory and it will permit Google Chromium to launch without errors.

Please help me or point me in the right direction. Thank you.

---

### Post by Welly Wu on 2012-05-16
How do I modify the default Novell App Armor profile installed by the apparmor-profiles package for Google Chromium so that it will allow it to launch without errors and I can download content to my /home/wellywu/Downloads directory when I set it to enforcing mode? Please help if possible. Thank you.

---

### Post by Welly Wu on 2012-05-17
This is from Google: [https://code.google.com/p/chromium/wiki/LinuxSandboxing](https://code.google.com/p/chromium/wiki/LinuxSandboxing)

---

