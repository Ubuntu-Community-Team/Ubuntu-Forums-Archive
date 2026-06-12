---
title: "Brightness keys have no effect (no output in xev) on Clevo"
date: 2012-08-23
forum: General Help
---

### Post by YannBuntu on 2012-08-23
Dear all

My brightness keys have no effect on my Clevo laptop. 12.04.

- my brightness keys have no output in "xev" , nor in "sudo showkey -k"
- "xmodmap -pke" shows:
```
keycode 237 = XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown
keycode 238 = XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp
```
- no change with the "acpi_osi=Linux acpi_backlight=vendor" option
- no change with [kernel 3.4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/")

Until here, my situation have common points with this one: [http://ubuntuforums.org/showthread.php?t=2039350](http://ubuntuforums.org/showthread.php?t=2039350)

But the difference is that the "sudo setpci -s 00:02.0 F4.B=xx" workaround doesn't work for me. :sad: (00:02.0 is ok, and i tried xx=20 , 40, 60, 80)

Any idea please?

---

### Post by Toz on 2012-08-23
Can you post the results of:
```
lspci | grep VGA
```

And while you're at it, can you also provide the results of the following:
```
sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name
```

A look at your dmesg log file might help as well:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

And finally, your backlight interfaces:
```
for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
```

In the meantime, give the "**acpi_osi=**" kernel parameter a try. Thats "acpi_osi=" without an accompanying string value.

EDIT: you might also want to give acpi_osi="Windows 2006" a try. It will be tricky to get the escaping correct on the grub line. If editing /etc/default/grub, it would look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Window 2006\""
```

---

### Post by YannBuntu on 2012-08-24
Hello Toz, thanks for your interest

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

```
sudo dmidecode -s system-manufacturer
CLEVO CO.                   
```

```
sudo dmidecode -s system-product-name
W240HU/W250HUQ
```

```
pastebinit /var/log/dmesg
http://paste.ubuntu.com/1163952
```

```
for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
/sys/class/backlight/acpi_video0
7
7
7
/sys/class/backlight/intel_backlight
4882
4882
4882
```

I will try the kernel option.

---

### Post by YannBuntu on 2012-08-24
the correct syntax is:
```
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash acpi_osi="Window 2006"'
```
..but it doesn't work for me.

However, the **acpi_osi=** option seems to be a correct workaround (**the keys increase/decrease brightness, but still no output in showkey nor xev**, and still no effect with "setpci -s 00:02.0 F4.B=XX").
Thanks for suggesting it !

---

### Post by YannBuntu on 2012-08-24
however, when using acpi_osi=, I can't adjust brightness via the System settings->Brightness and lock menu any more. (the slide bar has no effect any more)

[IMG]http://pix.toile-libre.org/upload/original/1345796819.png[/IMG]

---

### Post by YannBuntu on 2012-08-24
Not sure if this can help:
- With and without acpi_osi=, "ls /sys/class/backlight" returns:
```
acpi_video0  intel_backlight
```

- But with acpi_backlight=vendor, it returns only:
```
intel_backlight
```
- with acpi_backlight=vendor, nothing works, neither the hotkeys nor the System Settings way.

I will create a bug report.

---

### Post by YannBuntu on 2012-08-24
Bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041116)

---

### Post by Toz on 2012-08-24
> **YannBuntu said:**
> Not sure if this can help:
- With and without acpi_osi=, "ls /sys/class/backlight" returns:
```
acpi_video0  intel_backlight
```

- But with acpi_backlight=vendor, it returns only:
```
intel_backlight
```
- with acpi_backlight=vendor, nothing works, neither the hotkeys nor the System Settings way.

I will create a bug report.

Can you try with **acpi_backlight=legacy** and **acpi_backlight=video**

---

### Post by YannBuntu on 2012-08-24
tested each one separately. No effect.

---

### Post by Toz on 2012-08-24
Which of the backlight interfaces are active? You can test by echoing a value to the brightness file. e.g.:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...I chose the values as half of what was reported back in post #3.

What modules are loaded?
```
lsmod
```

And what kernel parameter(s) are we working with:
```
cat /proc/cmdline
```

---

### Post by YannBuntu on 2012-08-27
```
$ echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
4
```

Works from 1 to 7.  
"8" returns :

```
$ echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness
8
tee: /sys/class/backlight/acpi_video0/brightness: Invalid argument
```


```
$ echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
2441
$ echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
2000
$ echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
1000
$ echo 100 | sudo tee /sys/class/backlight/intel_backlight/brightness
100
```

don't have any effect.

---

### Post by YannBuntu on 2012-08-27
```
$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rtl8192ce              84826  0 
wmi                    19256  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  2 rtlwifi,mac80211
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17646  0 
mac_hid                13253  0 
psmouse                87692  0 
serio_raw              13211  0 
memstick               16569  1 jmb38x_ms
i915                  472941  3 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
jme                    41259  0 

```

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=789016b1-f3f0-4b76-be92-afa2dbb36c5e ro quiet splash vt.handoff=7
```

---

### Post by Toz on 2012-08-27
It looks like acpi_osi= is your best bet (except it breaks brightness and lock). It looks like the acpi_video0 is the active interface, but brightness and lock is using the intel_backlight interface.

If there were some way to remove the intel_backlight interface, it would probably work. 

Can you try "acpi_osi= acpi_backlight=legacy" and "acpi_osi= acpi_backlight=video" to see if it removes the intel_backlight interface?

I came across this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661"). The problem is for a Dell, but later comment states it also worked for a Panasonic. The important thing is that it appears to be the same problem as this one. 

Perhaps a test of the kernel (with the kernel boot parameter "i915.enable_backlight=0" (try with and with "acpi_osi=")?

---

### Post by YannBuntu on 2012-08-27
I forgot to mention that post#11-12 results were obtained when my system had no specific kernel option (in particular no acpi_osi=).
Will answer the rest soon.

---

### Post by YannBuntu on 2012-08-27
> **Toz said:**
> Can you try "acpi_osi= acpi_backlight=legacy" and "acpi_osi= acpi_backlight=video" to see if it removes the intel_backlight interface?

how do I check if it removes the intel_backlight interface?

---

### Post by Toz on 2012-08-27
> **YannBuntu said:**
> how do I check if it removes the intel_backlight interface?

Have a look and see if the intel_backlight directory exists in /sys/class/backlight. If its not there, then the interface is not available (which is what we want).

---

### Post by YannBuntu on 2012-08-28
- when using "acpi_osi= acpi_backlight=legacy" , or "acpi_osi= acpi_backlight=video", the intel_backlight directory still exists in /sys/class/backlight. 

- "i915.enable_backlight=0" (with and without "acpi_osi=") makes no improvement, and removes the brightness cursor in the window below:

[IMG]http://pix.toile-libre.org/upload/original/1346141604.png[/IMG]

---

### Post by Toz on 2012-08-28
> - "i915.enable_backlight=0" (with and without "acpi_osi=") makes no improvement, and removes the brightness cursor in the window below:

- Did you install the kernel from the referenced PPA (the sputnik kernel from [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel]("https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel")) or are your running this on the base kernel? 
- Does the intel_backlight interface exist when using this kernel parameter?
- Can you post back your /var/log/dmesg file when you use "i915.enable_backlight=0"?

---

### Post by YannBuntu on 2012-08-28
> **Toz said:**
> - Did you install the kernel from the referenced PPA (the sputnik kernel from [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel]("https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel")) or are your running this on the base kernel? 


That was with the base kernel (3.2.0-29).
With "i915.enable_backlight=0" and without "acpi_osi=", /sys/class/backlight folder exists but is empty, and Dmsg is [http://paste.ubuntu.com/1171888](http://paste.ubuntu.com/1171888)

I will retry with the Sputnik kernel.

---

### Post by YannBuntu on 2012-08-28
With the 3.2.0-30 Sputnik PPA kernel, with "i915.enable_backlight=0" and without "acpi_osi=":
- /sys/class/backlight folder exists but is empty
- Dmsg is [http://paste.ubuntu.com/1172044](http://paste.ubuntu.com/1172044) 
- brightness hotkeys have no effect
- There is no brightness cursor in the SystemSettings->Brightness and Lock menu

---

### Post by YannBuntu on 2012-08-28
With the 3.2.0-30 Sputnik PPA kernel, without "i915.enable_backlight=0" and without "acpi_osi=":
- /sys/class/backlight folder exists and contains both acpi_video0 & intel_backlight
- Dmsg is [http://paste.ubuntu.com/1172077](http://paste.ubuntu.com/1172077)
- brightness hotkeys have no effect
- The brightness cursor in the SystemSettings->Brightness and Lock menu is functional.

---

### Post by Toz on 2012-08-28
How about with "i915.enable_backlight=0" _and_ "acpi_osi="?

---

### Post by YannBuntu on 2012-08-28
With the 3.2.0-30 Sputnik PPA kernel, without "i915.enable_backlight=0" and with "acpi_osi=":
- /sys/class/backlight folder exists and contains only intel_backlight
- Dmsg is [http://paste.ubuntu.com/1172316](http://paste.ubuntu.com/1172316)
- brightness hotkeys are functional
- The brightness cursor in the SystemSettings->Brightness and Lock menu exists, moves, but has no effect.

---

### Post by YannBuntu on 2012-08-28
EDIT: See post #27

---

### Post by Toz on 2012-08-28
> **YannBuntu said:**
> With the 3.2.0-30 Sputnik PPA kernel, with "i915.enable_backlight=0" and with "acpi_osi=":
- /sys/class/backlight folder exists and contains only intel_backlight
- Dmsg is [http://paste.ubuntu.com/1172382](http://paste.ubuntu.com/1172382)
- brightness hotkeys are functional
- The brightness cursor in the SystemSettings->Brightness and Lock menu exists, moves, but has no effect.

According to that dmesg log, only acpi_osi= is set. Actually, both of the last two dmesg logs have only acpi_osi= set. Are these the right logs? Are you running "sudo update-grub" after every change to /etc/default/grub?

---

### Post by YannBuntu on 2012-08-29
Yes I run "sudo update-grub" after every change to /etc/default/grub, but I may have made a mistake, sorry. I'll redo it.

---

### Post by YannBuntu on 2012-08-29
Should be good this time:

With the 3.2.0-30 Sputnik PPA kernel, with "i915.enable_backlight=0" and with "acpi_osi=":
- /sys/class/backlight folder exists and is empty
- Dmsg is [http://paste.ubuntu.com/1173326](http://paste.ubuntu.com/1173326)
- brightness hotkeys are functional
- The brightness cursor in the SystemSettings->Brightness and Lock menu isn't present.

---

### Post by Toz on 2012-08-29
> [   18.866373] i915: Unknown parameter `enable_backlight'

Hmmmm.

Oh wait, from [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel]("https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel"),
> Previous versions of this kernel PPA involved a kernel boot parameter "i915.enable_backlight"; this parameter is no longer available.

I didn't notice that the first time around. Okay then, so that parameter isn't required for this kernel.

I'm sorry, but I'm afraid I'm out of ideas. It looks like "acpi_osi=" is your best bet now. I noticed that you've created a bug report. Perhaps you can get some resolution through that route.

---

### Post by YannBuntu on 2012-08-30
ok. Thanks anyway for having investigated.

---

### Post by YannBuntu on 2012-11-14
For information, I confirm that the tests below (done on Ubuntu12.04) are also valid on 12.10 (default kernel: 3.5.0-18 ).

> **YannBuntu said:**
> ```
$ echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
4
```

Works (change the real backlight) from 0 to 7.  
"8" returns :

```
$ echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness
8
tee: /sys/class/backlight/acpi_video0/brightness: Invalid argument
```


```
$ echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
2441
$ echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
2000
$ echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
1000
$ echo 100 | sudo tee /sys/class/backlight/intel_backlight/brightness
100
```

don't have any effect.

---

### Post by YannBuntu on 2012-12-15
Dear all,

the bug is fixed with kernel 3.7.0.

Thanks to everybody who contributed!

---

