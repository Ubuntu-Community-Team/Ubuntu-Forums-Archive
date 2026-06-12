---
title: "Weird problem with kernel 2.6.35-24 on 64bit Maverick"
date: 2011-01-14
forum: General Help
---

### Post by PC_load_letter on 2011-01-14
The following is what happened earlier today on my Dell laptop running Ubuntu 10.10 64bit w/ kernel 2.6.35-24. I'm typing this right now from the same system but the kernel is 2.6.35-22 instead, where none of the issues has been observed. 

============================
1- A message was displayed saying that I'm running out of disk space and I have only 1.7 GB left. I knew it was not true as I was sure that I had about 14 GB left on this partition.

2- The applications that were running at that moment were: Google Chrome, Evince, and Thunderbird. Having 4GB of ram, that was nothing. 

3- The sound of the hard drive started to get a bit louder and coarser, otherwise it is usually pretty quiet. 

4- I started the Disk Usage Analyzer to see if there was indeed a problem w/ disk space. It took forever and the system was becoming very sluggish.

5- So, I CTRL+ALT+Bkspace to logout of the session, tried unsuccessfully to login 3 times (no way I could have messed up my password that many times).

4- Finally I was logged in, started Disk Usage Analyzer again, but then was hit with a warning that my available disk space is now 4k!!!!???? System started to be sluggish again and I noticed the windows losing their borders and upper title bar. 

5- I rebooted, but then was greeted with an error message (right after the GRUB menu) saying that I should consider booting with the "irqpoll" kernel option as there was an irq conflict/error. 

6- Session started BUT:
   - The stored password for my wireless router was gone, had to enter it again to connect to my home wlan.
   - USB flash drives mounted under a generic usb0 name, and I couldn't unmount them from the right-click menu getting an error message saying that I am not root!!! This was fixed when I uninstalled **usbmount** but this problem never happened before.
   - The terminal profile settings were gone, defaulted to original.
   - Some Compiz settings were defaulted to original values. 

7- I ran the Disk Usage Analyzer again and it reported that I have 14.7 GB of disk space ??!!!!!!!

8- I installed **gsmartcontrol** to check the integrity of the drive. Did the long test, took more than 2hrs, and there were no errors. 

Now, I still get the same irq error message at startup + weird hard disk noise, **ONLY** when booting with the 2.6.35-24 kernel. 
=========================

Anyone has any clue what is happening here? Any idea how to report this if it was a bug? 

Thanks.

---

### Post by PC_load_letter on 2011-01-15
The system is back to normal again as if nothing happened, but it was a very intense couple of hours when I was experiencing all this. 
If anyone had seen this kind of behavior before, please post and let me know. Thanks.

---

### Post by akand074 on 2011-01-15
> **PC_load_letter said:**
> The system is back to normal again as if nothing happened, but it was a very intense couple of hours when I was experiencing all this. 
If anyone had seen this kind of behavior before, please post and let me know. Thanks.

Never had that time of behavior before. But the first time I installed the 2.6.35-24 kernel, my system wouldn't boot. I have a text boot, and it booted to the login, after logging in and running "startx" it just crashed every time. I ended up booting back into the -23 kernel and everything was fine.

Oddly, yesterday night on the -23 kernel I decided to reboot my computer because my flash videos were getting sluggish, after booting it hung when I typed 'startx' every time. Couldn't fix it and I tried other kernels, ended up doing a wipe and install. Luckily it took not more than an hour because I had saved my packages from synaptic and I have /home on a separate partition.. but really weird. Now after a clean install I'm on the -24 kernel and everything is running fine so far.

---

