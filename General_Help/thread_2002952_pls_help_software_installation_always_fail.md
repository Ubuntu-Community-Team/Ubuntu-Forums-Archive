---
title: "pls help software installation always fail"
date: 2012-06-13
forum: General Help
---

### Post by ray1251 on 2012-06-13
pls help me,since the day i installed ubuntu12.04,i have not been able to download software from terminal command or software center,for software center when i click download it asks for my password,after typing my password it displays Requires installation of untrusted package the action would require the installation of packages from not authenticated sources. ok option and repair when i click ok option,it just stop installation,but when i  click repair it begins to show updating cache  querying software sources which always fail[Failed to download repository information,Check your Internet connection],pls help me i need to starting using my system for programming but unable to even install the application i need ,i use an acer aspire one d257,a mobile network hspa modem.thanks

---

### Post by oldos2er on 2012-06-13
Please run ```
sudo apt-get update
``` in a terminal and post all the output here.

---

### Post by ray1251 on 2012-06-13
> **oldos2er said:**
> Please run ```
sudo apt-get update
``` in a terminal and post all the output here.
ray@ray-AOD257:~$ sudo apt-get update
[sudo] password for ray: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ray@ray-AOD257:~$

---

### Post by drmrgd on 2012-06-13
If you still have the Software Center open, please close it and then try to run that command again.  The system doesn't allow you to do package installation / management with the GUI tool and commandline at the same time.

---

