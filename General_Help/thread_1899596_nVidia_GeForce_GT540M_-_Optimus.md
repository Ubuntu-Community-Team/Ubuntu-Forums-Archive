---
title: "nVidia GeForce GT540M - Optimus"
date: 2011-12-23
forum: General Help
---

### Post by 9antreas9 on 2011-12-23
I just bought a laptop that has the nvidia geforce gt540m video card.

I have ubuntu 11.10 oneiric installed with wubi.

I understand that now my system powers the video card at all times but  uses the onboard chip at all times, meaning a big waste of power, and big battery duration time reduction.

I use linux only for php development, which basically only requires a text editor, plus the occasional movie, so I don't need really good graphic support.

So, I want a way to ether manage the dual graphic card settings so i have what i want on demand, or if possible a way to tottally turn of the gt540m card and use the onboard chip at all times, so that my battery does not get wasted without good reason.

Any ideas?

---

### Post by yaliny on 2011-12-25
Hi,

I've got Nvidia 550m on my Asus N53S. While reading to how to utilize nvidia card found this note. I don't need power management so I haven't used it and don't know how to work with.

You may want to give a try.
[https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI-Removed](https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI-Removed)

best luck.

---

### Post by wildmanne39 on 2011-12-25
Hi, there is still many problems with getting that nvidia card to work, you can blacklist the driver and it will be disabled.

This is the command assuming the driver just says nvidia which I believe it does.
```
sudo su
echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf
exit
``` 
Thanks

---

### Post by 9antreas9 on 2011-12-25
@[wildmanne39]("http://ubuntuforums.org/member.php?u=508533"): blacklisting the driver will turn off the card and make it stop eating up battery, or is it just for switching to the onboard card, while the nvidia card is still powered?

Also, I found a way to disable my card, and got +1h in my battery life time. Problem is it is not saved, so when I boot my system, I have to run it again. Will post it here asap.

---

### Post by wildmanne39 on 2011-12-25
Hi, if it is what is eating your battery life then it will stop, the card will be disabled.

There is a bug for battery consumption I do not think it has been fixed yet but I believe there is a work around and I have read that installing a package called jupiter will help.

You can google battery issues in ubuntu and and the package jupiter for more information.
Thanks

---

### Post by 9antreas9 on 2011-12-26
Actually when I installed Ubuntu on my system I also installed the nvidia card driver. Installing the graphics card driver made compiz config behave bad, so I tried uninstalling the driver, but since I am not a skilled user, I could not.

So I installed Ubuntu from scratch, and I never installed the nvidia driver.

The laptop battery dies after one hour max, and the laptop is 4 days old.

I found this link [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html) and it helped me turn the card off, but every time I reboot, I have to run 3 commands in terminal to turn it off.

With the card off, battery lifetime is around 2:20, so it's really worth doing it evry single time, but a more permanent solution wouldn't be bad.

You are suggesting I should install the nvidia driver, then do what you posted above and my system will have permanently disabled the nvidia card?

---

### Post by wildmanne39 on 2011-12-26
Hi, if you never installed the driver it should be disabled unless it is using the nouveau driver, please post the output of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

This will tell us if the other driver is being used instead.
Thank you

---

### Post by 9antreas9 on 2011-12-26
```
anpel@ubuntu:~$ lsmod
Module                  Size  Used by
acpi_call              12748  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
nouveau               728662  0 
ttm                    76805  1 nouveau
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtlwifi               110972  1 rtl8192ce
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              199587  2 rtlwifi,mac80211
i915                  566827  3 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  2 nouveau,i915
drm                   236290  6 nouveau,ttm,i915,drm_kms_helper
mei                    41480  0 
mxm_wmi                12979  1 nouveau
i2c_algo_bit           13423  2 nouveau,i915
video                  19412  2 nouveau,i915
wmi                    19256  1 mxm_wmi
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  1 
libahci                26861  1 ahci
jme                    41301  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
xhci_hcd               82820  0 
anpel@ubuntu:~$ 

```

That is after i've disabled the card using the way i posted above.

Should I reboot and post info with the card not deactivated?

---

### Post by wildmanne39 on 2011-12-26
Hi, I was correct the nouveau driver is loaded since you did not install the nvidia that is a default driver.

If you run this command it will blacklist the driver and as long as you do not install nvidia you should be okay.
```
sudo su
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
exit
```
again there are issues with power consumption that have nothing to do with that video card and installing jupiter is suppose to help.
Thanks

---

### Post by 9antreas9 on 2011-12-26
I already installed Jupiter.

Also I did what you said above and rebooted my system. This is what lsmod outputs now.

```
anpel@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
i915                  566827  3 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rtlwifi               110972  1 rtl8192ce
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42558  1 i915
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72711  0 
snd_timer              29991  2 snd_pcm,snd_seq
drm                   236290  4 i915,drm_kms_helper
mac80211              462092  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
videodev               92992  1 uvcvideo
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
i2c_algo_bit           13423  1 i915
v4l2_compat_ioctl32    17083  1 videodev
soundcore              12680  1 snd
jmb38x_ms              17646  0 
cfg80211              199587  2 rtlwifi,mac80211
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mxm_wmi                12979  0 
memstick               16569  1 jmb38x_ms
wmi                    19256  1 mxm_wmi
video                  19412  1 i915
ahci                   26002  1 
libahci                26861  1 ahci
xhci_hcd               82820  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
jme                    41301  0 

```

Is it safe to assume I've done it correctly?

---

### Post by wildmanne39 on 2011-12-26
Hi, there is no driver loaded for the nvidia card now so it is disabled, also I believe you can disable it by going into the bios.
Thanks

---

