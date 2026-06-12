---
title: "[WUBI] sysnative error!"
date: 2010-06-28
forum: General Help
---

### Post by C0MM4NDER on 2010-06-28
Hi

Recently i have tried to install WUBI on my computer to then install Kubuntu or some other flavor of Linux to test out how the performance is for the ATI 5970 series card since rumors say that ATI have not been so great on Linux. 

Anyway to the point, I am getting errors during the install of wubi. 

First when i select a flavor i see copies of my hard drive in the menu as in this screenshot -> [http://bayimg.com/LaNCEaacg](http://bayimg.com/LaNCEaacg)

After trying to install i am getting errors that it tries to go c:/windows/sysnative/bcdedit.exe and set some parameters. However I do not have this folder. After reading few post and bugs i see several post that it should not go for the sysnative folder if it is not there and instead go to c:/windows/system32/bcdedit.exe however it does the same every time. 

Error screenshot -> [http://bayimg.com/LAncFaACg](http://bayimg.com/LAncFaACg)
Error Loggs -> [http://pastebin.org/363757](http://pastebin.org/363757)

Also is it possible to install Wubi on a Raid Array 0 because i have 3 SATA drives witch two of them are using hardware ATI raid 0. And my third drive is on SATA 3. First few installs of Wubi did work however i got few errors that it could not find installation.iso and got me into busybox and initramfs. 

Few other installs and now i am getting the error that i described above about the bcdedit.

Anyone knows how to fix these issues?

ps running Windows 7 86_64bit

Best Regards
Commander

---

### Post by C0MM4NDER on 2010-07-05
I hate bumps but this need one :(

---

### Post by aphixe on 2011-09-09
Same error i am attempting to install latest version of ubuntu with wubi. i am unsure how to share the log atm. but this i do know. i am using the main drive. and i have ahci enabled and this drive using using GUID setup. Windows 7 pro. Currently i am trying to installing again, but this time went and used ccleaner to try and remove any stuff in registry. Will update if i still have error

Update: Still errors.
Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The requested system device cannot be found.


>>stdout=

[http://pastebin.com/VStZbvF1](http://pastebin.com/VStZbvF1)
i do have a bcdedit.exe in just plain old C:\windows\System32
not sure if its a good thing. but will try maybe making that folder and throwing in the bcdedit.exe

---

### Post by bcbc on 2011-09-09
It doesn't know where the bcd store is. If you go to a command line (as an administrator) and enter "bcdedit" you should see the same exception. Normally that will output the contents of the bcd store.

---

