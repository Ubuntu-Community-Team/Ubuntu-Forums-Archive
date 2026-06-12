---
title: "how to fix with battery-status indicator?"
date: 2011-09-24
forum: General Help
---

### Post by zhu1 on 2011-09-24
read this, please.....):P
i have a problem with  battery-status at ubuntu 10.04 on laptop satellite l640. 
when i write in terminal :
$ dmesg|grep batt

result :

[    0.690699] ACPI: Battery Slot [BAT1] (battery absent)


whereas in the notification area the battery indicator is showing but does not work properly:sad:.
please help me.....
and at power management like this :

[IMG]http://www.freeimagehosting.net/t/f3bcb.jpg[/IMG]











;

---

### Post by varunendra on 2011-09-25
The image you attached is just a thumbnail, so nothing viewable there. The best option is to upload it somewhere else and post its url here using the "Insert Image" button on the edit box.

About the issue- please install "acpi" and see what it tells about your battery:
```
sudo apt-get install acpi
```
To get the status:
```
acpi -bi
```

---

