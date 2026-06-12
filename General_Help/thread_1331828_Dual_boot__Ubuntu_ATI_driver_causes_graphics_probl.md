---
title: "Dual boot : Ubuntu ATI driver causes graphics problems in Windows XP?"
date: 2009-11-19
forum: General Help
---

### Post by dempo on 2009-11-19
Hi, I am new to Ubuntu. Please forgive the lengthy post…
   
  I tried to create a dual boot PC by installing install Ubuntu 9.04 64-bit on a second hard drive, with Windows XP previously in perfect working order on the first hard drive. I am now experiencing major problems in Windows XP after trying to update the ATI graphics drivers in Ubuntu.
   
  Hardware:
   
  CPU:                           AMD Athlon 64 3500+, 2200 MHz
  RAM:                          1024 MB DDR, 400 MHz
  Graphics Card:            GV-RX60X128V Radeon X600XT
  Motherboard:              nVidia nForce4 Socket 939
  Monitor:                      AOC 19” LM925
  Hard Drive 1:              Windows XP, Seagate 200 GB, Serial ATA
  Hard Drive 2:              Western Digital Caviar Blue 640 GB, Serial ATA
   
  ___________________________________________________________________
   
  What I did:
   
  Physically installed a second hard drive inside my computer.
   
  Loaded Ubuntu Jaunty 9.04 64-bit from CD.
   
  Installed Ubuntu to second hard drive, formatting the hard drive first.
   
  Downloaded and updated latest Ubuntu packages with Update Manager or Ubuntu equivalent.
   
  Downloaded Karmic Koala and upgraded to Ubuntu 9.10.
   
  Synaptic Package Manager: installed ‘x-org-driver-fglrx’
  [FONT=&quot] [/FONT]
 Command prompt: [FONT=&quot]sudo aticonfig --initial[/FONT][FONT=&quot][/FONT]
   
  This is meant to configure the X.org configuration file to work with the ATI drivers.
   
  Message:         No adapters found (I think).
   
  Rebooted to Ubuntu.
   
  Serious problems then occurred with mouse and keyboard, e.g. Alt-Tab didn’t work, mouse clicks not recognised in Ubuntu GUI and in Firefox.
   
  Command prompt: [FONT=&quot]sudo dpkg-reconfigure xserver-xorg[/FONT][FONT=&quot][/FONT]
   
  Message:         None at all.
   
  The file ‘[FONT=&quot]/etc/X11/x.org[/FONT]’ didn’t appear to have any changes written to it.
   
  Command prompt:
   
  [FONT=&quot]sudo mv /etc/X11/x.org.conf.original-0 /etc/X11/xorg.conf[/FONT]
   
  Message: File not found. Not surprising since the [FONT=&quot]x.org.conf.original-o[/FONT] file didn’t exist. Another older file did exist which had a name similar to [FONT=&quot]xorg.conf[/FONT], but this file appeared to be identical to the existing [FONT=&quot]xorg.conf[/FONT], and didn’t appear to have any configuration settings in it.
   
  Synaptic Package Manager: uninstalled ‘x-org-driver-fglrx’
   
  Reinstalled Ubuntu Jaunty 9.04 64-bit from CD, twice, including format of second hard drive.
   
  Mouse clicks not recognised during installation screens.
   
  After installation, in Ubuntu Jaunty, same problems with mouse and keyboard.
   
  Rebooted to Windows XP. Problems with mouse and keyboard in Windows XP.
   
  Rebooted from Windows XP CD.
   
  Entered recovery console.
  Typed ‘[FONT=&quot]fixboot[/FONT]’ and ‘[FONT=&quot]fixmbr[/FONT]’ to removed GRUB.
   
  Rebooted to Windows XP. Still problems with mouse and keyboard.
   
  Deleted Ubuntu partitions and formatted second hard drive with NTFS.
   
  Problems remain in XP. Mouse clicks and keyboard play up, especially in Firefox 3.5.5, Internet Explorer 8 and Adobe Reader. Adobe Reader also doesn’t load properly, hangs, etc.
   
  ________________________________________________________________
   
  I really don’t know what the cause of the problem is and I’m stumped. I didn’t reboot to Windows XP until after I installed Ubuntu a few times, so it is possible that the installation of the second hard drive is the cause of the problems in Windows XP, but I really just don’t think it is. The second hard drive, now NTFS, works fine, and the new [graphics] problems in XP seem too similar to those I encountered in Ubuntu.
   
  Perhaps the Uunbu ATI drivers somehow affected firmware on my Radeon graphics card, which persists between different operating systems?
  Or, the BIOS has somehow been altered?
  Or, maybe some data from the Ubuntu ATI graphics device driver was left in RAM while rebooting from Ubuntu into Windows XP (clutching at straws…).
   
  I don’t know much about hardware but I am pretty good with software, especially in Windows. I am probably now gonna format the first drive, which contains Windows XP, and reinstall XP, because several applications continue to freeze, hang, etc. However, I am not completely sure that this will fix the problem, since I don’t know how (or even if) it persisted, or was transmitted, between operating systems and hard drives/partitions.
   
  If anyone has an idea of what might be going on, I would greatly appreciate any advice. (I apologise if this post is more related to Windows XP than Ubuntu.)
   
  Thanks.

---

### Post by bodhi.zazen on 2009-11-19
I do not know the cause of your problem, but unstalling Ubuntu should not affect windows XP in this way ...

And you have problems across operating systems ....

Hardware problem ? 

Did you loosen anything or disconnect something when installing the new HD ?

---

### Post by dempo on 2009-11-19
> ** said:**
> I do not know the cause of your problem, but unstalling Ubuntu should not affect windows XP in this way ...

And you have problems across operating systems ....

Hardware problem ? 

Did you loosen anything or disconnect something when installing the new HD ?


Hi bodhi.zazen,

I don't think there is anything physically wrong with any hardware, since all was OK in XP before, the new hard drive appears to work fine in XP, and after I installed the new HD, I was careful to replace all other cables and cards exactly as they were before. 

I am going to reinstall XP, because I need my PC to work now and I don't have days to spend troubleshooting.

My main concern, hopefully unjustified, is that after formatting the primary hard drive, the problem lingers somewhere in firmware or BIOS settings? I just don't know enough about that stuff: can the Ubuntu Synaptic Package Manager or 'aticonfig' command somehow alter firmware or BIOS?

dempo

---

### Post by dempo on 2009-11-20
OK, I formatted the the primary hard drive and reinstalled XP on it. Everything is OK, so no lasting damage.

Weird, though. Won't be moving to Ubuntu just yet...

---

### Post by darkksyde on 2009-11-20
I think the problem was just coinsidental

---

