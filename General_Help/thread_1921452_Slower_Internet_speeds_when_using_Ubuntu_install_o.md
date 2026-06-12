---
title: "Slower Internet speeds when using Ubuntu install of dual-boot Ubuntu/Windows 7 system"
date: 2012-02-06
forum: General Help
---

### Post by Paperypip on 2012-02-06
I've been using a dual-boot Ubuntu 11.10 64-bit/Windows 7 system the past several months and for the most part I'm very pleased with it. However, when I am using the system while loaded into Ubuntu, my download speeds are noticably slower than when I'm using Windows. Furthermore, it's fairly common to see time-outs when I try to load a new web page, or for me to be disconnected from an instant messenger service I'm using. There are no such difficulties when using the Windows half of the machine so I think it's something to do with Ubuntu. What might be going on and how might I diagnose/fix this issue?

---

### Post by Penguinnerd on 2012-02-06
Probably a good start would be to describe the hardware (Wifi/ethernet hardware and such) and tell us if you've had to install special drivers in either Windows or Ubuntu for the networking.

---

### Post by Paperypip on 2012-02-06
I have a wired connection connected to the integrated network card of a Gigabyte GA-Z68XP-UD3. I have never installed special driver software in either Ubuntu or Windows.

---

### Post by varunendra on 2012-02-06
For a more comprehensive info, please post the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
```Please wrap the outputs in [noparse]```
..and..
```[/noparse] tags by clicking on '#' at the top of the box (in which you create new posts) to create the tags, then copy-paste the output in-between those tags. This preserves the formatting and makes it easily readable.


**_Edit_:**
As apparent from your Motherboard's specs, if it is an RTL8111E chip using R8169 driver (output of lspci..) then please try this solution first: [http://ubuntuforums.org/showpost.php?p=11477748&postcount=4](http://ubuntuforums.org/showpost.php?p=11477748&postcount=4)

Whether it helps or not, please post the outputs I asked anyway, as it helps us as confirmation to a particular problem/solution.

---

### Post by Paperypip on 2012-02-07
I'm not clear whether you want to see the outputs from those commands before or after I try that solution so I am going to post both- here are the outputs of the commands before.

```

keegan@keegan-Z68XP-UD3P:~$ uname -mr
3.0.0-15-generic x86_64
keegan@keegan-Z68XP-UD3P:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
keegan@keegan-Z68XP-UD3P:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  5 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
nvidia              11713772  40 
snd_usb_audio         118122  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_usbmidi_lib        25371  1 snd_usb_audio
i915                  567092  1 
drm_kms_helper         42558  1 i915
drm                   236290  2 i915,drm_kms_helper
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
mxm_wmi                12979  0 
i2c_algo_bit           13423  1 i915
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
video                  19412  1 i915
wmi                    19256  1 mxm_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
xhci_hcd               82820  0 
keegan@keegan-Z68XP-UD3P:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:49:fa:5c  
          inet addr:128.189.187.25  Bcast:128.189.187.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe49:fa5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100352 errors:0 dropped:100352 overruns:0 frame:100352
          TX packets:147045 errors:0 dropped:100 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76403054 (76.4 MB)  TX bytes:122331713 (122.3 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37263 (37.2 KB)  TX bytes:37263 (37.2 KB)

keegan@keegan-Z68XP-UD3P:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

keegan@keegan-Z68XP-UD3P:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain resnet.ubc.ca.
search resnet.ubc.ca.
nameserver 142.103.1.42
nameserver 137.82.1.2

```

Here are the results after:

```


keegan@keegan-Z68XP-UD3P:~$ uname -mr
3.0.0-15-generic x86_64
keegan@keegan-Z68XP-UD3P:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8168
keegan@keegan-Z68XP-UD3P:~$ lsmod
Module                  Size  Used by
r8168                 211483  0 
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  5 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
nvidia              11713772  40 
snd_usb_audio         118122  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_usbmidi_lib        25371  1 snd_usb_audio
i915                  567092  1 
drm_kms_helper         42558  1 i915
drm                   236290  2 i915,drm_kms_helper
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
mxm_wmi                12979  0 
i2c_algo_bit           13423  1 i915
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
video                  19412  1 i915
wmi                    19256  1 mxm_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
xhci_hcd               82820  0 
keegan@keegan-Z68XP-UD3P:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:49:fa:5c  
          inet addr:128.189.187.25  Bcast:128.189.187.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe49:fa5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:332154 (332.1 KB)  TX bytes:99756 (99.7 KB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49487 (49.4 KB)  TX bytes:49487 (49.4 KB)

keegan@keegan-Z68XP-UD3P:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

keegan@keegan-Z68XP-UD3P:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain resnet.ubc.ca.
search resnet.ubc.ca.
nameserver 142.103.1.42
nameserver 137.82.1.2

```

---

### Post by varunendra on 2012-02-07
Oh sorry, I should have made it clear.
> **Paperypip said:**
> 
```
....
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. [COLOR=Red]**RTL8111/8168B**[/COLOR]
..
..
    Kernel driver in use: [COLOR=Red]**r8169**[/COLOR]
```
Actually, based on your motherboard's model, I already suspected the above combination, which is usually problematic. But IF the solution worked, you could just move on without posting back anything, since you no longer needed help. So I asked to post the outputs anyway (before or after - doesn't matter) just for confirmation that the problem still exists, and that solution works.

So, did it solve the problem? From the 'post-fix' status, it seems you are good now!
Earlier status:
> **Paperypip said:**
> ```

keegan@keegan-Z68XP-UD3P:~$ ifconfig
          RX packets:100352 errors:0 **[COLOR=Red]dropped:100352[/COLOR] **overruns:0 frame:100352
```

While current status:
> **Paperypip said:**
> ```

          RX packets:2841 errors:0 **dropped:0** overruns:0 frame:0
```

---

### Post by dcstar on 2012-02-08
And of course, if it is "solved" someone might actually use the bug reporting system and put this issue in a place where it might actually get fixed properly?

If people continually find "workarounds" and do not use the mechanisms that exist to actually properly address problems, then more people in the future will have this exact same issue.

---

### Post by varunendra on 2012-02-08
> **dcstar said:**
> And of course, if it is "solved" someone might actually use the bug reporting system and put this issue in a place where it might actually get fixed properly?
True!

Due to this and many other similar issues, I often feel compelled to file a bug report myself. But to be honest - firstly, I'm not sure if I'd be the right person do that, because it's not me who is affected by the bug; and secondly, I don't really know the correct procedure yet. Is it simple enough for normal users as well who don't want to go into technical details?

I'd appreciate if you could point me to an easy and a straightforward method to file such bug reports and tell me who can do it. Maybe I could start requesting people to do that, or do it myself if it is okay (although I don't think so).

Sorry if I sound ignorant. Of-course I haven't done my homework in this regard and I admit my laziness..:redface:

As for the OP, I'd strongly suggest to do that since he/she is the one who is affected right now, _and would get affected again everytime a kernel update occurs_!

---

### Post by Paperypip on 2012-02-08
Okay, so since I made the adjustments posted earlier I've had no issues. When I get the chance later this week I'll look into how to file a bug report and do so. Thanks for the help everyone. :D

---

### Post by varunendra on 2012-02-08
You're always welcome!

And your intentions to help improve Ubuntu (and Linux in general) are quite appreciated. After all, 'Open Source' means it is 'Ours', and thus it is 'we' who have to make it the way we want it to be.

---

### Post by dcstar on 2012-02-08
Everybody should have a quick look at this:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Paperypip on 2012-02-09
I'm making another post and unmarking this as solved because my solution appears to have undone itself (I suppose this may have happened while updating?). I noticed I was getting the slow speeds again and I ran the same commands as before and I noticed it's using the r8169 driver again. How do I get it to stick? edit: There was a "blacklist" step in the post that I followed to downgrade to the r8168 driver but I suppose it didn't work for some reason?

Most recent information:
```

keegan@keegan-Z68XP-UD3P:~$ uname -mr
3.0.0-15-generic x86_64
keegan@keegan-Z68XP-UD3P:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
keegan@keegan-Z68XP-UD3P:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  5 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
nvidia              11713772  40 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mxm_wmi                12979  0 
serio_raw              13166  0 
mei                    41480  0 
wmi                    19256  1 mxm_wmi
i915                  567092  1 
drm_kms_helper         42558  1 i915
drm                   236290  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
xhci_hcd               82820  0 
keegan@keegan-Z68XP-UD3P:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:49:fa:5c  
          inet addr:128.189.187.25  Bcast:128.189.187.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe49:fa5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113155 errors:0 dropped:113155 overruns:0 frame:113155
          TX packets:30013 errors:0 dropped:106 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44210883 (44.2 MB)  TX bytes:4644698 (4.6 MB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

keegan@keegan-Z68XP-UD3P:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

keegan@keegan-Z68XP-UD3P:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain resnet.ubc.ca.
search resnet.ubc.ca.
nameserver 142.103.1.42
nameserver 137.82.1.2

```

---

### Post by varunendra on 2012-02-09
Firstly, thanks for the valuable feedback, it is important and appreciated.

Now about the problem-
What happens if you do:
```
sudo modprobe -rfv r8169
sudo modprobe -v r8168
```
Does it give any errors? Does it make things normal again (temporarily of-course)?

---

### Post by Paperypip on 2012-02-14
Didn't get the chance to do this till now. Last night Ubuntu updated itself from 3.0.0-15 to 3.0.0-16 and since then my Internet connection hasn't worked at all on that half of the machine (currently posting while using the Windows half).

I tried what varunendra just suggested (admittedly after the update and so after I lost my Internet connection) and got this:

```

keegan@keegan-Z68XP-UD3P:~$ sudo modprobe -rfv r8169
[sudo] password for keegan: 
keegan@keegan-Z68XP-UD3P:~$ sudo modprobe -v r8168
FATAL: Module r8168 not found.

```

---

### Post by varunendra on 2012-02-15
Just like I mentioned in post #8, it'll break with every kernel update, requiring you to compile it again. So keep the original downloaded source (unless you get a newer and better one), and run the same installation procedure with each kernel upgrade.

You are completely disconnected because, I guess, the r8168 driver is broken with the kernel upgrade and the native r8169 is blacklisted. Although your previous outputs showed it being loaded, I don't know how it could despite being blacklisted. I have at least one more thread at hand where it happened, but the OP there hasn't posted for a while. So couldn't figure out why it got loaded even with blacklisting.

However, I myself tried recently to compile the r8168 driver, downloaded from realtek's site, using their recommended method in the readme file (just run ./autorun.sh), and it compiled like a charm. Just make sure all the support packages are preinstalled (current kernel headers, dkms, build essential).

To see whether a driver is currently associated or not, please check(before compiling the 8168 driver):
```
lspci -nnk | grep -iA2 RTL8111
```
If it shows r8169, please also post the out put of,
```
cat /etc/modprobe.d/blacklist.conf | grep r81
```

As for re-compiling and loading the r8168 driver, the procedure should be:
```
sudo modprobe -rfv r8169
(then compile the r8168 driver as per instructions in readme file- which is just running sudo ./aururun.sh from within extracted directory)
sudo modprobe -v r8168
```

---

### Post by ercolesptr on 2012-02-26
> **varunendra said:**
> Just like I mentioned in post #8, it'll break with every kernel update, requiring you to compile it again. So keep the original downloaded source (unless you get a newer and better one), and run the same installation procedure with each kernel upgrade.

You are completely disconnected because, I guess, the r8168 driver is broken with the kernel upgrade and the native r8169 is blacklisted. Although your previous outputs showed it being loaded, I don't know how it could despite being blacklisted. I have at least one more thread at hand where it happened, but the OP there hasn't posted for a while. So couldn't figure out why it got loaded even with blacklisting.

However, I myself tried recently to compile the r8168 driver, downloaded from realtek's site, using their recommended method in the readme file (just run ./autorun.sh), and it compiled like a charm. Just make sure all the support packages are preinstalled (current kernel headers, dkms, build essential).

To see whether a driver is currently associated or not, please check(before compiling the 8168 driver):
```
lspci -nnk | grep -iA2 RTL8111
```If it shows r8169, please also post the out put of,
```
cat /etc/modprobe.d/blacklist.conf | grep r81
```As for re-compiling and loading the r8168 driver, the procedure should be:
```
sudo modprobe -rfv r8169
(then compile the r8168 driver as per instructions in readme file- which is just running sudo ./aururun.sh from within extracted directory)
sudo modprobe -v r8168
```


I have the same problem and using this method it solves it. However every time I restart I get back that r8169 driver even though it is in the blacklist. How can i make it permanently r8186?

I noticed that the r8186 driver is still there and I do not have to make it again I just need to disable the bad one and activate the new one with:

sudo modprobe -rfv r8169 
sudo modprobe -v r8168

But I have to do this at every restart. How can I make it permanent at least when no updates have been done.

---

### Post by ercolesptr on 2012-02-26
OK at last I found the solution. I just needed to add the last 2 lines to the original ones in terminal. So for the benefit of people having this same problem here are all the lines you need to enter to solve this bug.

sudo -s
apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget [http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2)
tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
modprobe -rfv r8169
make
cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
depmod -a
modprobe -v r8168
echo "blacklist r8169" | tee -a /etc/modprobe.d/blacklist.conf

mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
echo “r8168&#8243; >> /etc/modules

---

### Post by varunendra on 2012-03-01
Thanks for the input *ercolesptr*, I'm sure this would help others too. I'm going to simply link to your post in another thread with similar problem and am quite hopeful it would work the same way for the poster there.

---

