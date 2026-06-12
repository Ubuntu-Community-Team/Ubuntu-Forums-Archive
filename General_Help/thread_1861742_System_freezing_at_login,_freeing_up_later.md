---
title: "System freezing at login, freeing up later"
date: 2011-10-16
forum: General Help
---

### Post by ratcheer on 2011-10-16
I had a lot of trouble with system freezes after trying to upgrade from 11.04 to 11.10 64-bit. Description of problems in this thread:

[http://ubuntuforums.org/showthread.php?t=1859108](http://ubuntuforums.org/showthread.php?t=1859108)

After I moved everything to my former Oneiric testing instance, everything seemed ok all afternoon. I rebooted several times with no problems at all.

But late this evening, after rebooting again, the system froze totally at the LightDM login screen. I rebooted again and the same thing happened. I rebooted to recovery mode, and that screen was frozen, too!

I rebooted to a Parted Magic CD. There was a very short freeze after it first started, but it cleared up, quickly. I poked around in Parted Magic for a while, but could find nothing wrong. I ran fsck of my Oneiric system partition, and it seemed to be fine.

I rebooted to Arch Linux and it froze at the login screen, too! I was sitting there wondering what on earth was going wrong, when I absently tried to type my login again and it started taking it. Hmmm...

I rebooted to Oneiric, got to the frozen LightDM login screen, and timed to see when and if it would eventually let me in. I typed the first character of my password every 5 seconds until it accepted it, which was at 65 seconds. Then, I was able to complete my login and everything seems normal after that.

Has anyone else seen or heard of this? It is apparently unrelated to Ubuntu, as Arch is similarly affected and Parted Magic is slightly affected. Neither Ubuntu nor arch were having this problem a few hours ago.

Please help, this is not right.

Tim

---

### Post by ratcheer on 2011-10-16
Bump.

There was never any sign of this freezing on my PC until I ran the Natty to Oneiric upgrade. And, I have not even so much as looked at my BIOS settings in weeks.

Does anyone have any idea at all?

Tim

---

### Post by ratcheer on 2011-10-16
Ok, I have partially solved the problem. Disconnecting the 2 TB Seagate external USB drive lets me log in without the freezing.

So, the nest question is, what's up with that? I have been using that drive for months with no issues. Yes, I know something could have gone wrong with it, but after the freeze up clears, it also seems to be working normally.

Here are some messages from the syslog:

```
usb 1-1.3: device descriptor read/64, error -110 
Oct 16 12:54:32 tim-oneiric kernel: [   32.038038] usb 1-1.3: new high speed USB device number 4 using ehci_hcd 
Oct 16 12:54:32 tim-oneiric kernel: [   32.155413] 
MediaState is connected
```Then, somewhat later:

```
usb 1-1.3: device descriptor read/64, error -110 
Oct 16 12:55:02 tim-oneiric kernel: [   62.476664] usb 1-1.3: new high speed USB device number 5 using ehci_hcd 
Oct 16 12:55:07 tim-oneiric kernel: [   67.498982] usb 1-1.3: device descriptor read/8, error -110 
Oct 16 12:55:08 tim-oneiric kernel: [   68.177562] 
MediaState is connected
```

Tim

---

### Post by ratcheer on 2011-10-16
If it works, I have found an answer on Launchpad, Question #173612 dated 7-Oct-2011.

Add kernel option irqpoll to boot menu.

Tim

---

### Post by ratcheer on 2011-10-16
Well, hell. There now seems to be a bug with the kernel no longer recognizing the irqpoll option. So, that workaround cannot work for me.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855199](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855199)

Tim

---

### Post by ratcheer on 2011-10-16
I feel stupid, but I also feel better. I turned off the PC, disconnected the power from the USB drive for about 15 seconds, reconnected the power, rebooted, removed the irqpoll kernel option, and Ubuntu started, perfectly. I need to learn that the USB drive just goes freaky sometimes and remember to do this. But, this is only the second time I've had to do this in months of use.

Tim

---

