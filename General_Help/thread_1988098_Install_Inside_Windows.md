---
title: "Install Inside Windows"
date: 2012-05-26
forum: General Help
---

### Post by ki4jgt on 2012-05-26
My dad has a Windows XP box from HP. He currently uses it to watch Netflix and surf the web. Every time I come over for maintainance, it is loaded with spyware and viruses from those "Click Here to scan your computer for viruses" ads. Now, I've convinced him to use Ubuntu for his surfing needs and Windows for Netflix only. I tried installing Ubuntu from the liveCD. I gave Ubuntu around 25 gigs of space to work with. The Windows bootloader refuses to allow Ubuntu an entry though. It literally will not show up. I've tried a lot of different methods to bypass it but none of them have worked. However, the last time I dualbooted his computer with Ubuntu I was able to do so by installing it inside of Windows.

I read online about doing this in the Windows terminal
```
K:\wubi.exe --force-wubi
```

The install inside Windows option appeared perfectly. The problem I'm having now is, it's downloading a 64-bit AMD iso and his computer is 32-bits. It completely ignored the OS on the flashdrive and went straight to downloaded the 64-bit.

---

### Post by bcbc on 2012-05-27
If it's downloading 64bit then his computer is 64bit. I haven't seen any case where Wubi gets this wrong - probably the windows OS is 32 bit but that doesn't matter.

If you want to find out why it ignored the flash drive you can check the log file in the %TEMP% directory (wubi-12.04-rev266.log)

When you install a normal dual boot (not wubi) it replaces the windows bootloader in the drive MBR with grub2. Windows can't stop this. There may be some software in windows that replaces that after you reboot into Windows, but it wasn't clear what you meant by "The Windows bootloader refuses to allow Ubuntu an entry though."
I'm sure you could figure that out and do a normal dual boot if you wanted to (probably a better option)

---

### Post by 3rdalbum on 2012-05-27
> **ki4jgt said:**
> 
The install inside Windows option appeared perfectly. The problem I'm having now is, it's downloading a 64-bit AMD iso and his computer is 32-bits. It completely ignored the OS on the flashdrive and went straight to downloaded the 64-bit.

A couple of notes:

1. Congratulations, your Dad is the proud owner of a 64-bit computer, and he never even knew it! If Wubi is downloading the 64-bit edition, then the computer has a 64-bit CPU. Doesn't matter if XP is 32-bit.

2. If you burn the ISO to a CD, and then insert the CD while the computer is running, you can run Wubi from the CD and it should, I believe, install the version on the CD.

3. A real dual-boot will be better if you can find out why GRUB isn't appearing. If the Windows system is full of malware, then it may completely crash. If the Windows partition crashes, Ubuntu (as installed with Wubi) can't mount it, and therefore can't boot. If you do a real dual-boot then this limitation does not affect you.

---

### Post by miasmablk on 2012-05-27
if you mean the windows bootloader doesn't show ubuntu at startup, one simple thing you might try of course is booting into XP recovery and run "bootrec /fixmbr" (without the " ") from the command utility.

---

### Post by ki4jgt on 2012-05-27
This all happened after a complete system reinstall. One of the first things I did when he got his computer was review the specs. It has 4 gigs of RAM also. Both Ubuntu and Windows are reporting 900 megs and where Windows usually tells the processor, it's blank. I'm assuming something has gone terribly wrong on the hardware end of the computer and not the software. I guess now's as good a time as any to renew my computer engineering skills. I don't see how the RAM could've come unsettled though as the computer's basically been sitting in the same place for the last 8 years (probably longer). No one's touched it (except to press the power button, insert CDs and USBs). So I am assuming it to be wrong as something is really fishy about the specs the computer is reporting. How long have they made 64-bit PCs?

---

