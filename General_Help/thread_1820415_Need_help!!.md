---
title: "Need help!!"
date: 2011-08-07
forum: General Help
---

### Post by new_b on 2011-08-07
I'm very new to the whole linux thing as the name suggests, I've just freshly installed the recent ubuntu version (11.04) 32bit version from a memory stick to run alongside windows. The issue I have is that although sometimes it boots perfectly from the window which asks me to chose whether I want to boot into linux or windows, other times it doesn't. I've tried different things but can't seem to find a pattern which explains why this happens and I've tried various things and am close to just giving up on linux so this is the final resort.

Additional details:
My system specifications are - 
64 bit
Toshiba
System model: Satellite Pro C650
BIOS: InsydeH2O Version 1.20
Processor: Intel(R) Celeron(R) CPU 2.20GHZ
2048mb RAM
Directx 11

Any advice is appreciated on how to fix this issue, but please word it in plain English as my tech terminology isn't great at the moment.

---

### Post by fdrake on 2011-08-07
I don't mean to be a pain but since you are new to Ubuntu i suggest you to install always the long term support release "which now is 10.04".

said that, can you be more descriptive on the problem? it looks like you have problem with the GRUB loader menu. What exactly happens? You don't see the menu? or it does not boot when you select the OS you want to boot?

---

### Post by new_b on 2011-08-07
> **fdrake said:**
> I don't mean to be a pain but since you are new to Ubuntu i suggest you to install always the long term support release "which now is 10.04".

said that, can you be more descriptive on the problem? it looks like you have problem with the GRUB loader menu. What exactly happens? You don't see the menu? or it does not boot when you select the OS you want to boot?

I wasn't aware of the "long term support release" version but if I can't solve this then I will download that one. And I do see the menu, although the message saying "highlighted option will be chosen in 10 secs" appears sometimes and when it does appear and I let the 10 seconds pass then linux starts up normally - the times it doesn't appear it doesn't start and goes blank instead (from my experience so far). Also, when it goes blank the "caps lock" button often flashes on my keyboard for a certain amount of time before the laptop reboots and I'm bought to the menu again

Hope that's enough information...

---

### Post by fdrake on 2011-08-07
are you running windows 7 or something else? win 7 is known for havving problem with the grub. Depending on the win that you use we have to take different approach

---

### Post by maxar6 on 2011-08-07
You installed a 32 bit version of ubuntu on a 64 bit computer it may be best to install the 64 bit version. Also installing from flash drive have had problems before would be safer to install from a cd.

---

### Post by wildmanne39 on 2011-08-07
Hi, you are fine with the 32 bit version.

Also you should not be having any problems from installing using usb stick.

Is this a wubi install?

---

### Post by new_b on 2011-08-07
Yes, I'm running windows 7 fdrake. What do you think the approach to this should be?

Maxar I installed the 32 bit version because my friend said that the 64bit is unstable and it wouldn't make a difference if I got the 64bit version because my computer only has 2 gig ram. Does my friend know what he's talking about? haha

And wildmanne, as far as I know wubu is what allows linux to run from inside of windows and my friend warned me against that so I resized an existing hard drive and took the free space available to partition it and run this version of linux alongside windows. When I boot up my computer it asks me to chose either linux, linux (recovery mode), two random things, and windows 7(loader)

Hope that helps you guys to deduce something!

---

### Post by wildmanne39 on 2011-08-07
Hi, it is likely a video card driver issue, you can try booting with nomodeset, or when it boots properly check additional drivers and see if there is one there for your card.

Here is a link for nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Sometimes even when you install the driver it does not work well with 11.04 so you might can try another driver for your card.

But if you post the outcome of these commands here it will take some of the guess work out.
```
sudo lshw
```
```
lsmod
```
Post here by clicking on new reply and click # and paste the information between the brackets.

Also 64 bit is not unstable, but with 2 gigs of ram you do not need it.
Thank you

---

### Post by new_b on 2011-08-08
The search for additional drivers resulted that there are no proprietary drivers in use on this system. 

Also, I realised that the screen size changes as it pleases and I have to change it back with the xrandr command. 

Sudo lshw asks for [sudo] password for user

lsmod lists a lot of stuff, which I'll put below
```

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  3 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_conexant    43782  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
ath9k                 103633  0 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  3 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
binfmt_misc            13213  1 
mac80211              257001  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_common           13611  1 ath9k
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
ath9k_hw              300328  2 ath9k,ath9k_common
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19141  2 ath9k,ath9k_hw
uvcvideo               66851  0 
psmouse                73312  0 
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  3 ath9k,mac80211,ath
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
video                  18951  1 i915
sparse_keymap          13666  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 

```

---

### Post by wildmanne39 on 2011-08-08
Hi, when you run this command:
```
sudo lshw
```
type your login password into the terminal.
It will not be displayed on the screen, so when you are done hit enter and the command will be carried out.

You have an intel graphics card so the driver should be installed properly, but run this command to see.
```
lspci -k
``` 

There are issues with the intel graphics but I have not seen booting issues as being one of them.

You should probably try nomodeset in the link I gave you to see if that fixes your boot issue and if it does you can use the directions in the link to make it permanent.

---

### Post by 3rdalbum on 2011-08-08
An intermittant fault like this that causes a kernel panic (the blinking keyboard lights) sounds like something to do with hardware. As it appears to be happening before the GUI desktop loads, I'd guess that it's probably bad RAM.

You could try running Memtest from the GRUB menu; you might need to run it overnight to get a result. Or run the Phoronix Test Suite's memory benchmarks and you might get an instant crash if it's faulty RAM. The most reliable way is to remove RAM modules and see if the problem still occurs, but this might be impractical for a laptop computer.

---

### Post by 3rdalbum on 2011-08-08
> **wildmanne39 said:**
> 
There are issues with the intel graphics but I have not seen booting issues as being one of them.

I don't think Celerons use the Sandy Bridge architecture that's been causing problems.

---

### Post by new_b on 2011-08-08
> **wildmanne39 said:**
> Hi, when you run this command:
```
sudo lshw
```
type your login password into the terminal.
It will not be displayed on the screen, so when you are done hit enter and the command will be carried out.

You have an intel graphics card so the driver should be installed properly, but run this command to see.
```
lspci -k
``` 

There are issues with the intel graphics but I have not seen booting issues as being one of them.

You should probably try nomodeset in the link I gave you to see if that fixes your boot issue and if it does you can use the directions in the link to make it permanent.

The code described in that link for nomodeset isn't exactly the same as the one I am given, so I'm unsure of the exact place to put nomodeset after the grub menu, but I'll let the computer log in and change to nomodeset permanently to see what happens. 

I will run the command now and inform you of what happens. I really want to get this fixed today so I can continue with the work I need to do on linux so any suggestions from anyone will be very helpful!

---

### Post by new_b on 2011-08-08
If you're instructing me to take the laptop apart, I think that's a bit too much for something like this considering I'm not even familiar with linux.

Do you guys think the earlier version would work properly on my system? I really need this for next year of my uni course so I'm trying to get some practise on it. It doesn't really matter about version. If so, how do I uninstall the current one I've got.

---

### Post by wildmanne39 on 2011-08-08
Hi, it is hard to say,if it is a hardware issue then it will not help.

If it is not a hardware issue then possibly.

If you are going to try another version I recommend 10.04 Lts, just go to the ubuntu  download site and download it.

Put in the cd and reformat your ubuntu partitions and install, if you choose along side it would just take up more space and you would have two versions of ubuntu on your system.

---

### Post by new_b on 2011-08-08
How can this be a hardware issue, I swear linux is supposed to be better than this. My laptop isn't even that old. 

But okay I'm gonna wait a little while in case someone knows an easy fix otherwise I guess reinstallation is my only option :(

---

### Post by wildmanne39 on 2011-08-08
Hi, did you try nomodeset? I had a problem almost like yours, I had to use the nomodeset option.

Also the output from those last two commands I asked you to run might help us.

---

### Post by new_b on 2011-08-08
Yes, I've tried the nomodeset option and it hasn't achieved anything :( I even put it in permanent and still nothing.

Another thing I just noticed during my several attempts of trying to log into linux again was when i chose the linux (recovery) option from the grub menu then from the recovery menu chose dpkg - "repair broken packages", it runs a lot of commands etc. then always says 
```
200 upgraded, 7 newly installed, 0 to remove and 0 not upgraded
Need to get 47.9mb/215mb of archives 
After this operation 223mb of additional disk space will be used. Do you want to continue? Y/n?
```

After I click yes then restart, it always lets me log into linux but right after when I restart again I hit the same problem. But I find it weird how it always says 223mb of additional disk space will be used even though I did it before. This may be nothing relevant but just thought maybe with this extra info you can find a solutionto this problem.

---

### Post by wildmanne39 on 2011-08-08
Hi, I have researched your problem but I did not find an answer.

With you computer it would run better with 10.04 but I do not know if it will fix this problem.

---

### Post by new_b on 2011-08-09
hmm okay I guess I will do that then. One last thing, how exactly do I uninstall this?

I tried to boot the memory stick I installed linux with hoping there would be an uninstall option but there wasn't...

---

### Post by bcbc on 2011-08-09
> **new_b said:**
> hmm okay I guess I will do that then. One last thing, how exactly do I uninstall this?

I tried to boot the memory stick I installed linux with hoping there would be an uninstall option but there wasn't...

First reinstall the windows bootloader. You can use a windows repair CD for this, boot to a repair command prompt and run: ```
bootrec /fixmbr
```
Second, make sure it boots straight into windows when you start your computer.
Third, delete the ubuntu partition, format and reuse, or merge it back.

If you remove the ubuntu partition first, then windows won't boot.

---

### Post by wildmanne39 on 2011-08-09
Hi, if you are going to install 10.04, just set your computer to boot from the livecd when you start the install process, in the partitions section of the process chose manual partitioning and reformat the ubuntu partitions and install 10.04 on to those partitions.

Be very careful make sure you only reformat the ubuntu partitions.

---

