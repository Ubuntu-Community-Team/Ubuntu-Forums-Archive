---
title: "BOOTMGR is missing ?"
date: 2011-07-02
forum: General Help
---

### Post by BradRocheee on 2011-07-02
I do not understand alot of thing on a computer so can you help me. I installed ubuntu a couple of days ago replacing windows 7 but i want to got back. I found a windows 7 iso to use and i run it in unetbootin to put it on my usb as i dont have a disk drive. When i reboot my laptop i press f122 to get the boot menu up. I then go to usb and select. An error comes up saying 'BOOTMGR is missing'.I tried this yesterday and no error came up but it didnt work as the iso was wrong. Is there anyway to solve this as i would like windows 7 back.

---

### Post by sam_delta on 2011-07-02
Id guess that the usb was not correctly made by unetbootin. Try burning the ISO to a dvd or make the usb using the provided microsoft tool ([http://images2.store.microsoft.com/prod/clustera/framework/w7udt/1.0/en-us/Windows7-USB-DVD-tool.exe](http://images2.store.microsoft.com/prod/clustera/framework/w7udt/1.0/en-us/Windows7-USB-DVD-tool.exe)) you will need a 4gb usb

sam

---

### Post by soumyabratapaul on 2011-07-02
> **BradRocheee said:**
> I do not understand alot of thing on a computer so can you help me. I installed ubuntu a couple of days ago replacing windows 7 but i want to got back. I found a windows 7 iso to use and i run it in unetbootin to put it on my usb as i dont have a disk drive. When i reboot my laptop i press f122 to get the boot menu up. I then go to usb and select. An error comes up saying 'BOOTMGR is missing'.I tried this yesterday and no error came up but it didnt work as the iso was wrong. Is there anyway to solve this as i would like windows 7 back.

Have you formatted the partition where, the Ubuntu was installed? See this message generally comes up, when the BIOS cannot find the boot sequence which it uses to load the files into the RAM and load up the OS. So looks like you have formatted the system drive where Ubuntu was kept. Now go to Microsoft's website and download the software called "Windows7-USB-DVD-tool", which will actually extract the Windows 7 system files on your USB and make it bootable. Then while, starting your system just press F2/Del/F12, whichever works for your system BIOS, and then go to the boot menu, and then select the boot preference, and set it as USB disk as the first option and then press F10 and then when prompted to save the setting press, yes and exit. Just remember to plug your USB device and it should boot into Windows 7 and you should be able to install the OS. if you encounter any problem just let me know. And also please post all your system configuration.

---

