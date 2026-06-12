---
title: "Sony Vaio Y blank screen problem"
date: 2010-08-08
forum: General Help
---

### Post by blandwa on 2010-08-08
When I try to install Ubuntu or (having installed using Wubi) boot Ubuntu, I get a blank screen and no activity.  This problem has been addressed many times but I haven't been able to get any of the proposed solutions (e.g. nomodeset, i8042.nopnp) to work.  Could someone provide any help that is specific to my hardware?  Is there another Linux or Unix-like OS that is known to work with this hardware?

Sony Vaio Y (VPCY)

Name	Intel(R) HD Graphics
PNP Device ID	PCI\VEN_8086&DEV_0046&SUBSYS_9076104D&REV_02\3&11583659&0&10
Adapter Type	Intel(R) HD Graphics (Core i3), Intel Corporation compatible
Adapter Description	Intel(R) HD Graphics
Adapter RAM	1.71 GB (1,840,177,152 bytes)
Installed Drivers	igdumd64.dll,igd10umd64.dll,igdumdx32,igd10umd32
Driver Version	8.15.10.2102
INF File	oem4.inf (iILKM0 section)
Color Planes	Not Available
Color Table Entries	4294967296
Resolution	1366 x 768 x 60 hertz
Bits/Pixel	32
Memory Address	0xD0000000-0xD03FFFFF
Memory Address	0xC0000000-0xFEAFFFFF
I/O Port	0x00005050-0x00005057
IRQ Channel	IRQ 4294967294
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\igdkmd64.sys (8.15.10.2102, 9.84 MB (10,320,512 bytes), 21/04/2010 3:57 PM)

---

### Post by 2ormore on 2010-08-17
Hi,

Did you find a solution? I'm facing the exact same issue... :(

> **blandwa said:**
> When I try to install Ubuntu or (having installed using Wubi) boot Ubuntu, I get a blank screen and no activity.  This problem has been addressed many times but I haven't been able to get any of the proposed solutions (e.g. nomodeset, i8042.nopnp) to work.  Could someone provide any help that is specific to my hardware?  Is there another Linux or Unix-like OS that is known to work with this hardware?

Sony Vaio Y (VPCY)

Name	Intel(R) HD Graphics
PNP Device ID	PCI\VEN_8086&DEV_0046&SUBSYS_9076104D&REV_02\3&11583659&0&10
Adapter Type	Intel(R) HD Graphics (Core i3), Intel Corporation compatible
Adapter Description	Intel(R) HD Graphics
Adapter RAM	1.71 GB (1,840,177,152 bytes)
Installed Drivers	igdumd64.dll,igd10umd64.dll,igdumdx32,igd10umd32
Driver Version	8.15.10.2102
INF File	oem4.inf (iILKM0 section)
Color Planes	Not Available
Color Table Entries	4294967296
Resolution	1366 x 768 x 60 hertz
Bits/Pixel	32
Memory Address	0xD0000000-0xD03FFFFF
Memory Address	0xC0000000-0xFEAFFFFF
I/O Port	0x00005050-0x00005057
IRQ Channel	IRQ 4294967294
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\igdkmd64.sys (8.15.10.2102, 9.84 MB (10,320,512 bytes), 21/04/2010 3:57 PM)

---

### Post by blandwa on 2010-08-18
No, I never found a solution.  I settled for VirtualBox.

---

### Post by habitu on 2010-11-17
Hi,

I own a VPCY2 (i5 U430, Ubuntu 10.10, installed by USB (pendrivelinux)). 

Replacing "quiet splash" by "i915.modeset=0 xforcevesa" booted my system.




Btw: If you have time and like to customize your system I can recommend CrunchBang Linux. 
It installed and worked out of the box. However it is minimal.

---

### Post by blandwa on 2010-11-21
Thanks for your reply.

Did everything else (e.g. wireless) work, too?

---

### Post by habitu on 2011-03-10
time to revive this thread :D

works:    
wireless, bluetooth, speakers, headphones, cpu and hdd temp sensors, 
          cpu scaling, mousepad

does not work:    
microphone, external VGA (probably both config issues)

not tested:    
hdmi, SD-cards, SIM-card and some vaio keys

---

### Post by ceminino on 2011-03-21
I can' get the display to load the intel drivers, I tried the solution here:
[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e](http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e)
but still just vesa...
could you post your xorg file or give a tip?

> **habitu said:**
> time to revive this thread :D

works:    
wireless, bluetooth, speakers, headphones, cpu and hdd temp sensors, 
          cpu scaling, mousepad

does not work:    
microphone, external VGA (probably both config issues)

not tested:    
hdmi, SD-cards, SIM-card and some vaio keys

---

### Post by blandwa on 2011-04-10
I didn't have the blank screen problem at all with Ubuntu 11.04 Beta 1.  Wireless isn't working though, as described in [http://ubuntuforums.org/showthread.php?t=1723617](http://ubuntuforums.org/showthread.php?t=1723617).

---

### Post by ceminino on 2011-04-10
> **blandwa said:**
> I didn't have the blank screen problem at all with Ubuntu 11.04 Beta 1.  Wireless isn't working though, as described in [http://ubuntuforums.org/showthread.php?t=1723617](http://ubuntuforums.org/showthread.php?t=1723617).

you can fix the wireless problem by blacklisting acer-wmi

---

### Post by blandwa on 2011-04-10
> **ceminino said:**
> you can fix the wireless problem by blacklisting acer-wmi

Worked.  Thanks!

---

### Post by ceminino on 2011-04-10
> **blandwa said:**
> Worked.  Thanks!

no problem.

They are also problems with acpi I couldn't solve, standby doesn't work and no temperature...

---

### Post by vehka on 2011-05-02
Yes, suspend and hibernate seems to not work. There's always a blank screen after resume with suspend. I tried booting into a root shell and typing pm-suspend, same thing. Couldn't find anything in the pm-suspend log file either. Any ideas how to continue debugging this problem?

---

### Post by vehka on 2012-01-16
Just a brief update: suspend works with Ubuntu 11.10 on Vaio VPC-Y2.

---

