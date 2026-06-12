---
title: "Wubi to uninstall Unbutu"
date: 2011-01-25
forum: General Help
---

### Post by Rasputin69 on 2011-01-25
"[Wubi]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") is an officially supported Ubuntu installer for Windows users. It can install and uninstall Ubuntu in the same way as any other Windows application. It's simple and safe."

Ok, due to a failed version I have two installations and I need to use Wubi to uninstall one of them.

I could not find the uninstall instructions.

---

### Post by hhh on 2011-01-25
Go to Add/Remove Programs in Control Panel and uninstall Ubuntu. From the FAQ...
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by bcbc on 2011-01-25
Do you mean you have two entries for "Ubuntu" in your Windows boot manager?

If you need to remove one of them then:
XP - [edit boot.ini]("http://support.microsoft.com/kb/289022") 
Vista/7 - use easyBCD or windows' command line bcdedit command.

---

### Post by Rasputin69 on 2011-01-25
> **hhh said:**
> Go to Add/Remove Programs in Control Panel and uninstall Ubuntu. From the FAQ...
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Ubuntu does not appear in the add/remove list.

---

### Post by IWantFroyo on 2011-01-25
Go into your file system and search for a folder named ubuntu. I don't remember exactly where to find it, but open it and run the uninstall wubi.exe. If it is only wubi.exe, don't run it.

---

### Post by bcbc on 2011-01-25
If you really want to remove Wubi completely, then follow the [manual uninstall instructions]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

But you stated that you had "two" and wanted to remove "one of them". This is not possible. There can only be one Ubuntu installed through wubi - sometimes people see two entries in the Windows boot manager - and my previous post will take care of that; but if you really uninstall Ubuntu  it will remove it completely.

---

### Post by Rasputin69 on 2011-01-25
> **IWantFroyo said:**
> Go into your file system and search for a folder named ubuntu. I don't remember exactly where to find it, but open it and run the uninstall wubi.exe. If it is only wubi.exe, don't run it.

I actually installed it from a usb stick using  the Universal USB Installer. That had wubi.exe in it.

The reason that it did it that way was because  when I had previously tried to open wubi windows froze.

Wubi is not in my add/remove and neither is Ubuntu.

I notice that when I boot the boot manager shows more than one copy of Ubuntu. The one that runs is the default.

There is a second one down the list.

I believe this is the one that was corrupted by the updates.

I have also noticed that the amount of used space on my hard drive has increased signifantly.

I want to be sure that I remove the corrupted installation and not the one that works.

As you can tell, I am a newbi.

---

