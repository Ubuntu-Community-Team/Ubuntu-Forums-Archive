---
title: "asus 1215n ion 2 support"
date: 2010-10-10
forum: General Help
---

### Post by snizzo92 on 2010-10-10
Hello all!

Is there a way to use my nvidia chip in my eee pc 1215n?

It has an integrated graphic card and a discrete card (nvidia). I don't care about battery but I'd just want to use nvidia chip.

Is there a way?

Thanks in advance.

---

### Post by TheBrinos on 2010-10-14
I'm having the opposite problem. I'd love to be able to switch over to the less powerful graphics card so my battery doesn't get drained. I've partitioned the harddrive, and on the windows side I get about 6 hours of battery. On the Ubuntu side (even with the update to 10.10) I get 3 hours. I'm pretty certain it's the more advanced graphics card. I'd like to be able to switch that off so I can save battery.

---

### Post by ovis23 on 2010-10-17
The hybrid-graphics-linux folks have had some luck with experimentally switching off the nVidia graphics with acpi calls.

[http://www.mail-archive.com/hybrid-graphics-linux@lists.launchpad.net/msg00235.html](http://www.mail-archive.com/hybrid-graphics-linux@lists.launchpad.net/msg00235.html)

I don't have this computer and haven't tried it myself.

---

### Post by Tryfon on 2010-11-16
I don't get it. Does the ion chip work even without the proprietary nVidia drivers enabled?

For now I have them disabled after reading in posts that they screw up the system. Intel integrated graphics works fine. Has anybody tried enabling the nVidia drivers with any success?

---

### Post by thisnameagain on 2010-11-20
I made the mistake of installing the nvidia driver and got the black screen problem. I ended up having to reinstall the OS because I could not find another way to get my screen back. This is unfortunate, since the onboard video card is not that good.

---

### Post by SeijiSensei on 2010-11-20
I read somewhere, perhaps on the hybrid-graphics-linux site, that it was possible to turn off VGA switching in the BIOS on some machines; I don't know if the 1215n is one of them, though.

I'm so glad I bought my daughter the 1201n so we don't have to deal with this stupid crap.  I've been a big Nvidia supporter over the years, but after they've decided to leave Linux users high-and-dry in this generation, I'm not sure I'll continue to be in their corner.

---

### Post by Tryfon on 2010-12-18
I just noticed that NVidia released new display drivers for Linux 32bit on 2010.12.13 and they supposedly support all the ION series. Has anybody tried installing them? Any luck?

---

### Post by emoguitarist06 on 2011-02-02
> **Tryfon said:**
> I just noticed that NVidia released new display drivers for Linux 32bit on 2010.12.13 and they supposedly support all the ION series. Has anybody tried installing them? Any luck?

BUMP I'd like to know too before I buy the Asus VX6

---

### Post by arsenalrule on 2011-02-02
I've been looking around the internet for a solution to this, but it seems to have been quiet in 2011.
Just had a look at the nvidia drivers site, and there was a driver release on the 21st Jan:
[http://www.nvidia.co.uk/object/linux-display-ia32-260.19.36-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.36-driver-uk.html)
 
I'm at work at the moment so cant test it on my laptop till later/tomorrow.
I assume that if this breaks the computer, you just boot into ubuntu (recovery) to remove it? (linux noob here)

---

### Post by link141 on 2011-02-02
My Compaq Presario f756nr recently crapped out due to the (at least somewhat) infamous HP GPU over-heating problem (just google "hp gpu overheating").  I read that HP's recommended fix is for you, the customer, to pay over 400 dollars to buy a new motherboard.  For this reason, I'm in the market for a new laptop.

I'm just a relatively poor college student that wants a decently portable laptop, so I am strongly considering buying an ASUS eee pc 1215N.  However, after a few hours of searching online, it looks like the ION2 chip does not work at all in Linux. Is this true? Or does anyone know if this laptop can be forced into discrete graphics mode.  It looks like the ION2 itself may work with Linux, but it is unclear if it will work at all in this specific laptop due to the NV Optimus crap.  I'm also unsure of how much of the Linux "hybrid-graphics" switching applies to this setup.

This would really suck if NVidia is just giving us Linux users the cold shoulder.  I could always use the integrated Intel graphics, but then I'm not getting what I've paid for.  Furthermore, it's sad if the only reason this setup exists is because of political issues between Intel and NVidia.

Oh well, maybe I'll have to go with a different laptop/netbook.
 
Just my two cents

Edit:
[Link to an 'official' thread on some NV forum.](http://www.nvnews.net/vbulletin/showthread.php?t=144750)  As you can see, the response from Linux users has been overwhelmingly negative.

It is now clear that ION2 will work with Linux ONLY if optimus isn't used in the hardware. The last official statement from an NVidia employee, which was last February, states that NVidia is not planning to add optimus support for Linux [(link here)](http://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477).  There has been absolutely no other feedback from NVidia since then stating whether they plan to add this support.

What's frustrating is that the actual GPUs that are affected by this are supported well by the proprietary NVidia driver, but the Optimus setup prevents them from accessing/using the card in the normal way (that and the discrete GPU depends on the Intel GPU for certain fundamental functions).  It seems that our only hope for working ION2 graphics on Optimus notebooks lies in someone reverse engineering open source drivers.

Edit 2:
Apparently, work is being done to get this setup to work with the open source NVidia drivers:
[Hybrid-graphics-linux project page](https://launchpad.net/~hybrid-graphics-linux)
Scroll down to find a link to the NVidia+Intel+Optimus setup progress.

---

### Post by capleton on 2011-02-06
I was thinking about getting a 1215n as well, but I'm shying away because of the nvidia issue now. 

[quote=Arch Wiki]nVidia Optimus is basically a software configuration that utilizes an Intel IGP + an nVidia GPU that writes to the Intel IGP's framebuffer. This is all done on the software side. The nVidia GPU is not wired to the outputs (VGA, HDMI etc.) [/quote]

I doubt that nvidia has the software developers to dedicate toward creating something like optimus for linux.  Also, I kind of feel bad for nvidia.  When the first Ion netbooks came out, they got rave reviews, but were invariably cited as having short battery life.  Which, if you ask me, is kind of understandable for a dedicated video card on a netbook, no?  Anyway, I think Optimus was an attempt to appease those consumers that want unreasonable performance, and the cost is simplicity and cross-platform support :mad:

Anyway, I have faith in the Linux Community, and i don't doubt that a fix will happen relatively soon.

Also check this out:  [http://linux-hybrid-graphics.blogspot.com/2010/03/google-summer-of-code-2010-open-source.html](http://linux-hybrid-graphics.blogspot.com/2010/03/google-summer-of-code-2010-open-source.html)

---

### Post by link141 on 2011-02-08
You might want to hold out for just another Month as ASUS is releasing the eee pc 1215B sometime in March.  It uses a dual-core AMD/ATI solution for its processor/gpu, and the two are integrated onto one chip.  Unlike the 1215N, it only has one GPU -- so it would be like the ion 2 integrated onto the intel chip in the 1215n.  Apparently, the Radeon in this new model is actually very slightly better than the ION2 in the 1215N, and the processor is supposed to be much more powerful than the atom D525 in the 1215N.  You should also be able to get up to the full 4GB of memory with the new model as this was apparently a problem with the intel chipset.

Hopefully, the proprietary ATI drivers should support linux for the new model.  If not, I have a strong feeling that support will come to this Radeon GPU faster than Optimus comes to linux.

EDIT: It looks like the latest proprietary ATI drivers work with this specific GPU in this configuration.

---

### Post by pads on 2011-02-13
there is an argument that 1215 works well with only intel graphics (nvidia switched off for good). but still, better avoid this model if you want your linux experience not to be spoiled. 
1201n is far more better with linux, than 1215 with win7 and linux i suppose.

---

### Post by klwinters on 2011-03-27
I got a 1215n a while ago and I was finally getting around to putting my beloved Ubuntu on it, and then I stumbled upon this problem. Intel's integrated graphics has always been pretty awful so I hate to see the Nvidia chip go, but I'm at my wits end with Windows.

I'm lost to what to do.

---

### Post by ratson on 2011-04-05
could someone give an update on the current status? 
is it possible to use the nvidia chip in ubuntu?
any new from official nvidia sources if they ever will support ion2 in linux drivers?

---

### Post by beew on 2011-04-05
> **TheBrinos said:**
> I'm having the opposite problem. I'd love to be able to switch over to the less powerful graphics card so my battery doesn't get drained. I've partitioned the harddrive, and on the windows side I get about 6 hours of battery. On the Ubuntu side (even with the update to 10.10) I get 3 hours. I'm pretty certain it's the more advanced graphics card. I'd like to be able to switch that off so I can save battery.

No, it is not the Nvidia card that you're using, it is the less powerful Intel card. Here is the real travesty. If you use Linux with Optimus, not only that you cannot use the Nvidia card (the more powerful one), it will nevertheless generate heat and drain your battery so it is worse than an expensive paper weight. At least a paper weight doesn't do anything.

---

### Post by beew on 2011-04-05
> **ratson said:**
> could someone give an update on the current status? 
is it possible to use the nvidia chip in ubuntu?
any new from official nvidia sources if they ever will support ion2 in linux drivers?

Unfortunately no if the laptop is Optimus enabled. It doesn't matter if Nvidia has the driver. The driver would not work in the Optimus environment because the Nvidia chip has been turned into a hybrid when Optimus is enabled.

Take sometimes to write to Nvidia. This is very bad because most new laptops with Nvidia cards are shipped with Optimus these days, that means effectively Nvidia no longer supports Linux laptops.

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

---

### Post by f03el on 2011-05-29
Check out the Bumblebee project which aims at adding Optimus support for Linux: [https://github.com/MrMEEE/bumblebee]("https://github.com/MrMEEE/bumblebee")

I tried it in my Asus 1215N and now it seems like I can disable the NVIDIA graphics. For the first time the fan occasionally spins down completely. However, I'm not sure that the switching between the cards is fully working for me yet.

---

### Post by DrJohn999 on 2011-06-01
Bumblebee works for me on ASUS 1215N in Ubuntu 11.04. I installed from the tarball download at [https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee). For some reason 'git clone ...' failed to download.

After installation, copy the appropriate 'bumblebee-enablecard.xxxx and bumblebee-disablecard.xxxx from /usr/share/doc/bumblebee to /usr/local/bin. For the 1215n (as root):
```
cp /usr/share/doc/bumblebee/bumblebee-disablecard.1215n /usr/local/bin/bumblebee-disablecard
cp /usr/share/doc/bumblebee/bumblebee-enablecard.1215n /usr/local/bin/bumblebee-enablecard
```

Disable/Enable scripts do just that for the nVidia Otimus. The optirun app will enable the Optimus if not already enabled, run the specified program, and then disable the Optimus when the program exits. So far I've only tried it with glxgears (tests basic frame rates):

```
optirun glxgears
```

Here are some stats with no graphics running to the Optimus (the Natty desktop is handled by the Intel chip)

```
nVidia Optimus     Enabled                  Disabled
glxgears frame rate      200+                     60
Core0 temp                49 °C                   38 °C
Core1 temp                42 °C                   33 °C
Acpitz temp               62 °C                   57 °C
Est Battery Time           3:20                    5:40
```

Running glxgears on the Optimus increases all the temps by about 5 °C.

Battery time when disabled is comparable to Win 7 estimates (the 1215n is dual-booted).

After plugging/unplugging the AC power, for some as yet unknown reason the nVidia driver can no longer be found:
```
root@eee-1215N:/# bumblebee-enablecard
_PS0 Enabling nVidia Card Succeded.
P3MO Enabling nVidia Card Succeded.
DGPS Enabling nVidia Card Succeded.
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-8-generic/updates/dkms/nvidia-current.ko): No such device
root@eee-1215N:/# 
```

Reboot doesn't make any difference. More later...

-- DrJohn

---

### Post by DrJohn999 on 2011-06-24
Solved. Installed latest bumblebee build and made one change in /etc/X11/xorg.conf.nvidia: in Section "Device" change

```
Option    "ConnectedMonitor" CRT-0"
```
to 
```
Option    "ConnectedMonitor" DFP-0"
```
Run bumblebee-disablecard first to default the nVidia to off.
Now optirun <program name> works quite well. The nVidia output appears on the laptop screen, and the nVidia is turned off when the application terminates.
Simultaneous display on a monitor connected to the VGA port works only in the "Classic Ubuntu" mode. With Unity the sync frequency is screwed up and the result is a lot of colored hash. Perhaps there is some tweaking that could be done to one of the xorg conf files.
The HDMI output turns on but just sends a blank black screen. If you need this then Bumblebee is not for you at the moment.

---

### Post by AbeFM on 2011-07-22
> **DrJohn999 said:**
> Solved. Installed latest bumblebee build and made one change in /etc/X11/xorg.conf.nvidia: in Section "Device" change....
The HDMI output turns on but just sends a blank black screen. If you need this then Bumblebee is not for you at the moment.

WOW! Thanks for all the good work!

What's interesting - my netbook has ALWAYS had the HDMI port working, so I assume the ION2 has been on? Certainly it plays 1080p without an issue (although there's tearing, a v-sync looking issue, under VLC).

But battery life has sucked. So I'll give this a shot.

Do you have any pointers on how to make HDMI work well? I'd like sound-and-video to switch at once. Right now it requires switching each independently and some other tricks. It's a 3 minute process to do what plugging a cable would do on windows.

---

### Post by AbeFM on 2011-07-22
Uh, oh. While I didn't have to make the CRT-0 change, things aren't working!


abe@Netbuntu:~$ sudo /usr/local/bin/bumblebee-disablecard
ERROR: Module nvidia is in use
Error: could not unload nvidia module, leaving card turned on



Any ideas?

---

