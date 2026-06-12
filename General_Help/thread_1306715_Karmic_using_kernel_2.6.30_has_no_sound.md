---
title: "Karmic using kernel 2.6.30 has no sound"
date: 2009-10-30
forum: General Help
---

### Post by DeMus on 2009-10-30
I just installed kernel 2.6.30 instead of the 2.6.31 which is standard for karmic. I had some issues with this kernel and wanted to see if the older one does not have those issues. Well, it turns out things run fine, except I have no sound.
In the preferences of my volume button in the top panel I see what is on the attached picture.
Anyone any idea how I can get a sound device again?

---

### Post by georgelenzer on 2009-10-30
First we need to make sure that ALSA modules loaded properly.

To find out is the ALSA modules are loaded, run this (If there is output, then the modules are loaded).  Paste the results back here:

```
aplay -l
```

If you don't get anything that indicates that you have an ALSA device, run this to find out what sound device you have, then paste the results back here:

```
lspci
```

---

### Post by DeMus on 2009-10-30
> **georgelenzer said:**
> First we need to make sure that ALSA modules loaded properly.

To find out is the ALSA modules are loaded, run this (If there is output, then the modules are loaded).  Paste the results back here:

```
aplay -l
```

If you don't get anything that indicates that you have an ALSA device, run this to find out what sound device you have, then paste the results back here:

```
lspci
```

Thanks for your help.
aplay -l tells me there is no soundcard found

lspci tells me this:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

---

### Post by georgelenzer on 2009-10-30
Is this a clean installation, or an upgrade?  If it's an upgrade, you may have some cruft left over in the ALSA configuration that is preventing sound modules from loading.

Also, based on your 'lspci' output, you should have the intel_hda ALSA module loaded.  Just to find out if the actual module is or isn't loaded (post results back here):

```
lsmod
```

You could also try this to see if the module will load manually.  (Post any errors you might get):

```
sudo modprobe snd_hda_intel
```

I have to leave for a few hours, but hopefully someone else will pick up with you.  I'll check back when I am back online later tonight (US EST).

---

### Post by philippe_carlo on 2009-10-30
> **DeMus said:**
> Thanks for your help.
aplay -l tells me there is no soundcard found

lspci tells me this:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

Taken from [http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)
try this:
```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

---

### Post by DeMus on 2009-10-30
> **georgelenzer said:**
> Is this a clean installation, or an upgrade?  If it's an upgrade, you may have some cruft left over in the ALSA configuration that is preventing sound modules from loading.

Also, based on your 'lspci' output, you should have the intel_hda ALSA module loaded.  Just to find out if the actual module is or isn't loaded (post results back here):

```
lsmod
```

You could also try this to see if the module will load manually.  (Post any errors you might get):

```
sudo modprobe snd_hda_intel
```

I have to leave for a few hours, but hopefully someone else will pick up with you.  I'll check back when I am back online later tonight (US EST).

@georgelenzer:
It is a clean install. I just installed the older kernel manually, and then in Synaptic I uninstalled the newer (standard Karmic) kernel because Grub2 does not let me choose at all. But that's another problem I have.

lsmod:
Module                  Size  Used by
binfmt_misc            10156  1 
snd_hda_codec_realtek   268068  1 
snd_hda_intel          32072  0 
snd_hda_codec          85408  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9128  1 snd_hda_codec
snd_pcm_oss            46528  0 
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                92456  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            32544  0 
snd_seq_midi            8000  0 
coretemp                7552  0 
snd_rawmidi            26048  1 snd_seq_midi
snd_seq_midi_event      8352  2 snd_seq_oss,snd_seq_midi
w83627ehf              25360  0 
hwmon_vid               3936  1 w83627ehf
iptable_filter          3104  0 
snd_seq                58464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26192  2 snd_pcm,snd_seq
snd_seq_device          8212  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              20528  1 iptable_filter
snd                    75016  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
x_tables               24328  1 ip_tables
snd_page_alloc         10736  2 snd_hda_intel,snd_pcm
nvidia               9619944  36 
lp                     11716  0 
parport                41968  1 lp
raid10                 23296  0 
raid456                54976  0 
raid6_pq               80672  1 raid456
async_xor               4128  1 raid456
async_memcpy            2464  1 raid456
async_tx                4064  3 raid456,async_xor,async_memcpy
xor                     5712  2 raid456,async_xor
raid1                  24064  0 
multipath               9060  0 
linear                  5636  0 
raid0                   7844  2 
floppy                 63272  0 
usbhid                 43424  0 
usb_storage            64704  0 
ohci1394               34644  0 
ieee1394              101664  1 ohci1394
atl1                   38312  0 
mii                     6016  1 atl1
intel_agp              31792  0 

sudo modprobe snd_hda_intel
finished very fast without any messages, warnings or errors.

@philippe_carlo
your codes installed a lot of things. Where on earth do you know all these things?

It finishes with:
You should now stop all applications using sound devices 
and reload all ALSA sound modules.
How do I reload all ALSA sound modules?

---

### Post by HardcoreSSG on 2009-10-30
I have the same problem, I want to try kernel 2.6.30 but I have no idea how to install it lol.

---

### Post by georgelenzer on 2009-10-30
OK.  From your output for lsmod, this is good.  It means that the module is loaded:

```
snd_hda_intel          32072  0 
```

I'm not familiar with module-assistant, but if it did what it seems like it did, that should have reinstalled or reloaded your ALSA modules.  The following:
[I]
It finishes with:
You should now stop all applications using sound devices 
and reload all ALSA sound modules.
How do I reload all ALSA sound modules?[/I]

To do this, follow these steps (might want to print these out or put them on another computer screen if you have another computer):

1. Press Ctrl-Alt-F1 to get to a virtual terminal (Your GUI will still be running, you're just at a different screen that is running outside of your GUI)
2. Log with your regular account
3. Stop the GUI (killing off any sound daemons that might be running or any other locked devices):

```
sudo /etc/init,d/gdm stop
```

4. Unload the currently loaded ALSA modules:

```
modprobe -r snd_hda_intel
```

5. Reload them:

```
modprobe snd_hda_intel
```

6. Restart the GUI:

```
sudo /etc/init.d/gdm start
```

After that, you can log in again.  Open a terminal and run aplay -l again to see if the sound device is there now or not.  If not, the next thing to do is get a little more specific...  But for now, let's see if the reload of the ALSA modules works.

---

### Post by DeMus on 2009-10-31
[QUOTE=georgelenzer;8200978]

```
sudo /etc/init.d/gdm stop
```

This does not work anymore. Just try it. There is text written with which I have no idea what to do next.
Somebody knows how to switch of the gdm?

---

### Post by georgelenzer on 2009-10-31
Did you get any errors?  If so can you post them here?

> **DeMus said:**
> [quote=georgelenzer;8200978]

```
sudo /etc/init.d/gdm stop
```This does not work anymore. Just try it. There is text written with which I have no idea what to do next.
Somebody knows how to switch of the gdm?

---

### Post by QIII on 2009-10-31
Karmic uses the new "service" syntax

```
sudo service gdm stop
```

---

### Post by michaelzap on 2009-10-31
I what may be the same problem on my Lenovo Y530 (no sound device reported in the Sound Control Panel, no sound input or output, and random crashes). I removed the proprietary driver for my internal modem (which it turns out is a sub-element of my sound card) and suddenly I had sound and the device is visible in the Sound Control Panel (and so far I've had no more crashes). It's too early for me to be sure that the issue is resolved, but I'm happy not to use my modem if my system will be stable and have sound.

---

### Post by DeMus on 2009-10-31
```
sudo /etc/init.d/gdm stop
```
Rather than invoking init scripts throuhg /etc/init.d, use the service(8 ) utility, e.g. service gdm stop

Since the script you are attemting to invoke has been converted to an Upstart job, you may also use the stop(8 ) utility, e.g. stop gdm


```
sudo service gdm stop
```
stop: unknown instance

---

### Post by georgelenzer on 2009-10-31
Try this:

```
stop gdm
```

---

### Post by DeMus on 2009-10-31
> **georgelenzer said:**
> Try this:

```
stop gdm
```

stop gdm
stop: unknown instance:

---

### Post by georgelenzer on 2009-10-31
Believe it or not, I think that worked.  You can tell by checking the process list:

```
ps ax | grep gdm | grep -v grep
```

If you don't get anything back, then your GUI is stopped.  Also check to make sure pulseaudio isn't running now that I think of it:

```
ps ax | grep pulseaudio | grep -v grep
```

---

### Post by DeMus on 2009-10-31
> **georgelenzer said:**
> Believe it or not, I think that worked.  You can tell by checking the process list:

```
ps ax | grep gdm | grep -v grep
```

If you don't get anything back, then your GUI is stopped.  Also check to make sure pulseaudio isn't running now that I think of it:

```
ps ax | grep pulseaudio | grep -v grep
```

gdm is still running, pulsaudio is not

---

### Post by DeMus on 2009-10-31
Thanks for all the help but I am returning to Jaunty. Karmic just has too many problems. In my opinion it is not finished yet and shouldn't have been brought out.

Signing off now and re-install Jaunty.

---

### Post by georgelenzer on 2009-10-31
Understandable.  The old saying... "if it ain't broke, don't fix it".  Karmic will become more stable with time.

---

### Post by DeMus on 2009-10-31
> **georgelenzer said:**
> Understandable.  The old saying... "if it ain't broke, don't fix it".  Karmic will become more stable with time.

Tell that to the people who made 9.10:
Kernel 2.6.31 has bugs that's wy I returned to 2.6.30 which is good.
Grub2 should never have been used. What's wrong with Grub1?

Sorry to have waisted so much of your time. Thanks for all your help.

---

### Post by QIII on 2009-10-31
I don't mean to sound gruff, because I understand your frustration, but...

We all had the opportunity to vent our frustrations an make the developers aware of issues with Karmic beginning with the release of the first Alpha.  It is better to help solve problems early than to stand by and criticize others' hard work only when the product rolls out.

Get involved in testing Lucid when the Alphas start to appear.

---

### Post by DeMus on 2009-10-31
> **QIII said:**
> I don't mean to sound gruff, because I understand your frustration, but...

We all had the opportunity to vent our frustrations an make the developers aware of issues with Karmic beginning with the release of the first Alpha.  It is better to help solve problems early than to stand by and criticize others' hard work only when the product rolls out.

Get involved in testing Lucid when the Alphas start to appear.

The problem is on my computer I have a program running 24/7 which I do not want to interrupt when fooling around with a new system.
I type this on an 9 year old laptop now of which I'm not sure it could handle a new system like Karmic or Lucid at all. I'm running DSL on it which makes it still "pretty fast".
I know very well programmers need input from the audience to make the product better. But as said I use the computer 24/7.

---

### Post by zingo on 2009-11-11
It seem to be a general problem when using 2.6.30 on 9.10 I have the same problem and I have seen one more forum post about it.

There seem to be some strange things that didn't happend in the /dev directory  I can see that my dvb cards has a flat structure like /dev/dvb0.demux0 and not the /dev/dvb/adapter0/demux0 that it should. The same migth just have happened for all device including sound, I don't know how the sound device shhould appeare in /dev...

---

### Post by zingo on 2009-11-13
Could it be some sort of udev problem?

---

### Post by zingo on 2009-11-17
Here is a solution
[http://ubuntuforums.org/showthread.php?t=1322019](http://ubuntuforums.org/showthread.php?t=1322019)

---

