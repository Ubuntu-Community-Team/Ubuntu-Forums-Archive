---
title: "Sound issues in 9.10"
date: 2009-10-30
forum: General Help
---

### Post by eddtox on 2009-10-30
Hello, I've just upgraded to Ubuntu 9.10 from 9.04 and all my audio is very distorted when I turn it up above a whisper. I had the same problem in 9.04 and I've been trying to fix it for months but to no avail. I also experience the same thing in openSUSE 11.1 but not in Windows XP. I am running a Compaq SR1629UK, specification can be found [_here._]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00579251&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=uk&lang=en&product=1815540")

I include my lspci output. Hope it helps.

> 
:~$  lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
02:02.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 05)
02:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
Any suggestions would be greatly appreciated, as this is the main thing that is stopping me from trying out Ubuntu full-time.  

Thanks,
ed

---

### Post by tommynz1975 on 2009-10-30
this may work as it worked for me with distorted sound in 8.04
go into your sound mixer and reduce the volume of PCM

If its a driver thing I am sure it wont be long before a fix is out. :)

---

### Post by eddtox on 2009-10-30
> **tommynz1975 said:**
> this may work as it worked for me with distorted sound in 8.04
go into your sound mixer and reduce the volume of PCM

If its a driver thing I am sure it wont be long before a fix is out. :)

Thanks for your reply. Reducing the PCM volume does reduce the distortion (I think) but if I do that it makes the sound so quiet you can barely hear it. :-(

ed

---

### Post by Stray Wolf on 2012-06-22
> **tommynz1975 said:**
> this may work as it worked for me with distorted sound in 8.04
go into your sound mixer and reduce the volume of PCM

If its a driver thing I am sure it wont be long before a fix is out. :)

Sound is still full of static and distortion in 12.04. PCM minimizes the distortion but I don't think it actually fixes the problem. It just makes the problem harder to detect audibly. And for me, alsamixer doesn't save the new PCM level so it has to be done every time.

---

### Post by Enigmapond on 2012-06-22
Why did you upgrade to a dead distro? 9.10 died April 2011 so if you will need to download anthing to fix this problem you won't be able to and you won't be getting any updates at all.

---

### Post by Enigmapond on 2012-06-22
Oh never mind...this was just a dead thread as well....hey..I didn't re-open it..LOL

---

### Post by Stray Wolf on 2012-06-23
> **Enigmapond said:**
> Oh never mind...this was just a dead thread as well....hey..I didn't re-open it..LOL
 Sorry, that was me. On Precise the problem persists for me.

---

