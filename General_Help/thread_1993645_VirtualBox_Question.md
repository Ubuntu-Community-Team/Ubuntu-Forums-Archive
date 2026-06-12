---
title: "VirtualBox Question?"
date: 2012-06-02
forum: General Help
---

### Post by cottfcfan on 2012-06-02
I have Windows 7 installed alongside Ubuntu on a 1TB Disc.
My computer came with a Windows 7 Recovery partition instead of a DVD.
Is it possible to wipe my Hard Drive (excluding the Recovery partition), install Ubuntu and then install Windows 7 in Virtualbox from the partition instead of from a DVD/CD? and if so how?
Thanks in advance.

---

### Post by Cheesemill on 2012-06-02
No, it's not possible I'm afraid. Even if it was you would be breaking the terms of your Windows license agreement.

An OEM copy of Windows (like the one your recovery partition contains) is only licensed to run on the actual hardware. To install a Windows VM you need a full retail copy of Windows and the installation CD that comes with it.

---

### Post by flemur13013 on 2012-06-02
You can download the windows ISO (google around, they are out there and legal), burn it to disk and use the registration code on the back of your machine or in your paperwork to register it.

---

### Post by Cheesemill on 2012-06-02
This *may* work, but the CD you download probably won't work with the OEM key that you have. Your key will only work with a CD that is tied to the manufacturer of your machine. These CD's won't work with a VM.

Even if it does work you are breaking your Windows license agreement by installing Windows on a VM instead of the physical hardware that your copy of Windows is registered to.

---

### Post by cottfcfan on 2012-06-02
Thanks for all your replies guys.
Think i'm probably better sticking to dual boot.

---

### Post by holycow131415 on 2012-06-02
dual booting is better anyway, esp if you want to play games. also you paid for windows, so why get rid of it completely? lol

---

### Post by traditionalist on 2012-06-02
> **cottfcfan said:**
> Thanks for all your replies guys.
Think i'm probably better sticking to dual boot.

I run Windows 7 x64 Ultimate in a virtual machine and it is great. But I bought the full retail version. I think you will have to do this, OEM versions wont work properly if at all as they are bound to the hardware.

---

### Post by cottfcfan on 2012-06-02
The problem is it takes out 3 of my 4 primary partitions, and I don't use it enough, to warrant it manipulating my computer to such a degree, so saving the recovery partition (just in case) and then installing it through virtualbox would have been ideal.
But if it can't be done i'll leave alone.

---

### Post by cottfcfan on 2012-06-02
> **traditionalist said:**
> I run Windows 7 x64 Ultimate in a virtual machine and it is great. But I bought the full retail version. I think you will have to do this, OEM versions wont work properly if at all as they are bound to the hardware.

Afraid I don't use Windows enough to spend money on a new Disc.

---

### Post by traditionalist on 2012-06-02
> **cottfcfan said:**
> Afraid I don't use Windows enough to spend money on a new Disc.

This is a fairly common problem. People save money by buying OEM versions of Windows without being aware of the consequences.  Unfortunate, but just how it is.

if you want it to work ( and be legal!) then you really need a full retail version.   I had the full retail version running on my machine anyway. I have now switched completely to Ubuntu, but I have the 7 running in a VM because I have two programs which require it.

I am not sure of the licensing details here, but I would have thought you could run the recovered disc in a VM ON THE SAME MACHINE without violating any license terms. It is after all still running on the same hardware. I don't know whether it will work but it's worth a try.

Just burn a recovery disc and try it in a virtual machine. You will still need your licence key to install it, but I don't see why it shouldn't work.

---

### Post by forrestcupp on 2012-06-02
> **cottfcfan said:**
> The problem is it takes out 3 of my 4 primary partitions, and I don't use it enough, to warrant it manipulating my computer to such a degree, so saving the recovery partition (just in case) and then installing it through virtualbox would have been ideal.
But if it can't be done i'll leave alone.

Well, you could always use GParted to get rid of all of your unused Windows partitions, including the recovery partition, and move things around to where you can absorb the space into your Ubuntu partition. If you ever need to reinstall Win7, you can always legally download the OEM version of the ISO and reinstall it straight to your hardware, which will work with your license and be legal.

If you do that, make sure to back up all of your important software first. Also, be aware that moving partitions around may cause you to have to restore GRUB.

---

### Post by Cheesemill on 2012-06-02
> **traditionalist said:**
> I am not sure of the licensing details here, but I would have thought you could run the recovered disc in a VM ON THE SAME MACHINE without violating any license terms. It is after all still running on the same hardware. I don't know whether it will work but it's worth a try.
You would think so, but that isn't the case. An OEM copy of Windows is licensed to the *physical* hardware, which isn't the same as running it on a VM as a VM  isn't physical hardware (it's virtual hardware).

Try dealing with the Microsoft licensing terms on a daily basis like I do for some of my clients and you will soon realise how convoluted the terms are :)

---

### Post by traditionalist on 2012-06-02
> **Cheesemill said:**
> You would think so, but that isn't the case. An OEM copy of Windows is licensed to the *physical* hardware, which isn't the same as running it on a VM as a VM  isn't physical hardware (it's virtual hardware).

It is still running on the same physical machine, which is what it is licensed for.   I can't find anything that specifies it must run on physical hardware.  Only on the same physical machine.

If it runs in a VM on the original machine for which it was licensed then I don't see a problem.

But I'm not a lawyer! :)

---

### Post by traditionalist on 2012-06-02
Since I was curious, I dug out one of my old OEM licences for one of the older XT boxes where I am now running Ubuntu 12.04.  It runs perfectly and it accepted the licence without a problem.  I have not yet activated it. I will try that and see what happens. If it is acceptable to Microsoft then that's fair enough I would imagine?

[[IMG]http://img403.imageshack.us/img403/1514/gerdrunningoraclevmvirt.th.png[/IMG]]("http://img403.imageshack.us/i/gerdrunningoraclevmvirt.png/")

It's my licence purchased with that machine, and it is running on that machine, albeit in a VM on that machine. So where might the problem be?

---

### Post by matt_symes on 2012-06-02
Hi

Image your current Windows partitions before you wipe Windows in case you need it again. Then you can recreate the partitions...just in case. Hard drive space is cheap.

If your going to consider this, use clonezilla or somesuch.

That's what i would do anyway.

Kind regards

---

### Post by Cheesemill on 2012-06-02
> **traditionalist said:**
> It is still running on the same physical machine, which is what it is licensed for.   I can't find anything that specifies it must run on physical hardware.  Only on the same physical machine.

If it runs in a VM on the original machine for which it was licensed then I don't see a problem.

But I'm not a lawyer! :)

An OEM copy is only licensed for the first machine it is installed on (which is defined by the manufacturer/model  of the motherboard). As a VM presents the Windows OS with a different  motherboard than the physical hardware then you are breaking the EULA.
I know it sounds crazy but that's just the way it is.

---

### Post by traditionalist on 2012-06-02
> **Cheesemill said:**
> An OEM copy is only licensed for the first machine it is installed on (which is defined by the manufacturer/model  of the motherboard). As a VM presents the Windows OS with a different  motherboard than the physical hardware then you are breaking the EULA.
I know it sounds crazy but that's just the way it is.

It is running on the same machine it was originally licensed for, with all the same hardware. The only difference is that it is running in a VM.  I can't find anything prohibiting that.  If you use that licence on some other machine in a VM you would be breaking the EULA.

In this case you quite obviously are not.

Extract from EULA;

BEGIN EXTRACT

SOFTWARE PRODUCT LICENSE
The term "COMPUTER" as used herein shall mean the HARDWARE, if the HARDWARE is a single computer system, or
shall mean the computer system with which the HARDWARE operates, if the HARDWARE is a computer system
component.
1. GRANT OF LICENSE. Manufacturer grants you the following rights, provided you comply with all of the terms and
conditions of this EULA:
• Installation and Use. Except as otherwise expressly provided in this EULA, you may install, use, access,
display and run only one (1) copy of the SOFTWARE on the COMPUTER. The SOFTWARE may not be used
by more than two (2) processors at any one time on the COMPUTER, unless a higher number is indicated on
the Certificate of Authenticity. You may permit a maximum of ten (10) ("Connection Maximum") computers
or other electronic devices (each a “Device”) to connect to the COMPUTER to utilize the services of the
SOFTWARE solely for File and Print services, Internet Information services, and remote access (including
connection sharing and telephony services). The ten (10) Connection Maximum includes any indirect
connections made through “multiplexing” or other software or hardware which pools or aggregates connections.
Except as otherwise permitted below, you may not use the Device to use, access, display or run the
SOFTWARE, the SOFTWARE’s User Interface or other executable software residing on the COMPUTER.
• Software as a Component of the Computer - Transfer. THIS LICENSE MAY NOT BE SHARED,
TRANSFERRED TO OR USED CONCURRENTLY ON DIFFERENT COMPUTERS. The SOFTWARE is
licensed with the HARDWARE as a single integrated product and may only be used with the HARDWARE. If the
SOFTWARE is not accompanied by new HARDWARE, you may not use the SOFTWARE. You may permanently
transfer all of your rights under this EULA only as part of a permanent sale or transfer of the HARDWARE, provided
you retain no copies, if you transfer all of the SOFTWARE (including all component parts, the media and printed
materials, any upgrades, this EULA and the Certificate of Authenticity), and the recipient agrees to the terms of this
EULA. If the SOFTWARE is an upgrade, any transfer must also include all prior versions of the SOFTWARE.
• Mandatory Activation. THIS SOFTWARE CONTAINS TECHNOLOGICAL MEASURES THAT ARE
DESIGNED TO PREVENT UNLICENSED OR ILLEGAL USE OF THE SOFTWARE. The license rights granted
under this EULA are limited to the first thirty (30) days after you first run the SOFTWARE unless you supply
information required to activate your licensed copy in the manner described during the setup sequence (unless
Manufacturer has activated for you). You can activate the SOFTWARE through the use of the Internet or telephone;
toll charges may apply. You may also need to reactivate the SOFTWARE if you modify your HARDWARE or alter
the SOFTWARE.
• Security Updates. Content providers are using the digital rights management technology (“Microsoft DRM”)
contained in this SOFTWARE to protect the integrity of their content (“Secure Content”) so that their


END EXTRACT

---

### Post by linux653 on 2012-06-02
> **Cheesemill said:**
> No, it's not possible I'm afraid. Even if it was you would be breaking the terms of your Windows license agreement.

An OEM copy of Windows (like the one your recovery partition contains) is only licensed to run on the actual hardware. To install a Windows VM you need a full retail copy of Windows and the installation CD that comes with it.

What is the difference. You are running it on the **same physical machine**. I've done this with a Win XP and 7 CD from Dell. It works perfectly fine and I had no problems with activation.

---

### Post by forrestcupp on 2012-06-02
> **traditionalist said:**
> Since I was curious, I dug out one of my old OEM licences for one of the older XT boxes where I am now running Ubuntu 12.04.  It runs perfectly and it accepted the licence without a problem.  I have not yet activated it. I will try that and see what happens. If it is acceptable to Microsoft then that's fair enough I would imagine?

[[IMG]http://img403.imageshack.us/img403/1514/gerdrunningoraclevmvirt.th.png[/IMG]]("http://img403.imageshack.us/i/gerdrunningoraclevmvirt.png/")

It's my licence purchased with that machine, and it is running on that machine, albeit in a VM on that machine. So where might the problem be?
XP was a lot more lenient than later versions. It can be done with Win7, too, but it's just about where your conscience is.

---

### Post by traditionalist on 2012-06-02
> **forrestcupp said:**
> XP was a lot more lenient than later versions. It can be done with Win7, too, but it's just about where your conscience is.

Doubtless, I have a full retail version of Windows 7 x64 BIT Ultimate running in a VM on this machine, and I have no doubt that an OEM version would run as well. I don't know about licencing that, but I can install my full retail version on any machine I like, as long as I stick to the licence agreement.

---

