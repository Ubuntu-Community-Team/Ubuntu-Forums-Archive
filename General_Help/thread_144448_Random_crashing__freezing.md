---
title: "Random crashing / freezing"
date: 2006-03-14
forum: General Help
---

### Post by Spookster on 2006-03-14
Hello,

I've had Ubuntu installed for a couple of months now and no major problems.

However, in the past couple of weeks I've noticed the system occasionally crashes in one of three ways...

1. Returns me to the login screen
2. Completely freezes (cannot move mouse, cannot connect from another system via SSH) with horizontal lines of dots superimposed on the screen.
3. Powers down completely.

(2) is the most common.

This has been getting more and more frequent, and today it has happened about once an hour. The last time it happened was only seconds after logging on.

The problem seems to occur most often when using Firefox, often when scrolling through pages or clicking on links. It's also happened while using GIMP too. It doesn't seem to happen when I am away from my computer.

I've looked in /var/log/messages and syslog but there doesn't seem to be any obvious pattern to the last messages displayed before the system dies.

I've run the memtest from the GRUB menu which didn't report any errors.

Any help would be appreciated!

---

### Post by Spookster on 2006-03-14
Suspecting that this must be hardware related I've just removed one of the two 256Mb sticks of RAM from my PC and it hasn't crashed yet (after about 30 minutes). Bizarrely, it also seems to be running faster :-k 

Anyways, I'll post again here if it carries on crashing :rolleyes:

---

### Post by Nonney on 2006-03-14
I had problems with hanging and after searching thru the forums found the following which worked for me.

[COLOR="Blue"][I][B]** Update **

Having just checked the info below, I have found that as a result of an kernel update yesterday, the additional kernel switches have been removed, and I still haven't had a hang - the services I had disabled via BUM have also been re-instated - which is slightly worrying.

I have universe, multiverse and backports enabled in my /etc/apt/sources.list 

** End Update **[/B][/I][/COLOR]

[B]
Using your chosen editor, edit[/B]

/boot/grub/menu.lst

**Go down, and on the kernels list, on the kernel line add the following:**

noapic
nolapic
pci=noacpi

**the kernel line will now look something like:**

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet noapic nolapic pci=noacpi splash
initrd		/initrd.img-2.6.12-10-k7
savedefault
boot

Other suggestions have been to disable boot services using BUM (Boot Up Manager) or Services from the Administration menu to disbale the following:

acpid
apmd
powernowd
acpi-support

I did both and haven't had a hang for a week.

Good luck

---

### Post by henriquemaia on 2006-03-14
[QUOTE=Nonney]I had problems with hanging and after searching thru the forums found the following which worked for me.

[COLOR="Blue"][I][B]** Update **

Having just checked the info below, I have found that as a result of an kernel update yesterday, the additional kernel switches have been removed, and I still haven't had a hang - the services I had disabled via BUM have also been re-instated - which is slightly worrying.

I have universe, multiverse and backports enabled in my /etc/apt/sources.list 

** End Update **[/B][/I][/COLOR]

[B]
Using your chosen editor, edit[/B]

/boot/grub/menu.lst

**Go down, and on the kernels list, on the kernel line add the following:**

noapic
nolapic
pci=noacpi

**the kernel line will now look something like:**

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet noapic nolapic pci=noacpi splash
initrd		/initrd.img-2.6.12-10-k7
savedefault
boot

Other suggestions have been to disable boot services using BUM (Boot Up Manager) or Services from the Administration menu to disbale the following:

acpid
apmd
powernowd
acpi-support

I did both and haven't had a hang for a week.

Good luck[/QUOTE]

Hi,

I was having the same problem. My system hanged whenever I had a full system load (2 CPUs working at 100%). I followed your suggestions and it now my system is stable again. Does anyone have an idea why this happens? On my system I noticed that this problem happened more when I installed folding@home. My system would hang just 5 minutes after a reboot.

One more thing, on my grub I did not add
```
pci=noacpi
```
as It made my system hang just a minute after rebooting.

I also would like to know more accurately what makes my system more stable now. Maybe I'll turn on the services again in order to troubleshoot this.

Anyway, thanks for your tip.

---

### Post by Spookster on 2006-03-14
Thanks for the replies - interesting reading.

Well my system hasn't crashed since I removed one of the RAM modules. I'm going to look further at this tomorrow but for now, I'm happy.

The only odd thing was that the memtest results were all fine. :confused:

Thanks again for the help.

spookster

---

### Post by WoodyMahan on 2006-03-14
Bad RAM perhaps?  Or maybe the 2 DIMM sticks weren't identical?  I've seen this as the culprit in other systems.

---

### Post by Spookster on 2006-03-15
Turns out I have a faulty motherboard - leaking capacitors. Fortunately I've discovered the PC is still under warranty so Dell are fixing it. :)

So, sorry for posting this in an ubuntu forum when it's nothing to do with ubuntu!

---

### Post by tormod on 2006-05-10
[QUOTE=Nonney]as a result of an kernel update yesterday, the additional kernel switches have been removed[/QUOTE]
If you actually read the comments in /boot/grub/menu.lst you'll see that you should not add your own options to the "Automagic Kernel List". You should add them to the "# kopt=" line (yes, there should be #), so that the kernel update routines will see them and add them to the new "automagic" list.

---

