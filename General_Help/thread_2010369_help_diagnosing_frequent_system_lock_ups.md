---
title: "help diagnosing frequent system lock ups"
date: 2012-06-25
forum: General Help
---

### Post by zorkerz on 2012-06-25
Hi all, 
My laptop (thinkpad x61) running Ubuntu 12.04 has been locking up pretty frequently. When it freezes the mouse and keyboard are unresponsive. All I have been able do is force a shutdown by holding down the power button. Occasionally the computer restarts itself before I manually shut it down. I have found no way to reliably reproduce these freezes. I believe I originally started experiencing freezes while using 11.10 (though possibly I started noticing them a bit later while using 12.04 alpha/betas). 

How does one go about figuring out what is causing system lock ups?

---

### Post by zorkerz on 2012-06-25
I started looking through the syslog. I noticed that often though not  always these four lines appear immediately before the lock up. 
```
kernel: [ 2095.762378] pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)
kernel: [ 2095.766526] pciehp 0000:00:1c.0:pcie04: Card present on Slot(2)
kernel: [ 2096.874175] pciehp 0000:00:1c.0:pcie04: No new device found
 kernel: [ 2096.874190] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00
``` I've attached the entire syslog in case its useful.

I also noticed this line showed up occasionally but usually not right before a lock up.
```
kernel: [  299.816089] [Hardware Error]: Machine check events logged
```This lead me to look into mcelog. It installed fine but when I try to run it I get the following response.
```
mcelog: warning: 16 bytes ignored in each record
mcelog: consider an update
```Here is my /var/log/mcelog
```
mcelog: failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
mcelog: failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
```Over on [this thread ]("http://ubuntuforums.org/showthread.php?p=12053213#post12053213")jmfal has been very helpful. He had me add pciehp to the /etc/modprobe.d/blacklist.conf blacklist.  This may have worked (its been over an hour since the last lockup).

Not sure if you can tell but I only kinda understand this stuff. I would really love some pointers on what to look for to determine what is causing a system lock up.

thanks

---

### Post by jmfal on 2012-06-25
I googled  processor context corrupt and found this:

[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

It might be as simple as you cpu fan is going bad, causing overheating or..........

---

### Post by zorkerz on 2012-06-25
Thanks again,
Overheating was my first suspicion. Months ago but after the freezing first started I replaced the main (and I believe only) fan on the computer because it was getting extremely loud and briefly stopping all together. Since then I have been monitoring the temperature using indicator sensors. It gives ten different temperatures. I don't know which one (or likely two) apply to each core's temp but I watch the one that typically reports the highest temp. The temperature always seems to be within acceptable ranges for a core 2 duo T7500.

I've also run memtest which reported no errors. 

I plan to do a hardrive test when I can spare the computer for a bit. 

The Machine Check Exception really worries me. It seems to point pretty strongly to some hardware problem. The only saving grace is that my lock ups happen much more often then the MCE is reported and rarely at the same time. Also since commenting out shphp, no lock ups yet, knock on wood.

---

### Post by zorkerz on 2012-06-25
Just had another lock up. Made it around four hours this time!

But I have no indication of what might have caused it. Here is the syslog immediately before the lock up. I don't see any entry here that could be related. The lock up happened at 19:16 and imklog always seems to be the first entry on system startup.

```
Jun 25 16:20:03 anoak sudo: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 25 17:17:01 anoak CRON[3618]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 25 17:25:30 anoak gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 25 17:56:51 anoak gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 25 18:10:48 anoak dbus[789]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jun 25 18:10:48 anoak AptDaemon: INFO: Initializing daemon
Jun 25 18:10:48 anoak dbus[789]: [system] Successfully activated service 'org.debian.apt'
Jun 25 18:10:48 anoak AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 25 18:15:48 anoak AptDaemon: INFO: Quitting due to inactivity
Jun 25 18:15:48 anoak AptDaemon: INFO: Quitting was requested
Jun 25 18:17:01 anoak CRON[3930]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 25 18:25:00 anoak gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 25 19:08:02 anoak pulseaudio[1834]: [alsa-sink] ratelimit.c: 109 events suppressed
Jun 25 19:08:02 anoak pulseaudio[1834]: [alsa-sink] protocol-native.c: Failed to push data into queue
Jun 25 19:09:03  pulseaudio[1834]: last message repeated 3 times
Jun 25 19:16:21 anoak kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

Where else can I look to figure out what is going wrong?

---

### Post by jmfal on 2012-06-25
I'm assuming you have a dual core processor that is 0 is core1&core 1 is the 2nd core

if you  installed lm sensors  you can try

```
 sensors   
```
and match up the temps so you can tell which one is which

try the Xorg.O log

Is the video onboard?

---

### Post by zorkerz on 2012-06-25
Yes this is a Thinkpad x61 with an intel core 2 duo T7500 @ 2.2GHz and an onboard intel GM965 chipset for graphics.

I've been using[ indicator-sensors]("https://launchpad.net/indicator-sensors") it seems to have the same information as lm-sensors.  Both give two temperatures under libsensors/acpitz-virtual-0/0 and eight under thinkpad-isa-0000. Two from each section all have the hottest temperatures and never vary from each other by many degrees. I have assumed these are the two cores. I have not looked into a way to verify that.

Not sure what to look for in Xorg.O.log

---

### Post by zorkerz on 2012-06-27
So for no good reasons I reinstalled ubuntu 12.04. Since then I have gotten a number of freezes but my /var/log/mcelog has remained empty. I have also not seen any Machine Check Errors in the logs. 

I was in class today without Internet access so I disabled my wifi. I made it 6 hours without a freeze. Could it be the wifi card? Is there any way to test that?

I'm totally shooting in the dark at this point. I have no idea how to find out what is causing the freezes. Insights always appreciated.

---

### Post by jmfal on 2012-06-27
Hi 

It could be the wifi card 
Check this out and find the chipset info, write it down or copy it to a word document
get  your wifi working and the next time it freezes up we can look at the logs;;;;;;

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported/](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported/)

Also you should look around and see how hard it is to replace it or if it is worth the trouble.

---

### Post by zorkerz on 2012-06-27
Here is the output of lspci -v
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fdf00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-13-e8-ff-ff-7a-5e-3d
    Kernel driver in use: iwl4965
    Kernel modules: iwl4965

```

I've taken this computer entirely apaprt in order to replace the cpu heatsink and fan. Thats one of the beauties of thinkpads they give videos telling you how to take the whole thing apart and put it back together again. Not that thats really necessary but it sure provides some peace of mind. Anyway I remember removing the wifi card during the process so it should be no problem if need be.

Waiting for a freeze now. What should I look for in the logs when it happens? Any particular log?

---

### Post by jmfal on 2012-06-27
SYS LOG should be good,  I'm sure there is some kind of network log, I think you have to look at it in a terminal.

Anyway try to post a couple of minutes before, I'm not sure how it will be listed may use the kernal module number or capabilities [100]

---

### Post by jonnyboysmithy on 2012-06-27
Can you tell us what happens when it freezes? 
You could try giving it a torture test, just to see if overheating is not the problem.

I would remove all that hardware that I could (external mouse, wifi card, memory stick etc..). I had a laptop (dell d610) that had a faulty graphics card that would also lock up from time to time.. Video drivers? I had some grief with those in the past turned out it I was using an unstable driver.. You have an intel card so should be all good driver wise as far as I can tell.. 
Perhaps theres some piece of junk rattling around on your motherboard thats causing shorts? I suppose you already cleaned all that while when you did the fan.

Then again its probably pci related like you said earlier..
Can you tell us what happens when it freezes? 

I would remove all  that hardware that I could (mouse, wifi card, memory stick etc..). I  had a laptop (dell d610) that had a faulty graphics card that would also  lock up from time to time.. Video drivers? I had some grief with those  in the past turned out it I was using an unstable driver.. You have an  intel card so should be all good driver wise as far as I can tell.. 
Perhaps  theres some piece of junk rattling around on your motherboard thats  causing shorts? I suppose you already cleaned all that while when you  did the fan.

Then again its probably pci related like you said earlier..

---

### Post by zorkerz on 2012-06-27
When it freezes it responds in no way except to me holding down the power button.  The screen is frozen the mouse does not move. Usually (possibly always) the wifi light is flashing, its pretty much always flashing anyways. Other lights are off except battery, power and some other light thats always on, maybe means powered on, i dunno.

For the most part I don't have anything plugged into it except the power cord. Occasionally some usb headphones or a usb drive but they don't seem to correlate to when the crashes happen. 

Oddly enough I've been going crash free for a good hour or so. I don't know if its just me but it seems that once it crashes once its much more likely to do it again soon.

I could have just as easily caused a problem taking the thing apart as fixed one but the freezes were happening prior to the fan replacement.

---

### Post by zorkerz on 2012-06-28
Another 6 hour day without wifi and no freezes.

Finally got one but oddly it happened right after pciehp again even though I have added it to /etc/modprobe.d/blacklist.conf

Here is the /log/var/syslog
```
Jun 28 17:56:48 anoak NetworkManager[1011]: <info> (wlan0): supplicant interface state: associating -> completed
Jun 28 17:57:14 anoak anacron[6692]: Anacron 2.3 started on 2012-06-28
Jun 28 17:57:14 anoak anacron[6692]: Normal exit (0 jobs run)
Jun 28 17:57:14 anoak kernel: [ 4267.744059] e1000e 0000:00:19.0: BAR 0: set to [mem 0xfe000000-0xfe01ffff] (PCI address [0xfe000000-0xfe01ffff])
Jun 28 17:57:14 anoak kernel: [ 4267.744067] e1000e 0000:00:19.0: BAR 1: set to [mem 0xfe225000-0xfe225fff] (PCI address [0xfe225000-0xfe225fff])
Jun 28 17:57:14 anoak kernel: [ 4267.744073] e1000e 0000:00:19.0: BAR 2: set to [io  0x1840-0x185f] (PCI address [0x1840-0x185f])
Jun 28 17:57:14 anoak kernel: [ 4267.744092] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 28 17:57:14 anoak kernel: [ 4267.744119] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
Jun 28 17:57:14 anoak kernel: [ 4267.744154] e1000e 0000:00:19.0: PME# disabled
Jun 28 17:57:14 anoak kernel: [ 4267.744243] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
Jun 28 18:03:38 anoak gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 28 18:17:01 anoak CRON[6864]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 18:34:45 anoak gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/e is already mounted
Jun 28 19:17:01 anoak CRON[7027]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 19:58:19 anoak kernel: [11532.675241] pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)
Jun 28 19:58:19 anoak kernel: [11532.679470] pciehp 0000:00:1c.0:pcie04: Card present on Slot(2)
Jun 28 19:58:20 anoak kernel: [11533.780139] pciehp 0000:00:1c.0:pcie04: No new device found
Jun 28 19:58:20 anoak kernel: [11533.780152] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00
Jun 28 20:00:08 anoak kernel: [11641.699045] pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)
Jun 28 20:00:08 anoak kernel: [11641.703770] pciehp 0000:00:1c.0:pcie04: Card present on Slot(2)
Jun 28 20:00:09 anoak kernel: [11642.806459] pciehp 0000:00:1c.0:pcie04: No new device found
Jun 28 20:00:09 anoak kernel: [11642.806473] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00
Jun 28 20:04:12 anoak kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

Heres auth.log
```
Jun 28 17:17:01 anoak CRON[3656]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 17:17:01 anoak CRON[3656]: pam_unix(cron:session): session closed for user root
Jun 28 18:03:38 anoak gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Jun 28 18:17:01 anoak CRON[6863]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 18:17:01 anoak CRON[6863]: pam_unix(cron:session): session closed for user root
Jun 28 18:34:45 anoak gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Jun 28 19:17:01 anoak CRON[7026]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 28 19:17:01 anoak CRON[7026]: pam_unix(cron:session): session closed for user root
Jun 28 20:04:13 anoak lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
```

Nothing looks interesting to me except pciehp being back. I don't really know anything about pciehp should it be disabled because it was added to the blacklist?

Geeze I wish I know how else to look into this. Thanks for all the help.

---

### Post by jmfal on 2012-06-28
I see your still having problems.

Blacklisting keeps pcihp from loading when the  os boots, at least that is what I understand.
Is your ethernet plug built in to the wifi if not try going hardwired and disable the wifi and see if  that cures it 

I'm not a network expert so I'm running out of options.

Are you using a generic video driver or proprietary

---

### Post by zorkerz on 2012-06-28
The wifi has been disabled for two 6+ hour stints with no freeze. I have not made it that long without a freeze otherwise.  Though during these stints I was generally not connected to the internet at all. Unfortunately its not going to be easy for me to hardwire this computer at my house and use it (i'll try to give it a shot when I can). 

All drivers for this computer are generic defaults installed by ubuntu.

---

### Post by steeldriver on 2012-06-28
I can't help here but fwiw I had very similar behavior on a T60p (200783U) - frequent *complete* lockups under Windows XP (not even caps lock light responding - if I happened to be streaming audio it would go into a loop). I was dual booting with Debian/KDE at the time and that was better but would still occasionally freeze and/or pop up bus error notifications (I don't remember the exact message - something like "uh-oh! something weird happened - attempting to continue"). I'd already torture tested it under XP and even swapped out both RAM sticks.

I have been hesitant to post a me-to since I don't know if the T60p shares any significant subsystems with yours but it really is sounding eerily familiar (especially the dependence on WiFi)

Like you I found it was stable with WiFi disabled - I even went as far as swapping the original Intel card for an Atheros one (or vice versa - I don't remember) so that both hardware AND drivers were different - same error. I eventually gave up and assumed it was a physical hardware problem somewhere in the PCI bus that only manifested with WiFi enabled - since then I either run it wired or with a CardBus or USB dongle and it's been 100% solid.

---

### Post by matt_symes on 2012-06-29
Hi

Try disabling  acpi as a kernel parameter from GRUB. 

It is a real big hammer but it should eliminate a firmware bug in ACPI if it still freezes. If it doesn't freeze then that's a place to start looking into.

```
acpi=off
```

Kind regards

---

### Post by zorkerz on 2012-07-05
Well it does not appear to be the wifi I just had two lockups while using ethernet with wifi disabled. I did (and frequently do) have a usb headset plugged in but many lockups have happened without this in.
[FONT=monospace]
[/FONT]The vast majority of the lockups have 'pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)' in the syslog immediately or nearly immediately before the startup sequence shows up.

I need to find out more about pciehp anyone know a good resource? I'd like to figure how many pcie ports I have and what uses them. Could it be as simple as a loos connection on one of the ports?

@matt_symes: I have not gone the acpi=off route yet but likely will pretty soon.
[FONT=monospace]

[/FONT]

---

### Post by jmfal on 2012-07-05
HI Zorkerz

Googled pciehp and couldn't find anything real useful.

I'm just wondering if having overheating problems in the past has taken its toll on the mobo.

---

### Post by jmfal on 2012-07-05
I forgot to ask if these freeze ups are happening when you open laptop lid or coming out of suspend or resume.

---

### Post by zorkerz on 2012-07-05
My quick searches around pciehp have not turned up anything useful yet either.

I'm sure overheating can cause some perminent damage to hardware components but I don't think I ever had a serious overheating problem. I replaced that fan mostly because it of the jet engine sound, a tell tale sign of ageing fan disease. Its always possible though.

No the freezes are not related to suspend, resume or closing/opening the lid. Though I do have an unrelated problem with that. Resuming from supend often gives me a blank screen except for the moveable mouse. With this I can restart the screen by press ctrl + alt + F1-6 and forcing a reboot (sudo reboot). This one has been filed as a bug report that I am following.

---

### Post by zorkerz on 2012-07-05
Hmm so I was just looking at the thinkpad x61s over at [thinkwiki]("http://www.thinkwiki.org/wiki/Category:X61") (great site if you have at thinkpad).  I think its saying that  I have three PCI-Express slots. 
 
[LIST]
[*]PCI-Express: Intel Gigabit Ethernet (10/100/1000)
[*]MiniPCI Express slot: Intel PRO/Wireless 4965AGN
[*]MiniPCI Express slot 2: Intel® Turbo Memory hard drive cache
[/LIST]
Below is the output of lspci -v. Here is what I have noticed. PCI comes up three times as well as each of the pieces of hardware above. Maybe this is because one is the port and one is the card?

 
The syslog usually says "Card not present on Slot(2)" before a lockup. One PCI entry is port 2 and the turbo memory entry is slot 2. Could it be that there is some problem with turbo memory or the slot it is plugged into? To my knowledge turbo memory does not even work with linux anyway (am I wrong?).


So without further input my next plan of action is to try and disable the PCI slot 2 and/or remove the turbo memory chip. More drastically I will look into disabling all PCI slots. 



What do you all think? Does that make sense? Any ideas if/how to disable PCI-Express slots?


```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
    Subsystem: Lenovo T61
    Flags: bus master, fast devsel, latency 0
    Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
    Subsystem: Lenovo Device 20de
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe000000 (32-bit, non-prefetchable) [size=128K]
    Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T60
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dc100000-dfcfffff
    Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: fc000000-fdffffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 18c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=08, sec-latency=32
    I/O behind bridge: 00004000-00007fff
    Memory behind bridge: f8300000-fbffffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
    Subsystem: Lenovo T61
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18e0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 1c30 [size=8]
    I/O ports at 1c24 [size=4]
    I/O ports at 1c28 [size=8]
    I/O ports at 1c20 [size=4]
    I/O ports at 1c00 [size=32]
    Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: medium devsel, IRQ 11
    Memory at fe227400 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c40 [size=32]
    Kernel modules: i2c-i801

02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
    Subsystem: Intel Corporation Turbo Memory Controller
    Physical Slot: 2
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfcffc00 (32-bit, non-prefetchable) [size=1K]
    I/O ports at 2000 [size=128]
    [virtual] Expansion ROM at dfe00000 [disabled] [size=64K]
    Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fdf00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwl4965
    Kernel modules: iwl4965

05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Lenovo Device 20c6
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=07, sec-latency=176
    Memory window 0: f4000000-f7fff000 (prefetchable)
    Memory window 1: c0000000-c3fff000
    I/O window 0: 00004400-000044ff
    I/O window 1: 00004000-000040ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 20c7
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
    Subsystem: Lenovo Device 20c8
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f8301800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```

---

### Post by zorkerz on 2012-07-05
Below is the output of 'sudo lshw'.  I don't really know how to read these command outputs but I can guess. 

Here is the part that stood out to me. 
```
*-pci:0
              description: PCI bridge
              product: 82801H (ICH8 Family) PCI Express Port 1
              vendor: Intel Corporation
              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:40 ioport:2000(size=4096) memory:dc100000-dfcfffff ioport:dfe00000(size=1048576)
            *-memory UNCLAIMED
                 description: Memory controller
                 product: Turbo Memory Controller
                 vendor: Intel Corporation
                 physical id: 0
                 bus info: pci@0000:02:00.0
                 version: 01
                 width: 32 bits
                 clock: 33MHz (30.3ns)
                 capabilities: pm msi pciexpress bus_master cap_list
                 configuration: latency=0
                 resources: memory:dfcffc00-dfcfffff ioport:2000(size=128) memory:dfe00000-dfe0ffff
```

Again the syslog repeatedly shows 'pciehp 0000:00:1c.0:pcie04: Card not present on Slot(2)' before a lockup. Notice that pci:0's bus info is pci@0000:00:1c.0. To me this indicates the pci slot not the turbo memory which shows up in the terminal indented just below it.

So I still think the plan of action is to disable that pci slot or maybe just remove the turbo memory card. 

Am I on to something?

```
 description: Notebook
    product: 7675CTO ()
    vendor: LENOVO
    version: ThinkPad X61
    serial: LVB3419
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=notebook family=ThinkPad X61 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=B4C153E0-7700-11DC-9C03-FEAE51CF6B65
  *-core
       description: Motherboard
       product: 7675CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZDXM79M1HA
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7NETC2WW (2.22 )
          date: 03/22/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          slot: None
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f8100000-f81fffff memory:e0000000-efffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8200000-f82fffff
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:16:d3:cc:55:ba
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:43 memory:fe000000-fe01ffff memory:fe225000-fe225fff ioport:1840(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fe226c00-fe226fff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:fe220000-fe223fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:dc100000-dfcfffff ioport:dfe00000(size=1048576)
           *-memory UNCLAIMED
                description: Memory controller
                product: Turbo Memory Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:dfcffc00-dfcfffff ioport:2000(size=128) memory:dfe00000-dfe0ffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:fc000000-fdffffff ioport:f8000000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 61
                serial: 00:13:e8:7a:5e:3d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-26-generic firmware=228.61.2.24 ip=192.168.1.15 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:45 memory:fdf00000-fdf01fff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fe227000-fe2273ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:4000(size=16384) memory:f8300000-fbffffff ioport:f4000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:05:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00706050-b0070604f irq:16 memory:f8300000-f8300fff ioport:4400(size=256) ioport:4000(size=256) memory:f4000000-f7ffffff memory:c0000000-c3ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f8301000-f83017ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f8301800-f83018ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18e0(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:1c30(size=8) ioport:1c24(size=4) ioport:1c28(size=8) ioport:1c20(size=4) ioport:1c00(size=32) memory:fe226000-fe2267ff
           *-disk
                description: ATA Disk
                product: HTS721010G9SA00
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MCZI
                serial: MPDZN7Y0J655YL
                size: 93GiB (100GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c65649ba
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 6500bea0-b156-4448-a482-703af48464d6
                   size: 8GiB
                   capacity: 8GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-26 21:28:07 filesystem=ext4 lastmountpoint=/ modified=2012-06-26 22:07:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-07-05 15:38:15 state=mounted
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 8GiB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 5GiB
                   capabilities: primary nofs
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: d7907667-4078-4838-9c79-f7d0ea7b23f1
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-06-26 21:31:31 filesystem=ext4 lastmountpoint=/home modified=2012-07-05 15:38:18 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-07-05 15:38:18 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe227400-fe2274ff ioport:1c40(size=32)
  *-battery
       product: COMPATIBLE
       vendor: GW
       physical id: 1
       slot: Rear
       capacity: 37440mWh
       configuration: voltage=14.4V

```

---

### Post by jmfal on 2012-07-05
I'm not sure if you can disable it, and if you can it would be in bios.

That may be a slot ID but there might not be a physical slot on mobo.

---

### Post by zorkerz on 2012-07-05
Ok so I think the turbo memory module is shpchp. If I disabled this by adding it to /etc/*modprobe*.*d*/blacklist might that do the trick?

In the PCI section of the BIOS there are INT A-H and the IRQs are all set to 11 they can be disabled, automatic or 3,4,5,6,7,9,10. I've been reading up on the PCI INTs and IRQs and from my understanding none of those directly correlate to a specific PCI slot.

No more time to look into this tonight but this is the first time I've felt like we might have pinned down a solution.

Easiest thing might be to just remove the Turbo Memory Card.

---

### Post by jmfal on 2012-07-05
you can do that, isee thereis a WWAN card that is next to the wifi , it has a fan but does not turn on till you use the wwan. could be part of the running hot problem

If you play with the IRQ  you should look at   lspci -v  it has IRQ for each and none shoould be the same.

plug and play is supposed to take care of IRQ problems

---

### Post by zorkerz on 2012-07-06
From lspci -v above there are two entries with IRQ 11

```
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: medium devsel, IRQ 11
    Memory at fe227400 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c40 [size=32]
    Kernel modules: i2c-i801

02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
    Subsystem: Intel Corporation Turbo Memory Controller
    Physical Slot: 2
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfcffc00 (32-bit, non-prefetchable) [size=1K]
    I/O ports at 2000 [size=128]
    [virtual] Expansion ROM at dfe00000 [disabled] [size=64K]
    Capabilities: <access denied>
```

In the BIOS there is INT A through H (eight in total) all of which are set to IRQ 11.  Does the A-H stand for different PCI ports or pieces of hardware or something else? Is there a way to know which is which (A-H is not very helpful). 

Or do I not understand this fully?

---

### Post by jmfal on 2012-07-06
I'm not sure myself,

[http://www.ehow.com/facts_5977415_smbus-controller_.html](http://www.ehow.com/facts_5977415_smbus-controller_.html)

This may help to

[http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-68244](http://support.lenovo.com/en_US/detail.page?LegacyDocID=MIGR-68244)

---

### Post by Cork87 on 2012-10-17
Hi I have the same issues on a workstation so probably this has nothing to do with you wifi controller. 

When I have a freeze I can manage to open up a console by pressing ctrl+alt+F1 and login. After you gained root privileges you can restart ligthdm and your graphical environment will restart. You will lose everything but at least you do not have to reboot. 

I will give you an update once I have further information.

---

### Post by zorkerz on 2012-10-17
Cork 87 your issue sounds a bit different to me. My computer is completely locking up, I am not able to reach an alternate console, the only solution I have found is to hold the power button down or directly cut power. I have an issue with similar symptoms to you sometimes when I come back from suspend, I know there's a large thread about that somewhere.

For others paying attention. I'm still experiencing the same problem, I went away for nearly a month about when I stopped posting here, then returned. I plan to install Ubuntu 12.10 in the near future and see if the lockups continue to occur. If so I think I will take out my turbo memory card, which is completely unused in linux to my knowledge and has been indicated as potentially related to the lockups. Beyond that om long out of ideas, it will be new laptop time for me if I can ever save the money.

---

### Post by zorkerz on 2012-10-30
An update for my memory. I removed the intel turbo memory card today. This uses the pci port that is my last best hope for the cause of these lockups. With luck the lockups will go away. If not I'll keep limping along until I can afford a new laptop.

---

