---
title: "Computer Freezes Continuously"
date: 2010-02-15
forum: General Help
---

### Post by 1awesomeguy on 2010-02-15
Hey Guys!

My desktop computer freezes continuously. I just has to restart it five times in a row because I was trying to watch a movie and browser the Internet at the same time. The computer always freezes when I am doing a task such as opening a new window, clicking on something, etc. It will never freeze if it is just sitting there.

I built this computer myself so it may be my poor workmanship that has causes this problem. This has been happening for about three to four years and I have no idea how to fix the issue. The computer currently runs Ubuntu 9.10 but has run previous versions of Ubuntu as well as Windows XP and has shown the same problem..

Any help in diagnosing the problem and fixing it will be greatly appreciated!

Thank you!

---

### Post by switch10 on 2010-02-15
How old is the machine?  Sounds like the RAM is crapping out.  Run a live cd and test your RAM.

Dave

---

### Post by mechro on 2010-02-15
Check your CPU temperature...

```
 cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by 1awesomeguy on 2010-02-16
Thanks guys for the tips.

My current CPU temperature is at 40 degrees C, with the computer on since this morning. That does not sound alarming to me, but I also did not use the computer for the last couple of hours. Is there a way I can stress test the CPU to see if it is causing the problem?

I ran a memtest from the live cd for a couple of hours and got one and a half passes through. No failures.

Any more ideas?

---

### Post by Richard1979 on 2010-02-16
Could be the GPU or graphics card RAM, do you have a spare graphics card around?

---

### Post by 1awesomeguy on 2010-02-16
> **Richard1979 said:**
> Could be the GPU or graphics card RAM, do you have a spare graphics card around?

Unfortunately, no. I could try removing the graphics card (the motherboard also has an on-board graphics card), but since my computer freezes erratically, I would not know if I have identified the problem. Any way to test this or any ideas on how I can force a compute freeze? It doesn't seem to happen when I want it to...

My novice mind was thinking this problem is most likely due to the CPU since it always seems to happen right after I click on a folder icon, or right after I load a new website, always right after I do something. It may be RAM or the graphics cars, but I am not entirely sure how to do an effective test. I think, the RAM stress test I did from the live CD rules out RAM?

---

### Post by switch10 on 2010-02-16
Take your video card out of your computer.

Plug your monitor into your on-board graphics card.

Boot up and see if your problem still exists.  If it does it is not your graphics card.

It sounds like your memory is fine.

---

### Post by HermanAB on 2010-02-16
Howdy,

It could also be the graphics driver - not the hardware.  The latest Nvidia driver is unusable to me since it causes frequent crashes on my Toshiba laptop.  Try the VESA driver and see whether the problem persists.

---

### Post by Autodave on 2010-02-16
I don't know if this will help you or not, but I had problems very similar to your problem and I came across the answer quite by accident while reading the forums.  If you have installed Compiz, delete or disable it.

---

### Post by 1awesomeguy on 2010-02-16
> **Autodave said:**
> I don't know if this will help you or not, but I had problems very similar to your problem and I came across the answer quite by accident while reading the forums.  If you have installed Compiz, delete or disable it.

Thanks everyone for the suggestions. I am going to try Autodave's advice on disabling Compiz. I will just use my computer normally and see if the problem persists. If I do not reply to this post, this most likely solved my problems.

---

### Post by 1awesomeguy on 2010-02-17
Disabling Compiz did not work... :(

My computer just froze twice in a row. Tested CPU temp and it is at 40 degrees C.

Can anyone give me instructions on disabling my graphics driver and installing the VESA driver? Google did not help. The only thing I did was install the default graphics driver when you select 'Advanced Desktop Effects' (which is now disabled). Also, I have an ATI graphics card.

---

### Post by mechro on 2010-02-18
> **1awesomeguy said:**
> 
Can anyone give me instructions on disabling my graphics driver and installing the VESA driver? Google did not help. The only thing I did was install the default graphics driver when you select 'Advanced Desktop Effects' (which is now disabled). Also, I have an ATI graphics card.

Try this...

Disable your ATI graphics driver. In a Terminal do **gksudo nautilus**. Navigate to **/etc/X11/xorg.conf** and rename xorg.conf to xorg.conf(copy) or similar. Reboot and a basic xorg.conf should be regenerated.

Navigate again to xorg.conf and edit the Device section to read...

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

Reboot, cross fingers and hope for best!

---

### Post by 1awesomeguy on 2010-02-19
> **mechro said:**
> Try this...

Disable your ATI graphics driver. In a Terminal do **gksudo nautilus**. Navigate to **/etc/X11/xorg.conf** and rename xorg.conf to xorg.conf(copy) or similar. Reboot and a basic xorg.conf should be regenerated.

Navigate again to xorg.conf and edit the Device section to read...

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

Reboot, cross fingers and hope for best!

After deleting xorg.conf, my computer does not regenerate one after I reboot it. It is behaving normally, minus the whole freezing situation.

---

### Post by mechro on 2010-02-19
Yeah, I think the latest Ubuntu method of configuring the X system is not to bother with an xorg.conf unless one is needed. So in your case enabling the ATI graphics driver probably generates the xorg.conf.

If you've lost the freezing problems then it does sound like the graphics driver.

Cool! Well done! Sorted, mate!

---

### Post by 1awesomeguy on 2010-02-19
> **mechro said:**
> Yeah, I think the latest Ubuntu method of configuring the X system is not to bother with an xorg.conf unless one is needed. So in your case enabling the ATI graphics driver probably generates the xorg.conf.

If you've lost the freezing problems then it does sound like the graphics driver.

Cool! Well done! Sorted, mate!

No, I haven't lost the freezing problem... :(

All I did was delete the file and a new one did not appear. The computer is still freezing...

---

### Post by mechro on 2010-02-19
OK :(

If you don't want to remove your graphics card you could try "blacklisting" it in /etc/modprobe.d/blacklist.conf... first you need to identify the name of the graphics module that your system is using...

In a Terminal do **lsmod**. Can you identify the graphics module from the list? If not, post the output here.

---

### Post by 1awesomeguy on 2010-02-24
> **mechro said:**
> OK :(

If you don't want to remove your graphics card you could try "blacklisting" it in /etc/modprobe.d/blacklist.conf... first you need to identify the name of the graphics module that your system is using...

In a Terminal do **lsmod**. Can you identify the graphics module from the list? If not, post the output here.

Not sure what I should be looking for here.

```
chris@computer:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
vboxnetflt            100300  0 
vboxnetadp             93292  0 
vboxdrv              1708524  1 vboxnetflt
arc4                    2144  2 
ecb                     3296  2 
rt61pci                23556  0 
crc_itu_t               2336  1 rt61pci
rt2x00pci               9216  1 rt61pci
rt2x00lib              34624  2 rt61pci,rt2x00pci
led_class               5256  1 rt2x00lib
input_polldev           4720  1 rt2x00lib
mac80211              210008  2 rt2x00pci,rt2x00lib
snd_intel8x0           36872  2 
snd_ac97_codec        125720  1 snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
iptable_filter          3872  0 
snd_pcm                93160  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
amd64_edac_mod         26688  0 
snd_seq_dummy           3460  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
joydev                 13088  0 
cfg80211              109144  2 rt2x00lib,mac80211
eeprom_93cx6            2528  1 rt61pci
serio_raw               6596  0 
lp                     11908  0 
edac_core              48876  1 amd64_edac_mod
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               8098608  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_intel8x0,snd_pcm
i2c_nforce2             8168  0 
ppdev                   8232  0 
k8temp                  5504  0 
parport_pc             37352  1 
parport                40528  3 lp,ppdev,parport_pc
usbhid                 43968  0 
forcedeth              61292  0 
floppy                 65192  0 
```

---

### Post by mechro on 2010-02-24
I can't see anything related to ATI in there. You have nvidia stuff... is that your on board graphics?

Sorry, but I'm now out of my depth :neutral: Can only suggest you remove your ATI card and see if you still get the "freezing".

---

