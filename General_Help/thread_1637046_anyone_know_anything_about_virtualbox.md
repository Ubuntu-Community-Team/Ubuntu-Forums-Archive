---
title: "anyone know anything about virtualbox"
date: 2010-12-03
forum: General Help
---

### Post by CarNut1981 on 2010-12-03
I am looking for help with virtualbox, I am trying to put windows 2000 on it. I am getting stopped at failure to formate the partition if I can get any help that would be great thanks.

---

### Post by TheOnlyMrK on 2010-12-03
> **CarNut1981 said:**
> I am looking for help with virtualbox, I am trying to put windows 2000 on it. I am getting stopped at failure to formate the partition if I can get any help that would be great thanks.

That's a problem with Windows 2000, not VB, and trust me when I say Windows 2000 has more than enough problems, but either way I assume you have your reasons for choosing Windows 2000 so can you give me more details on what you're doing/what the error(s) are?

---

### Post by slooksterpsv on 2010-12-04
How large is the partition? What filesystem are you formatting it to: NTFS or FAT32? Do you have VT-x or that enabled? Is this a CD or an ISO?

Those are my questions

---

### Post by CarNut1981 on 2010-12-05
was having the same problem with Windows 98, using anything newer then XP is not possable on my old system. the reason I would like this to work is cause WINE in my opnion is useless. what I am doing is using an Windows 2000 ISO I set everything up and got the Windows setup running and when I went it asks to format the partition it comes back with something to the effect of failure to format partition.

---

### Post by CarNut1981 on 2010-12-05
I've tryed both FAT and NFTS, and I am using an 8 GB non fixed partition

---

### Post by Dave_L on 2010-12-05
Are you using SP4?  My Win2000 .iso is SP3, so as soon I install Win2000 on VirtualBox, I apply the SP4 .iso.

---

### Post by slooksterpsv on 2010-12-05
Does your system support Virtualization? If not make sure its disabled in the properties of the VM, that can give you strange sporadic errors.

---

### Post by TheOnlyMrK on 2010-12-05
I'd recommend installing Windows XP, I've used Windows 2000 on multiple computers and VMs and it's given me more trouble than every computer I ever had, but if you really want to stick to 2000 then I recommend booting the VM from the Windows XP disk/.iso, have it format the drive, restart the computer with the 2000 CD/.iso and then install. The Windows formatter is kinda buggy on pre-Windows XP install CD's, so I prefer to use XP or Windows 7's formatters.

---

### Post by CarNut1981 on 2010-12-06
my only consern with XP is though this computer can run it, one of the main reasons I switched to Xubuntu is because XP is slower then cold molassas going up hill. I am only running A P3 I will try XP but I have a feeling its going to be slow

---

### Post by TheOnlyMrK on 2010-12-07
> **CarNut1981 said:**
> my only consern with XP is though this computer can run it, one of the main reasons I switched to Xubuntu is because XP is slower then cold molassas going up hill. I am only running A P3 I will try XP but I have a feeling its going to be slow

A Pentium III running a VM?.. :lolflag: Do you really need to have a VM running on this computer? A single core computer alone is terrible at running multiple OS's, then add in it doesn't have VM support and it can't be any faster than 1.4GHz everything will pretty much go to a halt with all those limitations. Can you not multiboot Windows XP/2000 and Xubuntu? You will get much better performance.

---

### Post by HiImTye on 2010-12-07
I couldnt see even a coppermine max overclocked running virtual box with any sort of desirability

---

### Post by slooksterpsv on 2010-12-07
??? I used to run VMs on an AMD Duron 1.1GHz with 384MB of RAM. He wants to run VMs so what? His hardware is capable, just not VT-x capable. Let's try and help him out instead of talking about the hardware.

Have you tried another OS like TinyCore (just as a simplistic one), because, like someone stated at the beginning, it could be a problem with the ISO file you have.

---

### Post by gobbles414 on 2010-12-07
Hi CarNut1981...

Have you considered "dual-booting" Windows 2000 alongside Xubuntu? You will pay a "performance penalty" regardless of which OS is in the virtual machine -- it could be DOS, and there would still be a performance penalty!

Also, perhaps XP was getting slow due to lack of software maintenance? According to the [http://support.microsoft.com/kb/304297](http://support.microsoft.com/kb/304297) and [http://support.microsoft.com/kb/314865](http://support.microsoft.com/kb/314865) at Microsoft, the system requirements for Windows 2000 and Windows XP differ only slightly. Furthermore, XP is heavily based on Windows 2000, and becomes even more similar if one disables XP's enhanced graphics features. Just for your information, I recommend running 3rd-party maintenance programs such as ccleaner and defraggler at least once per month, a full "disc check" at least once every 6 months, and a full reinstall of the operating system and all software in 12-24 month cycles (depending on how much you use the computer, and for what tasks).

Hope this helps!

---

### Post by TheOnlyMrK on 2010-12-07
> **slooksterpsv said:**
> ??? I used to run VMs on an AMD Duron 1.1GHz with 384MB of RAM. He wants to run VMs so what? His hardware is capable, just not VT-x capable. Let's try and help him out instead of talking about the hardware.

Have you tried another OS like TinyCore (just as a simplistic one), because, like someone stated at the beginning, it could be a problem with the ISO file you have.

We are trying to help him by suggesting better alternatives. Yeah I could run a VM on my 500MHz AMD K6 server but would it be reasonably usable? Haha no.

---

### Post by slooksterpsv on 2010-12-07
> **TheOnlyMrK said:**
> We are trying to help him by suggesting better alternatives. Yeah I could run a VM on my 500MHz AMD K6 server but would it be reasonably usable? Haha no.

With TinyCore, sure! Haha.

---

