---
title: "Cant start windows or ubuntu"
date: 2010-12-17
forum: General Help
---

### Post by Saggat on 2010-12-17
I installed windows Vista, and i choosed a bootloader.
I try EasyBCD 2.0.2 and it worked, but when i choosed UbuntuLinux it just dont start.
Now i screwed up my boot loader somehow. I cant start windows vista or linux, i run the diagnostic and everything is working fine, when the diagnostic finishes , boots from DellRecovery[im using a dell inspiron 1318] and i can see again, the dual boot panel.
Same happens, i can boot Windows Vista but i cant boot Ubuntu.
Now im in vista and triying to fix this, but i just cant, when i try to open easyBCD it says :
Valid BCD registry not detected[COLOR=Red]
"EasyBCD has detected that your BCD boot data and MBR are either not from the lastest version of Windows Vista, or  dont yet exist"[/COLOR]
Then it says if i want to correct the errors, i need to press ok, so i press ok.

"Unfortunately, EasyBCD could not automatically detect the drive letter of your boot device. This can be caused by a non-standard MBR, use of a 3rd-party bootloader, or a failed Windows Vista install.

To proceed, please enter the letter of your boot drive below. The boot drive is identified by the presence of special files and folders like boot.ini, ntldr, and bootmgr. If you continue to see this error message, please run "Reset BCD storage" from the Diagnostics section."
I get this msg, i press OK again, and i get this one
"EasyBCD is now attempting to recreate the BCD registry from scratch. In order for this process to succeed, we need you to pick the letter of a Windows Vista to be the default boot target.

Once you've picked the corresponding letter, press OK to continue."
Again ok, but i get this error:
[COLOR=Red]"The store import operation has failed "
"The volume does not contain recognized file system"[/COLOR]

I dont know what to do now, apparently my boot loader is screwed, i just want to choose between my partitions (ubuntu and windows vista).

---

### Post by Saggat on 2010-12-17
I just find a tool called GAG.
Gag is a boot manager,
i dont know if i can use it , i burn the .iso in a CD, and configure stuff just like int the minute 6:32 in this video [http://www.youtube.com/watch?v=UdI8_92QTkQ&feature=fvw](http://www.youtube.com/watch?v=UdI8_92QTkQ&feature=fvw)
It will work? I dont know. I should try?

---

### Post by ghostborg on 2010-12-17
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

[http://ubuntu-rescue-remix.org/]("http://ubuntu-rescue-remix.org/")

---

