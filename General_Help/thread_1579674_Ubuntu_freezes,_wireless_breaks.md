---
title: "Ubuntu freezes, wireless breaks"
date: 2010-09-22
forum: General Help
---

### Post by sedam on 2010-09-22
I have recently switched from XP to Ubuntu 10.4 on my laptop Toshiba Satellite p200. Never used Linux before.
I am installing all the updates as soon as they issued.

For the first two weeks everything was working fine. 
During last seven days I am having serious problems, these happens more than 5 times a day:
- My wireless connection gets lost and I cannot connect without restarting
- My screen freezes, keyboard and mouse also, so I need to press power button to shut down the computer. This usually happens 10-20 minutes after the wirelles problem, but sometimes before, so I don't know if these two issues are connected.

How should I troubleshoot this issue? 

Is it possible that my machine is infected with virus or rootkit? I have scanned it with Clamav, it found nothing, just test files. What is the best way to scan disk for viruses? 

I have tried to found meaning in error logs in /var/log/messages, but I have thousands of messages there which I don't understand.

I have disabled visual effects (thought maybe they cause display to freeze), but it still happens. 

Any help will be appreciated.

---

### Post by bryanfblareunion on 2010-09-22
well first of all, linux with wireless: not good. i had a ton of problems with getting my wireless working. linux has a few problems with connecting to a wireless network correctly. 

however, there is one thing that you can try: boot into an earlier kernel. This helped me. Now they updated things and i can connect fine in all kernels but you could try using an ealier one.

---

### Post by sedam on 2010-09-23
> **bryanfblareunion said:**
> well first of all, linux with wireless: not good. i had a ton of problems with getting my wireless working. linux has a few problems with connecting to a wireless network correctly. 

however, there is one thing that you can try: boot into an earlier kernel. This helped me. Now they updated things and i can connect fine in all kernels but you could try using an ealier one.

At the boot, I don't have any earlier kernel listed. I don't think there was kernel updates since I installed it. Is there a way to find out something from some error logs? 
Please help me, I don't know where to start and it is driving me crazy. Last two days  wireless became stable, but the display is still freezing several times a day.

---

### Post by sikander3786 on 2010-09-23
> 
Is it possible that my machine is infected with virus or rootkit? I have scanned it with Clamav, it found nothing, just test files. What is the best way to scan disk for viruses?


Not possible. You'll hardly see any Linux virus ever. Virus scan is un-necessary.

There should have been some kernel updates installed. Press and hold down the Shift key as soon as the computer gets past the Bios screen and choose an older kernel. The 3rd one on the list I think.


To be more accurate, when do you get a freeze? I mean at regular or random intervals? Do you remember any specific programs running then? If you can, you should try to disable the wireless connection and use your Laptop for some time to see if that is not causing the problems.

---

### Post by sedam on 2010-09-23
> **sikander3786 said:**
> 
There should have been some kernel updates installed. Press and hold down the Shift key as soon as the computer gets past the Bios screen and choose an older kernel. The 3rd one on the list I think.

I have two hard drives, with XP on the first one and still haven't dealt with booting, so to boot Ubuntu I press F12 and choose to boot from second disk. To follow your instructions I have pressed and held down Shift key after choosing to boot from second disk (several times) but got the same menu as usual with following options:

Ubuntu, with Linux 2.6.32-24-generic-pae
Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

I tried using ESC instead of SHIFT, but all it does is preventing highlighted entry to be chosen automatically after xx seconds.
Should I choose that one marked recovery mode? What it's for?

I run in terminal: dpkg --list | grep linux-image
And I got this:
ii  linux-image-2.6.32-24-generic-pae    2.6.32-24.43   Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic-pae              2.6.32.24.25   Generic Linux kernel image

Does that mean that I have older kernel installed - 2.6.32.24.25? Were you telling me to boot that one?

Sorry if I am missing something obvious, I'm new to Linux.

> **sikander3786 said:**
> 
To be more accurate, when do you get a freeze? I mean at regular or random intervals? Do you remember any specific programs running then? If you can, you should try to disable the wireless connection and use your Laptop for some time to see if that is not causing the problems.

No regular intervals, sometimes after 5 minues since start, soemtimes after several hours, sometimes 5-20 minutes after wireless broke. Sometimes after wireles broke and couldn't connect, I disabled it and continued working on LAN but freezing still happened. The only program that was running every time was Firefox. I open it as soon as I turn computer on and exit it just before shutting computer down.

---

### Post by sikander3786 on 2010-09-23
Troubleshooting and identifying problems like this is never easy. You need to go step by step. Most probably it is a graphics problem. Which graphics card have you got and which drivers are you using with it?

Check the xorg.log file under var/log/xorg for anything you find weird or post it here if you don't find anything. Post the most recent one and after the freeze has occured atleast once in the current date.

---

### Post by sedam on 2010-09-24
Hi, thank you for trying the help.
My graphic card is ATI Mobility Radeon HD 2600
Driver Packaging Version: 8.723.1-100408a-098580c-ATI
2D Driver Version: 8.72.11

This info is form ATI Catalyst Control Center. 

In the attachment to this post I've inculded:
- Screenshot of ATI Catalyst Control Center with more info
- Screenshot of Syanptic after ATI search
- xorg.0.log - since last restart, after the last freeze
- xorg.0.log.old - before last restart, before the last freeze

Logs are zipped because .txt formats were over file size limit for .txt upload.

---

### Post by sedam on 2010-09-25
I have installed graphic card driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

Should I now uninstall some of the earlier drivers? From that synaptic screenshot?

When I scroll in FireFox, now with new driver, it scrolls in waves, how to stop that? It is driving me crazy.
I have tried checking/unchecking smooth and auto scrolling in FF prefernces but it is the same.

---

### Post by sedam on 2010-09-27
UPDATE: I removed fglrx driver and there's no more "waving". Screen haven't froze since installing driver from AMD, I hope that's it.

---

### Post by sedam on 2010-09-28
Unfortunately, that's not it. Today it is freezing again. Wireless is also again loosing connection and won't connect without restarting. Any ideas?

---

