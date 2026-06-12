---
title: "Hibernation problems"
date: 2010-09-23
forum: General Help
---

### Post by Crazedpsyc on 2010-09-23
Ok I have 3 probs with hibernation right now. I am running Lucid with all updates and here's some hardware specs:
```

15:31:01> lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               2266.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K

15:31:42> lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

If you cant get this out of that, I running on quad intel i3 (2.27GHz each) with 8 gigs of ram and a 8 gig swap partition.

1. when i am running on battery power and use the pretty little power menu in the gnome-panel and select hibernate it just locks the screen (and yes i waited and the HD light blinked a lot, but then the unlock dialog came back.

2. When I am on AC power and use the same hibernate function it goes black and the HD light is on steadily for a while (probably writing to swap) and (a) then I have to hold down the power button to actually turn it off. when I turn it back on it goes to a frozen unlock dialog for a while before I can finally unlock it and then (b) it quickly gets up to 160 degrees Fahrenheit with half my total CPU power being used constantly (normal temp for me is about 120F).

3. When I use the hibernate program from synaptic (sudo hibernate --lock-console-as #) it goes to that program's unlockscreen until I unlock it. It should say something about writing to swap... _% complete and then shut down.

---

### Post by Kixtosh on 2010-09-23
Try and see if any of the solutions in this thread help. The link is to the last post (at the time of writing), which details how I fixed suspend (not hibernate) problems on one of my laptops, but there are references to hibernation issues also.

Note the reference in my post to an error in the first post of the thread (well, a correction that was never made).

[http://ubuntuforums.org/showpost.php?p=9837211&postcount=204](http://ubuntuforums.org/showpost.php?p=9837211&postcount=204)

---

### Post by zangderak on 2010-09-23
I think I'm having the same problem as you.  I also tried installing uswsusp then entering the command:

```
sudo s2disk
```
It goes to the blank screen, writes to swap then shuts off.  But when I turn on my machine again, it's as if Ubuntu just reboots.

Kixtosh, the thread you posted is really long, and I'm having trouble finding anything that would help this specific problem.  I'd appreciate it very much if someone could help us out.

---

### Post by Crazedpsyc on 2010-09-24
Oh yeah, that's another problem! How do I wake up after putting it to sleep? A lot of stuff says to push the suspend button, but I don't have one. My ASUS power4gear changing key combo (Fn+SPACE) does put it to sleep, but it won't wake it up. How do I wake up!!??

---

### Post by Kixtosh on 2010-09-24
> **zangderak said:**
> ... It goes to the blank screen, writes to swap then shuts off.  But when I turn on my machine again, it's as if Ubuntu just reboots. ...Coming out of hibernation always seems like rebooting on my laptops:

- You see the BIOS splash screen,
- You see the GRUB menu if you are dual booting with Windows,
- There is a similar wait time before the desktop finally appears.

But:

- It **is** faster (by 15 seconds or so in my case),
- It **does** remember exactly every application/document that was open before entering hibernation.

So, if it seems "as if Ubuntu just reboots", **that's not a problem, as long as you are actually returning to the same active state** (documents open, brower windows and tabs opened).

There is actually a third "hybrid" option, which attempts to hibernate in a suspend state instead, but still writes the information to the HDD in case the battery runs out from the suspend state. I haven't played with this yet, but it seems like the best of all worlds.

> Kixtosh, the thread you posted is really long, and I'm having trouble finding anything that would help this specific problem.  I'd appreciate it very much if someone could help us out.LOL! I know, I read the whole thing, which is how I found the very useful information on page nineteen. Seriously, though, twenty-one pages or some two hundred posts is a lot shorter than some troubleshooting threads! I'll try and review the most important points without reading the whole thing again myself, but basically, to get you started, after installing uswsusp:```
sudo apt-get install uswsusp
```
Try:```
sudo s2ram
```In my case, I got```
Machine is unknown.
This machine can be identified by:
   sys_vendor   = "TOSHIBA"
   sys_product  = "Portable PC"
   sys_version  = "Version 1.0"
   bios_version = "Version 1.80"
See http://suspend.sf.net/s2ram-support.html for details.
If you report a problem, please include the complete output above.
```The link was old, but redirects to a new link where you will find all these variations to try, one after the other:

[http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F](http://en.opensuse.org/SDB:Suspend_to_RAM#My_machine_is_not_in_the_whitelist.2C_what_can_I_do.3F)

This first one did not work for me:```
s2ram -f
```But, I only had to try two other variations before I discovered that this would give me full suspend and hibernate capability:```
s2ram -f -a 2
```Then, once tested to suspend and hibernate correctly, the change must be made permanent:```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/hal-system-power-suspend-linux
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
```This assumes that you have the gedit text editor installed on your system. If not, you'll get an error message, so you'll have to add it. This opens up a window with a pile of gibberish, which you replace with nothing but the two lines of your working variation like so (where -f -a2  was my working variation):```
#!/bin/sh

/usr/sbin/s2ram -f -a2
```You'll have to make the same changes for whatever works with hibernation. I didn't have to do this last step, since my problem was only with standby. On a side note: this also fixed my screensaver issues. I hadn't been using screensaver on my oldest laptop since it always caused it to freeze up. 

> **Crazedpsyc said:**
> Oh yeah, that's another problem! How do I wake up after putting it to sleep? A lot of stuff says to push the suspend button, but I don't have one. My ASUS power4gear changing key combo (Fn+SPACE) does put it to sleep, but it won't wake it up. How do I wake up!!??That's perfectly normal. You push the power button to wake up from suspend or hibernation. In some cases, just opening the lid will wake the laptop from either state (it does on both of my Toshibas).

---

### Post by zangderak on 2010-09-24
> **Kixtosh said:**
> 
- It **does** remember exactly every application/document that was open before entering hibernation.

By "as if Ubuntu just reboots" I really meant to say that it **doesn't** remember exactly every application/document that was open before hibernating.  Sorry if I wasn't clear.

I'll try this out again I install Ubuntu Studio (just found out about this 'real time kernel' thing, which sounds relevant to my audio recording needs).  Thanks alot for your reply!  I'll be back with an update soon.

---

### Post by Crazedpsyc on 2010-09-25
Actually, it does remember everything for me, but it isn't useful because when the HD(D) is full of cache everything is too slow, and it overheats.

---

