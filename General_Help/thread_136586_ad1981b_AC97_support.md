---
title: "ad1981b AC97 support"
date: 2006-02-26
forum: General Help
---

### Post by ibarro on 2006-02-26
hi to all. been using ubuntu 5.10 for 3 months now. basically nothing complicated just office work and some multimedia stuff on my desktop.  just installed it on my wife's laptop a NEC versas820. with the ff specs centrino 1Ghz, 256 ram, intel graphics, audio: AD 1981b, irewire, usb. Been convincing her to try this OS and finally i did but bummer!... installation was a breeze did not encounter any problem. all module were ok on loading up including ALSA. but when i try to play mp3 there is no sound.  Like to know if the ad1981b chipset is supported by ubuntu or any patches or other drivers i need to make it work.  (If not ill just reinstall windows). Need your expert advise on this.

---

### Post by huckem on 2006-02-26
What program are you using to play MP3's?  Do other system sounds work?

---

### Post by ibarro on 2006-02-28
im using xmms to play mp3. have downloaded LAME still no sound. It also has no sound upon boot up when you ubuntu desktop is displayed.  tnx for the reply. Hope you could help.

---

### Post by ibarro on 2006-02-28
Does ubuntu or any other distros support this audio controller chipset:soundmax ad1981b? how do i know if it detected on the laptop NEC versa s820? any help out there?:(

---

### Post by tinker312 on 2006-02-28
HI, 

Would it possible for you to type "lspci" in a terminal then copy and paste the results in this thread? I think you would find more help if we had details about your system. 

Thanks . . . 
John

---

### Post by ibarro on 2006-03-02
here the output of my lspci

0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]0000:02:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)0000:02:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)0000:02:05.2 FireW

appreciate your help. thanks

---

### Post by ibarro on 2006-03-04
Anyone have a solution why my audio controller has no sound. Really want ubuntu to work fully on my laptop.

---

### Post by ibarro on 2006-03-06
i guess its time for me to move on and remove breezy for the moment. Wil reinstall windows on our laptop for now until have a solution to the sound problems. Maybe i'll just wait for the latest version of ubuntu it might probably solve my problem.:(

---

### Post by xoros on 2006-06-19
Go here and you will see AD1981B:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Analog_Devices#matrix)

Then you see it uses either this snd-intel8x0:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=intel8x0)

Or this snd-via82xx:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Analog+Devices&card=.&chip=AD1881%2C+AD1881A%2C+AD1885%2C+AD1886%2C+AD1887%2C+AD1980%2C+AD1981A%2C+AD1981B%2C+AD1985&module=via82xx)

---

