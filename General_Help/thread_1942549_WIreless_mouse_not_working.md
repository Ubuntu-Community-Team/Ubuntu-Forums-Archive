---
title: "WIreless mouse not working"
date: 2012-03-17
forum: General Help
---

### Post by blackmail on 2012-03-17
Hello people, I am the happy user of 11.04 for some time, and no I will not switch to 11.10, but that's another story, the important part is that I have bought myself a little wireless mouse, it is manufactured by serioux, not a big company, but the mouse works fine, it has been tested on 3 windows machines and 2 linux machines, both having ubuntu 11.04 with all the upgrades available, just as my own system. My usb ports where all tested, and they work well, I have tested them with usb memory stick and with 2 other usb mice, as well as a Trust wireless mouse, they all respond, so it is not the usb ports.

I am fairly clueless, since these devices either work either they don't... so I really don't know what to use on them, this is the first tiome I have ever had this problem and I don't even know where to start. Thanks for any replies.

---

### Post by MisterGaribaldi on 2012-03-17
If you reboot (without doing anything else) from your Ubuntu LiveCD, does the mouse work there?

---

### Post by jquis8411 on 2012-03-17
is the mouse  listed if you type lsusb in a terminal?

---

### Post by blackmail on 2012-03-19
Hello, sorry i took so much time to respond...
The mouse is not shown with the LS USB command, and also I have reinstalled my OS, and in the Live CD it was also not recognized as well as on my freshly installed ubuntu OS it doesn't work either, and the weird thing is that my computer just slows down when the receiver is inserted in the USB port, but the little thing is not recognized by the lsusb or anyway not displayed... and is i hit lsusb without the receiver, it takes around 20-30 seonds to display the result, but without it did not take more than a fraction of a second to display the command result.
:mad::confused:

---

### Post by varunendra on 2012-03-19
After inserting the receiver, take a look at
```
dmesg | grep -i usb
```
or ```
dmesg | tail -20
```
to see if it logged any significant errors. Post them here if not sure.

---

### Post by cherideng on 2012-03-19
Code:
dmesg | grep -i usb
or
Code:
dmesg | tail -20

---

### Post by blackmail on 2012-03-20
Well it did say that it is unable to enumerate USB device on port 2
So I am baffled as to what can or could be done., and just to be sure here is the complete list for:
1) dmesg | grep -i usb:
```
[    0.193004] usbcore: registered new interface driver usbfs
[    0.193016] usbcore: registered new interface driver hub
[    0.193043] usbcore: registered new device driver usb
[    0.760047] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.760241] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.772023] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.772181] hub 1-0:1.0: USB hub found
[    0.772265] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.772521] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.846090] hub 2-0:1.0: USB hub found
[    0.846163] uhci_hcd: USB Universal Host Controller Interface driver
[    1.336014] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    2.278532] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
[    2.278730] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:02.0-3/input0
[    2.278938] usbcore: registered new interface driver usbhid
[    2.278941] usbhid: USB HID core driver
[    4.909607] usb 2-3: USB disconnect, address 2
[    6.296016] usb 2-3: new low speed USB device using ohci_hcd and address 3
[    6.519425] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4
[    6.519518] generic-usb 0003:1C4F:0003.0002: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:02.0-3/input0
[  846.194700] usb 2-3: USB disconnect, address 3
[  855.256054] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  855.473070] usb 2-2: unable to read config index 0 descriptor/start: -62
[  855.473080] usb 2-2: chopping to 0 config(s)
[  855.479089] usb 2-2: string descriptor 0 read error: -62
[  855.479366] usb 2-2: no configuration chosen from 0 choices
[  855.479439] usb 2-2: USB disconnect, address 4
[  855.728063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  855.976085] hub 2-0:1.0: unable to enumerate USB device on port 2
[  856.224066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  857.204072] hub 2-0:1.0: unable to enumerate USB device on port 2
[  857.452063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  857.700074] hub 2-0:1.0: unable to enumerate USB device on port 2
[  857.948063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  858.196096] hub 2-0:1.0: unable to enumerate USB device on port 2
[  858.444079] hub 2-0:1.0: unable to enumerate USB device on port 2
[  858.692067] hub 2-0:1.0: unable to enumerate USB device on port 2
[  858.940066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  859.188063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  859.436066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  859.684060] hub 2-0:1.0: unable to enumerate USB device on port 2
[  859.932224] hub 2-0:1.0: unable to enumerate USB device on port 2
[  860.180067] hub 2-0:1.0: unable to enumerate USB device on port 2
[  860.428063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  860.676090] hub 2-0:1.0: unable to enumerate USB device on port 2
[  860.924065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  861.172075] hub 2-0:1.0: unable to enumerate USB device on port 2
[  861.420061] hub 2-0:1.0: unable to enumerate USB device on port 2
[  861.668069] hub 2-0:1.0: unable to enumerate USB device on port 2
[  861.916085] hub 2-0:1.0: unable to enumerate USB device on port 2
[  862.164066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  862.412081] hub 2-0:1.0: unable to enumerate USB device on port 2
[  862.660071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  862.908070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  863.156065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  863.404070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  863.652156] hub 2-0:1.0: unable to enumerate USB device on port 2
[  863.900065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  864.148068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  864.396071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  864.644066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  864.892071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  865.140074] hub 2-0:1.0: unable to enumerate USB device on port 2
[  865.388086] hub 2-0:1.0: unable to enumerate USB device on port 2
[  865.636064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  865.884069] hub 2-0:1.0: unable to enumerate USB device on port 2
[  866.132066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  866.380072] hub 2-0:1.0: unable to enumerate USB device on port 2
[  866.628064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  866.876066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  867.124063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  868.104063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  868.352064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  868.600065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  868.848066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  869.096083] hub 2-0:1.0: unable to enumerate USB device on port 2
[  869.344057] hub 2-0:1.0: unable to enumerate USB device on port 2
[  869.592071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  869.840067] hub 2-0:1.0: unable to enumerate USB device on port 2
[  870.088073] hub 2-0:1.0: unable to enumerate USB device on port 2
[  870.336065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  870.584064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  871.564059] hub 2-0:1.0: unable to enumerate USB device on port 2
[  871.812062] hub 2-0:1.0: unable to enumerate USB device on port 2
[  872.060064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  873.040078] hub 2-0:1.0: unable to enumerate USB device on port 2
[  873.288066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  873.536078] hub 2-0:1.0: unable to enumerate USB device on port 2
[  873.784062] hub 2-0:1.0: unable to enumerate USB device on port 2
[  874.032068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  874.280066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  874.528071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  874.776063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  875.024063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  876.004081] hub 2-0:1.0: unable to enumerate USB device on port 2
[  876.252070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  876.500069] hub 2-0:1.0: unable to enumerate USB device on port 2
[  876.748099] hub 2-0:1.0: unable to enumerate USB device on port 2
[  876.996056] hub 2-0:1.0: unable to enumerate USB device on port 2
[  877.244073] hub 2-0:1.0: unable to enumerate USB device on port 2
[  877.492069] hub 2-0:1.0: unable to enumerate USB device on port 2
[  877.740070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  878.720065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  878.968063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  879.216063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  879.464066] hub 2-0:1.0: unable to enumerate USB device on port 2
[  879.712060] hub 2-0:1.0: unable to enumerate USB device on port 2
[  879.960090] hub 2-0:1.0: unable to enumerate USB device on port 2
[  880.208086] hub 2-0:1.0: unable to enumerate USB device on port 2
[  880.456079] hub 2-0:1.0: unable to enumerate USB device on port 2
[  880.704059] hub 2-0:1.0: unable to enumerate USB device on port 2
[  880.952086] hub 2-0:1.0: unable to enumerate USB device on port 2
[  881.200070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  881.448060] hub 2-0:1.0: unable to enumerate USB device on port 2
[  881.696064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  881.944068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  882.192063] hub 2-0:1.0: unable to enumerate USB device on port 2
[  882.440068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  882.688059] hub 2-0:1.0: unable to enumerate USB device on port 2
[  882.936067] hub 2-0:1.0: unable to enumerate USB device on port 2
[  883.184084] hub 2-0:1.0: unable to enumerate USB device on port 2
[  883.432064] hub 2-0:1.0: unable to enumerate USB device on port 2
[  883.680071] hub 2-0:1.0: unable to enumerate USB device on port 2
[  883.928065] hub 2-0:1.0: unable to enumerate USB device on port 2
[  884.176085] hub 2-0:1.0: unable to enumerate USB device on port 2
[  884.424093] hub 2-0:1.0: unable to enumerate USB device on port 2
[  884.672074] hub 2-0:1.0: unable to enumerate USB device on port 2
[  884.920082] hub 2-0:1.0: unable to enumerate USB device on port 2
[  885.168070] hub 2-0:1.0: unable to enumerate USB device on port 2
[  885.416068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  885.664068] hub 2-0:1.0: unable to enumerate USB device on port 2
[  885.912092] hub 2-0:1.0: unable to enumerate USB device on port 2
[  886.160061] hub 2-0:1.0: unable to enumerate USB device on port 2

```

and also for the
2) dmesg | tail -20 command

```
[ 1155.168068] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1155.416065] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1156.396068] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1156.644066] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1156.892065] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1157.140068] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1157.388101] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1157.636078] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1157.884068] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1158.132088] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1158.380068] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1158.628064] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1158.876079] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1159.124069] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1159.372060] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1159.620072] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1159.868067] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1160.116124] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1160.364063] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1160.612069] hub 2-0:1.0: unable to enumerate USB device on port 2

```

I have posted both of the versions, maybe you will see something I have missed, but I really hope to get this solved in one way or another, or to know at least why it is working on a laptop with the exact same OS and not on the desktop, the OS has the same updates and the same 11.04 version, it even works on windooz
:confused:[-o<](*,)

---

### Post by varunendra on 2012-03-21
Frankly, I have no idea what to do beyond this. So anyone who has a suggestion, please step in and share your ideas. Meanwhile, let's also take a look at:
```
lsmod
```IIRC, both usbhid and usbcore were associated with certain issues in the past, but I think they were power management related or something similar. So let's see in lsmod if something rings a bell.


**_EDIT_:**
Changing ports solved the problem at least for the user here: [http://askubuntu.com/questions/93840/mouse-isnt-recognized](http://askubuntu.com/questions/93840/mouse-isnt-recognized)
As he says, don't ask why.. ;) Just try and see if you are equally lucky.

---

### Post by gordintoronto on 2012-03-21
Is your mouse receiver plugged into a USB 2.0 port? EHCI only works on USB 2.0, I think. [http://www.gentoo.org/doc/en/usb-guide.xml](http://www.gentoo.org/doc/en/usb-guide.xml)

If you could paste the entire results from lsusb done on a computer where the mouse works, that might help.

---

### Post by blackmail on 2012-03-29
the entire lsusb on the laptop of my GF , the only linux machine so far on which this works is here:

```
johanna@Grumpy:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1d57:0016  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have tried running this on my computer and it just won't also I have just plugged in the receiver to the work computer (Windows 7 :| ) and it works right out of the box, but i fail to understand, I have a farly good computer and still it doesn't work, also all of the usb stuff workd, mainly this is the first wireless mouse that fails to work, and i am on the brink o being very frustrated...

Also lsmod | tail -20 on the working computer has the putput:

```
lsmod | tail -20
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451053  11 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40971  1 i915
psmouse                73312  0 
drm                   184164  12 i915,drm_kms_helper
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  4 
libahci                25548  1 ahci
tg3                   131476  0 

```

If anyone knows what to do just tell me...

---

### Post by gordintoronto on 2012-03-29
Have you tried plugging it in to every USB port?

---

### Post by blackmail on 2012-03-29
Yes I have tried and nothing...
On the laptop it works seamlessly and on my PC it just doesn't work... but it is the only USB device that doesn't work...

---

### Post by gordintoronto on 2012-03-30
What is the brand and model of the computer?

---

### Post by blackmail on 2012-04-28
Well it is an assembled computer... It has a Gigabyte motherboard, and a dual core AMD 4600 processor, on AM2 socket, nVidia 8400 video, 2 GB ram, a keyboard and a mouse (that won't work)

It is not from any particular manufacturer, like Dell or IBM or something.

oh I forgot to tell the Mainboard is GA-M61SME-S2.

---

### Post by gordintoronto on 2012-04-28
It's probably the combination of the motherboard and the dongle. Since it works on other computers, why not just put it on another computer, and use a different mouse on this one.

---

### Post by blackmail on 2012-05-12
that's what i did, i just didn't think of anything more clever either, but my problem was that i could not find out what happened...

THNX anywayz

---

