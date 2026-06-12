---
title: "amd catalyst 11.4"
date: 2011-05-18
forum: General Help
---

### Post by ddimit on 2011-05-18
im running ubuntu 11.4
im trying to install amd catalyst 11.4  for my x1300 ati graphic card
but when i installed it my system couldn't start and i had to start in recovery mode for removing tha package..
i think i have done something wrong with the packages 
any help for how to install ati catalyst 11.4 on my x1300 graphic card

---

### Post by pme 72 on 2011-05-21
I am not running Natty but I wondered what features the default open source drivers for your card lacked that caused you to want to upgrade to a proprietary one. I have read that the OS driver support for the X1xxx series has improved since 10.10 with the advent of Gallium. 

Unfortunately the amd catalyst 11.4 driver does not support your x1300. From [http://wiki.cchtml.com/index.php/Hardware:](http://wiki.cchtml.com/index.php/Hardware:)

 Radeon (Catalyst Legacy & Open Source)

ATI/AMD dropped Catalyst support for these cards in Catalyst 9-4. These cards are supported with the legacy ATI 9-3 Catalyst release, but you MUST use a kernel 2.6.28 (or earlier) and Xserver 1.5 (or earlier). For example, you can use Catalyst 9-3 if you're running Ubuntu 8.04 or Debian Lenny/5.0. Open source support is good and 3D is still improving.

* RS400/RS480 Radeon XPRESS 200(M)/1100 IGP
* R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1
* R350        Radeon 9800PRO/9800SE/9800, FireGL X2
* R360        Radeon 9800XT
* RV350       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2
* RV360       Radeon 9600XT
* RV370       Radeon X300, M22
* RV380       Radeon X600, M24
* RV410       Radeon X700, M26 PCIE
* R420        Radeon X800 AGP
* R423/R430   Radeon X800, M28 PCIE
* R480/R481   Radeon X850 PCIE/AGP
* RS482       Radeon (Xpress) 200
[COLOR="Red"]* RV505       Radeon X1300,[/COLOR] M52, M62
* RV515       Radeon X1400, M54, M64
* RV516       Radeon X1500
* RV550       Radeon X2300
* R520   ........and so on

Have you been successful removing the catalyst driver and restoring the default one?

---

### Post by MainframeGuy on 2012-04-28
Radeon X1300 was supported native for NAtty, I should know, I just moved to Pengolin and it broke my dual head :(

Anyone know good source for a driver that works with Pengolin?

---

### Post by MainframeGuy on 2012-04-28
> **pme 72 said:**
> ...

ATI/AMD dropped Catalyst support for these cards in Catalyst 9-4. These cards are supported with the legacy ATI 9-3 Catalyst release,...
linkie for others.... [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

