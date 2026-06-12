---
title: "Possible memory leak in kernel? How to debug?"
date: 2012-02-28
forum: General Help
---

### Post by 7bit on 2012-02-28
Hi,

I have recently updated my old Thinkpad T40 from Hardy to Oneiric (in several steps) and I also switched from Kubuntu to Xubuntu (with compiz). This machine has only 500MB Ram, so every MB counts. After cleaning up a lot of mess that has accumulated over the years (this machine has seen versions as old as Feisty and never was updated via fresh CD install because it has no functioning CD-ROM drive).

Now after booting into the xfce session It uses only a little more than 100MB RAM (without buffers and cache) which is Ok. This goes well for a few hours but then slowly the memory becomes used up to a point where it becomes essentially unusable. And now comes the strange thing: If I exit the xfce session, stop the display manager, stop most services so that only a very minimal system is left then the memory usage still does not go away. This is the output of htop after stopping almost everything:

htop after 3 hours work
[ATTACH]213423[/ATTACH]

At this time the following kernel modules are loaded:

```

Module                  Size  Used by
lib80211_crypt_ccmp    12789  2 
dm_crypt               22565  0 
joydev                 17393  0 
ppdev                  12849  0 
arc4                   12473  2 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
pcmcia                 39822  0 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
snd_rawmidi            25241  1 snd_seq_midi
rt2x00usb              20092  1 rt73usb
rt2x00lib              48146  2 rt73usb,rt2x00usb
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              393421  2 rt2x00usb,rt2x00lib
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcsp               14315  0 
ipw2100                77886  0 
snd_intel8x0           33318  0 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
libipw                 46701  1 ipw2100
lib80211               14570  2 lib80211_crypt_ccmp,libipw
snd_pcm                80435  3 snd_pcsp,snd_intel8x0,snd_ac97_codec
cfg80211              172427  4 rt2x00lib,ipw2100,mac80211,libipw
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
snd_timer              28932  2 snd_seq,snd_pcm
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
snd                    55902  9 thinkpad_acpi,snd_rawmidi,snd_pcsp,snd_intel8x0,snd_ac97_codec,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              12600  1 snd
binfmt_misc            17292  1 
nvram                  14029  1 thinkpad_acpi
nsc_ircc               23240  0 
parport_pc             32114  1 
shpchp                 32356  0 
ircomm_tty             37816  0 
ircomm                 24924  1 ircomm_tty
irda                  185428  3 nsc_ircc,ircomm_tty,ircomm
crc_ccitt              12595  1 irda
psmouse                73673  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
async_raid6_recov      12906  0 
async_pq               12959  1 async_raid6_recov
raid6_pq               88205  2 async_raid6_recov,async_pq
async_xor              12738  2 async_raid6_recov,async_pq
xor                    21860  1 async_xor
async_memcpy           12481  1 async_raid6_recov
async_tx               13123  4 async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  26291  0 
raid0                  17067  0 
multipath              12977  0 
linear                 12792  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
radeon                929507  1 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192194  3 radeon,ttm,drm_kms_helper
e1000                 101773  0 
i2c_algo_bit           13199  1 radeon
video                  18908  0 

```Now I manually unloaded all modules one after the other until it would not allow me anymore and these modules were left:

```

Module                  Size  Used by
binfmt_misc            17292  1 
radeon                929507  1 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192194  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon

```and htop output did not change much:

htop after unloading all modules
[ATTACH]213424[/ATTACH]

Then I rebooted and immediately logged out of xfce without doing any work and again stopped everything I could possible stop and made another htop and this time it looks as I would expect it:

htop after fresh boot
[ATTACH]213425[/ATTACH]

now the question is how do I proceed from here? How do I find out what exactly has eaten 100MB during 3 hours? Are there any tools I can use to further track down the cause of this? I have now switched from compiz back to xfwm4 and try to use this for a few days to see if it still happens.

Is it possible that the radeon driver is eating all the memory? is it possible that a userland application like compiz can cause this to happen? Is it normal that I cannot unload the radeon driver although no X server is running anymore? Or could this have been any of the other kernel modules and unloading them one after the other would not help me find the offending one?

Bernd

_________
PS: In case anybody is wondering how I got the output of htop from the text console without X into a running x termnial to make a screenshot: htop > out.txt and after a second press q. This will dump a stream of totally unreadable escape sequences into the text file but with cat in an xterm you can make them readable again. This does not seem to work in all terminals but on the text console (Ctrl+Alt+F1) it works.

PPS: I have chosen the prefix "all variants" instead of "xubuntu" because I suspect a bug in the kernel or the base system itself, none of the xubuntu or xfce specific parts seem to be the cause.

---

### Post by 7bit on 2012-03-02
It seems to happen whenever I use any OpenGL programs. Kernel memory will grow and never shrink. The same happens in the Natty kernel, unfortunately I don't have any other older kernels to test.

Where should I file a bug report and what additional information will be needed?

---

### Post by Khayyam on 2012-03-02
7bit ...

I can see no cause for alarm, the "use" of memory does not mean that this memory won't be freed if something should need it. You should read the [Linux Memory Management Wiki](http://linux-mm.org/Low_On_Memory) for some idea of how Linux manages memory, as it says "a page of free RAM is wasted RAM".

If your machine it becoming unresponsive then there may be some other issue involved (other than the kernels memory management). It may be a "[memory leak](http://en.wikipedia.org/wiki/Memory_leak) but this too would be "freed" if the application is quit. I assume you've never recieved an OOM (out of memory)?

Normally unresponsiveness is caused by CPU usage, but from the info you provided it looks like your well below the level of CPU usage where you would experience noticable lag.

So, "how to debug" ... I'm not sure, you might look in /proc/slabinfo and see if anything in particular is using a large portion of memory:

```
awk '{printf "%5d MB %s\n", $3*$4/(1024*1024), $1}' < /proc/slabinfo | sort -n
```

... but this may be a wild goose chase, I imagine that the problem lies somewhere other than the kernel.

It might be any number of things ... but I'm fairly sure its not the kernels MM.

best ... khay

---

### Post by 7bit on 2012-03-02
I have now produced a simple test that reliably demonstrates the problem on my machine.

0. use a machine that has a Radeon Mobility M7 LW [Radeon Mobility 7500]
    For example the good old IBM ThinkPad T40, maybe similar ATI graphic cards will do also
0.1 Use the open source radeon driver.

1. reboot (to have a reproducible starting point)
2. log in to a session that is using the compiz window manager
3. run this script:

```

#!/bin/sh

while : ; do
        /usr/bin/xclock &
        sleep 0.5
        killall xclock
done

```4. lean back and have a cup of coffee while you are watching (with htop) all RAM being used up and then slowly all your swap.

After waiting half an hour it had used all RAM plus 1GB (two thirds) of my swap. *None* of the processes (xorg, compiz, etc.) is showing any sign of increased numbers in RSS but it started swapping more than 1GB! The computer was totally unusable after this experiment and additionally while trying to log out and stop the display manager some kind of strange accident/crash happened that didn't even let me use the text console (Ctrl+F1) anymore. Normally when exiting X all this consumed memory does *not* go away. I can do a service lightdm stop and then htop and all RAM is still used and I'm not talking about buffers and caches here, I really mean htop's green bar, the allocated memory. Caches and Buffers cannot force other things into the swap, can they? And surely not 1GB in an empty XFCE session where X is the largest process with 40MB.

---

### Post by QIII on 2012-03-02
Not likely a memory leak in the kernel proper, or it would be all over the forum and launchpad.  A      module is possible.

I can have Kubuntu (pretty heavy) running for days, messing around with stuff, running BOINC continuously with ATI projects tapping multiple cards and not have the memory use get higher than roughly 2GB.  But what you have going on there is definitely a problem.

With an old GPU and the open source driver you may have found a fault there.

Have you gotten this on launchpad?  Definitely worth a look.

Edit:  just checked in on the machine that I use most heavily for BOINC.  Uptime is 36 hours.  DE is KDE.  Memory is sitting hard at 1.23GB.  I think you really need to report what you have there with all the detail you can muster.

---

### Post by Khayyam on 2012-03-02
Well no, all your test shows is that there is a problem somewhere (hardware, software, memory management, the radeon framebuffer driver, any number of things). What does /proc/slabinfo show (see above) ... what does 'slabtop' show? Does 'sync' have any effect on memory reported (it'll slow things down as all the pages are sysnc'd)? Have you run memtest? What is the 'S.M.A.R.T status' on your hardisk?

best ... khay

---

### Post by 7bit on 2012-03-03
Ok, I'm making some progress. The memory usage goes away if I stop compiz and drop the caches but the drop_caches will **ONLY** have an effect if the old compiz instance has been stopped (or replaced by a new one)

```

#!/bin/sh

echo "restarting compiz"
killall -9 gtk-window-decorator
killall -9 compiz # compiz will restart itself on SIGKILL

gksudo sysctl vm.drop_caches=3

```

I have put myself a panic button onto the desktop that will execute the above script. 

The strange things here which I don't understand are:

[LIST]
[*]why does the memory usage of compiz (if I assume that it really is compiz' fault) not show up anywhere in ps, top, htop, the reported memory figures (VIRT, RES, SHR) for the compiz process (and also all the other processes all remain constantly normal and low), but the system keeps stuffing gigabytes into the swap file with no indication where they might come from
[*]htop has 3 indicators: used, buffers and cache and unlike top it is showing what I really want to know: used := total-(free+buffers+cache), so it excludes buffers and cache from this number. What kind of memory is it that can be released by drop_caches and that is *not* included in cache or buffers?
[*]slabtop does not show any significant things, total amount never exceeded 16M and does not change much. I also tried ipcs -m but there is also no increase in shared memory segments.
[/LIST]
Has anybody already reproduced my problem with the script I posted yesterday? The script is simply opening and closing an xclock window rapidly. Any other small application that can start and stop in less than 0.5 seconds will also do if you don't have xclock installed. The most important thing is you need to do it when compiz is running. It will not leak any memory when doing it with metacity or xfwm4 or openbox, it only happens with compiz. The same effect also happens when rapidly moving the mouse through a menu bar back and forth many times, rapidly opening and closing menus, but this is cumbersome, therefore I wrote this little script. please try it, let it run half an hour while running htop in a second terminal and watch the green bar (used memory excl. caches+buffers) and eventually swap once all RAM is full with green, maybe someone can confirm my problem.

---

### Post by Khayyam on 2012-03-03
> **7bit said:**
> [...]The strange things here which I don't understand are:

[LIST]
[*]why does the memory usage of compiz (if I assume that it really is compiz' fault) not show up anywhere in ps, top, htop, the reported memory figures (VIRT, RES, SHR) for the compiz process (and also all the other processes all remain constantly normal and low) [..]
[/LIST]
I assume as compiz is using the video cards memory, if there is a problem then the effect may be somewhat obfusticated.

> **7bit said:**
> [...]

[LIST]
[*] what I really want to know: used := total-(free+buffers+cache), so it excludes buffers and cache from this number. What kind of memory is it that can be released by drop_caches and that is *not* included in cache or buffers?
[/LIST]
"cashes" .. as the name suggests.

> **7bit said:**
> [...]
[LIST]
[*]slabtop does not show any significant things, total amount never exceeded 16M and does not change much. I also tried ipcs -m but there is also no increase in shared memory segments.
[/LIST]
Again, I assume that this is due to the fact that the cards mem is used. I'm suprised it doesn't show up as being used by radeonfb, but there is quite possibly some veil drawn over the transfer of I/O from the driver to MM.

Anyhow, the above is mostly speculation. I'm not sure how you'd go about troubleshooting it other than perhaps trying to rule out if its the card itself.

HTH ... khay

---

### Post by 7bit on 2012-03-15
It seems it is caused by the close animation in compiz. If I disable all close animations it stops leaking. I noticed a huge linear increase in window handles in xrestop that would not go away until I kill compiz and the decoration manager (it doesn't matter which one I use, I tried gtk-window-decorator and unity-window-decorator, I didn't try the kde decorator because I want to avoid all the KDE stuff)

Every opening and closing of a desktop window will leak 3 handles for compiz and 19 handles for gtk-window-decorator and somehow this leak seems to be able to consume memory while not easily visible to which process it actually belongs.

I have filed a bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/954117](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/954117)

I still hope someone can replicate it and tell me that I am not crazy for trying to run a computer with less than a few dozen GB of RAM ;-) and I hope it can be fixed and will not continue to exist in the next ubuntu version.

---

