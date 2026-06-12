---
title: "confusion about SATA settings for new build"
date: 2009-11-19
forum: General Help
---

### Post by wanderingarticfox on 2009-11-19
I've been researching information for my new build and could use some help on an issue about SATA Controller Settings. I will be using a Gigabyte  :[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=3143&ProductName=GA-MA790GPT-UD3H](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=3143&ProductName=GA-MA790GPT-UD3H)  and two HDD's  [http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=58&subtype=70&model_cd=229&tab=fea&ppmi=1162](http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=58&subtype=70&model_cd=229&tab=fea&ppmi=1162)  and I plan to Use Ubuntu Alt. Install AMD_64 to create a software RAID. 
This is where the confusion comes in; Gigabyte says : Dear customer,
Linux same as Windows, need to enable SATA controller in bios to Raid and create Raid 1 array when system boots on second screen press Ctrl + F1 two keys in AMD Raid bios config, then when loading Linux need provide driver. please log on AMD web side look for SB 750v SATA driver for Linux support or log on Linux web look for the correct driver.( We are sorry since Linux was open source OS Gigabyte not provide Linux driver support ).  Their manual and AMD Catalyst info page say  [Gigabyte] Chapter 3	 Drivers Installation
    •	 Before installing the drivers, first install the operating system.
    •	 After installing the operating system, insert the motherboard driver disk into your optical drive.  {AMD CAtalyst}  Minimum System Requirements
       Before attempting to install the ATI Proprietary Linux driver, the following software
       must be installed:
          XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
          Linux kernel 2.6 or above
          glibc version 2.2 or 2.3
          POSIX Shared Memory (/dev/shm) support is required for 3D applications
  I _Think, but am not sure_ That if I set the SATA controller to 'Native IDE' that Ubuntu Will recognise [read 'see'] both drives and I can follow the guide [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) and set things up then after completeing the installation and using update manager I can then follow [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) to update the AMD Drivers.
 The problem I am having is that Gigabyte says I have to use the RAID 1 on the chipset and it is my understanding that Ubuntu [Linux] software RAID 1 is going to have the drivers needed to detect and allow the set up of the array via the Alt. Install ISO. I know a lot of people think I should use the 'FakeRAID' on the board; please read the following the above link to [Ubuntu Installation of Software RAID].
In conclusion I think that setting the SATA controller to Native IDE and using the Alt. Install ISO will allow me to build the array and then after updates and a few restarts I can then update the drivers in order to be able to take advantage of the on-board video best until I add a GPU card with ATI chip set. I could use some expert advice here, thank you, JLP:confused:

---

### Post by Giblet5 on 2009-11-19
You don't want to use software RAID. Really.

That is the fast-path to data loss. Great idea, impossible to maintain reliability.

If you want RAID, buy a real Hardware RAID Controller, such as the Adaptec PCIe SATA job.

Software RAID is a gimmick to make people think they can have high-end functionality on a shoestring budget. Technically, they're correct because you can get a system to boot with fake-raid.

Check [Google]("http://www.google.com/search?q=software+raid+sucks&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") first...

---

### Post by wanderingarticfox on 2009-11-19
Are you saying that the 'Software RAID 1' as described at [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
is not stable? Oh wow:confused:
I thought it was better than 'Fake RAID' from the motherboard chip set SATA Controller. I'm trying to learn about this before I build. I only plan on RAID 1 with 2 drives. I know if I wanted to get into a more complicated set up that a RAID Controller Card would be better but I was just hoping for a mirror of data.
I'm still confused:confused::rolleyes:

---

### Post by wanderingarticfox on 2009-11-20
I could really use a little help here. Thank You .

---

