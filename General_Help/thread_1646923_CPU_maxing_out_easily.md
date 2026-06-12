---
title: "CPU maxing out easily"
date: 2010-12-16
forum: General Help
---

### Post by Sylos on 2010-12-16
Hello and thanks for looking.

I recently bought an old desktop off ebay to give to my dad with lubuntu installed on it. He doesnt do much - just the usual web browsing and storing photos - so i went with something reasonably old and cheap -  2.6ghz celeron (ugh I Know) emachine (again ugh, but I thought it would the job). I made the RAM up to 512Mb and installed lubuntu. 

Unfortunately when I installed flash the video was all jumpy when watching anything online. So I looked into the onboard graphics and found that there are driver issues with some of that series. So I bought a graphics card (NVIDIA Geforce 5500 128mb - PCI cos the lame MB doesnt have PCI -e or AGP).

Sadly the video is still jumpy and lame. I've tried it in firefox as well so this isnt a Chromium issue. The video is watchable if you download it and then play through VLC (which it wasnt before the NVIDIA card). Xfce4 Taskmanager shows CPU useage maxing when I use Chromium to watch flash but RAM staying around half used.

I know I've been a tool buying an emachine - particularly with a Celery processor and no AGP or PCI-e (ebay is a cruel mistress at times) but Im appealing for any help people might have to sort this out. Im hoping there might be something I can do.

Many Thanks

---

### Post by mmsmc on 2010-12-16
it sounds like you need more ram, 512mb is not alot, and seeing that it is an old comp, it may just be a "to old problem", we'll see what others say about it
when you run something check your system monitor and see how much ram it is useing, lus while there check for any thing else out of the ordinary

---

### Post by gradinaruvasile on 2010-12-16
Have you installed the proprietary nvidia drivers? They make a whole world of difference.
I had a MX-440 that worked well with Athlon XP 1800+ cpu with Ubuntu.

About flash cpu usage - flash is a cpu hungry being. On Linux it does not have any hardware decoding capabilities. It will eat cpu on any machine (i have Athlon II x2 @ 3.0GHz and i have high cpu usage, even 100% on some sites even on some low res clips).
It really depends on the flash webplayer from the web page how efficient is and the encoding of that clip. On Windows i think there is some hardware decoding but the same issue of the particular web player implementations remain.

But the proprietary drivers help a great deal - they make the jumpy flash playable.

Also make sure you have Adobe Flash Player not the default Gnash player that comes by default.

Edit: 512 RAM is sufficient for web browsing and lighter tasks. Just make sure you have swap.

---

### Post by Sylos on 2010-12-16
mmsmc - I thought RAM too but using the Xfce Taskmanager shows that the RAM is only half used and I have 1g SWAP to handle some overspill so I dont think its that.

 gradinaruvasile - I have installed the NVIDIA 173 series drivers from synaptic and have them running. The improvment has been minimal. The wierd thing is I have an older AMD Athlon with only 2ghz processor and an NVIDIA fx 5200 (256mb admittedly) and that has no probs - can multitask and play flash at the same time. Seems like I may have wasted my money here (the PCI NVIDIA card was expensive as there are few graphics cards available for pci interface these days.

Any other thoughts?

---

### Post by mmsmc on 2010-12-16
just a quick question, do you know how old the comp is?

---

### Post by no2498 on 2010-12-16
you can try this and set it back if it does not help
write down what you are going to change
a restart is needed to see if it helps
this comes from the program cheese
the only command line is  gstreamer-properties

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by gradinaruvasile on 2010-12-16
> **no2498 said:**
> you can try this and set it back if it does not help
write down what you are going to change
a restart is needed to see if it helps
this comes from the program cheese
the only command line is  gstreamer-properties

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.



The gstreamer-properties utility applies only to gstreamer based applications (totem, empathy etc). It does not apply to the flash player, vlc, mplayer etc. It is not a true system wide configurator.
Adobe flash does not use xv as far as i know and it has some hardcoded configuration.
Anyway, xv is not hardware decoding - it is true, it lowers cpu usage a bit because of the hardware-accelerated presentation, but the decoding is still done by the cpu. Only newer cards such as the 8xxx+ nvidias (maybe the 4xxx+ atis too) have true hardware decoding (VDPAU for nvidia).

Sylos, please check 2 things:

1. open a terminal and launch "nvidia-settings" in it. If it gives no errors and you can see the driver properties, the nvidia driver works. If the nvidia driver is not loaded, you will have an error message saying that the driver is not installed. In this case you have to run

sudo nvidia-xconfig

Install the nvidia-xconfig package if it isnt present.

2. Open Firefox (not Chromium) and type at the address bar:

about:plugins

To see the loaded plugins. Copy-paste its contents here (please use [CODE] tags around it if paste the whole output).

At least the first 2 lines of each plugin entry is suffice (the big bolded text and the following line).

---

### Post by Sylos on 2010-12-17
gradinaruvasile:

1. The nvidia 173.14.22 driver is installed and working ok - just checked again and no errors.

2. Firefox plugins:

```
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

I tried adding another 256mb of RAM (make up to 768ish) but that didnt help - RAM use stays low and CPU high from the flash plugin (around 70%). Video is almost watchable at small size but switching to full screen makes it 2 fps roughly.


cat /proc/cpuinfo shows: 

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Celeron(R) CPU 2.60GHz
stepping	: 9
cpu MHz		: 2591.561
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 5183.12
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

128KB cache sounds small (but I know very little about this).
Whats the stepping about - is that like a throttling thing?

Cheers

---

### Post by gradinaruvasile on 2010-12-17
Ok. What videos do you typically watch? (site/size).

Are you sure you dont have the default gnash plugin installed too?

post the output of

apt-cache policy mozilla-plugin-gnash

---

### Post by Sylos on 2010-12-17
As far as the files are concerned I have been using the same file on youtube each time (to ensure Im getting a reasonably accurate indication of improvement) but I have also tried some others as one offs. The video I have been using is a music video - around 4mins 30 long. Heres the link (if it makes a difference)

[http://www.youtube.com/watch?v=-jfon11JIRg](http://www.youtube.com/watch?v=-jfon11JIRg)

I havent really been using firefox - I usually use Chromium as it is the Lubuntu default and slightly less resource hungry. I installed firefox just to eliminate chromium as the source of the problem. The video was noticably worse in firefox.

Output of apt-cache policy mozilla-plugin-gnash:@

```
mozilla-plugin-gnash:
  Installed: (none)
  Candidate: 0.8.7-0ubuntu1
  Version table:
     0.8.7-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```

So not installed it would appear. Would gnash help?

Thanks for the help.

---

### Post by gradinaruvasile on 2010-12-17
Now that is interesting. That video is a low res youtube video that is the kind i was able to play perfectly well even on ati 9000 card + athlon XP 1800 CPU/Dell laptop with Pentium4 @1800MHz/Ati 7500.
And even better on an nvidia mx-440 card on the same desktop computer (the youtube normal res videos were playing perfectly). And this was with Ubuntu 8.10 gnome.
I also tested Debian Squeeze + LXDE (same DE lubuntu uses) with the radeon 9000 and videos were ok. 

So your cpu should be able to play videos like that with a nvdia card.
But i dont know about the PCI cards efficiency (all cards i used were AGP 4/8x). Maybe they require some special xorg.conf settings. Or your computers BIOS may have something that prevents the card functioning properly.

But the fact that the mobo does not have AGP and has Celeron based on Pentium 4 processor is kinda interesting.

Here:

Is an interesting post:

[http://ubuntuforums.org/showthread.php?t=33142](http://ubuntuforums.org/showthread.php?t=33142)

About setting up a PCI nvidia 5500. It is old, but it states that the "agpgart" and "intel_agp" modules should be blacklisted (probably because the card is initialized as agp). Maybe you should try blacklisting them.

Also in the xorg.conf the 

Option "NvAGP" "1"

option should be added.

gnash is a source of problems usually. But since you dont run gnome, it is probably not installed by default.

---

### Post by Sylos on 2010-12-17
Thanks for the info - I'l try some blacklisting tomorrow.

It does seem very odd that it is struggling so much with playing something so (relatively) small and low quality. The plugin is just taking up 60 -70% of the CPU and if you switch to full screen it cant cope.

That being said I have had some success in getting firefox to run a little better earlier today. I followed a guide on optimizin and turned off some form of GPU checking and that made it a lot more usable - even on full screen. It also recomends playing with DRI settings etc in Xorg.conf so I think I'll be attacking that tomorrow as well.

I really appreciate your help - this pc is a christmas present for my dad and if it cant do flash me and my linux fetish are gonna look very foolish.

EDIT: I should say I am quite shocked at how slow the overall performance of this machine is compared to my lower basic spec AMD Athlon rig that I've had since 2003 - slower cpu and same RAM gets better results - must be down to chipset and architecture. This is becoming a steep learning curve on PC hardware.

---

### Post by Sylos on 2010-12-18
Cant seem to blacklist the agp stuff as /etc/hotplug/blacklist does not exist anymore (apparently). Cant seem to find where the new equivalent is either.

And my previous statement about GPU validity checking being turned off helping - now appears wrong. Must have just had a good few minutes. LAME!

Also tried adding some DRI options into xorg.conf but that hasnt helped either.

The quest continues...

---

### Post by cascade9 on 2010-12-18
> **Sylos said:**
> EDIT: I should say I am quite shocked at how slow the overall performance of this machine is compared to my lower basic spec AMD Athlon rig that I've had since 2003 - slower cpu and same RAM gets better results - must be down to chipset and architecture. This is becoming a steep learning curve on PC hardware.

If you're comparing a 2.6GHz celery to a 2GHz Athlon, then I'm not shoched at all. The slowest 2GHz Athlon was a 2400+, and the 2600+ runs at 2GHz as well. Either of which will be noticably faster than a 2.6GHz celery, even if the celery is running a DDR motherbaord. If its using SD RAM then the difference will be even bigger.

I ran a Celeron 2.4GHz for a few days, and it was a lot slower than the AMDs of similar age and speed (mainly a 2200+ and a 2500+), so I noticed the same thing, its not just you. 

BTW, the 'XXXX+' on athlon XPs is in comparison to P4 models, on sempys its compared to celerys.

*edit- I only ran a few distros and winXP on the 2.4 Celery, but I was getting stupidly high CPU spikes idling. With windows as wel as linux distros. You might be able to get a new CPU, it makes a big difference (I went from 2.4GHz Celeron to a 2.53 P4 and the difference was instantly noticable).

---

### Post by Sylos on 2010-12-18
cascade9 - cheers for the post.

Do you think the 128kb cache size is part of the problem? I wonder if it cant keep up swapping info from RAM into CPU hence the low RAM use and max CPU - Im not sure _ I dont know enough about hardware

Methinks this may not be salvagable without changing the CPU as you say. Im not gonna do that because Im giving the rig to a man who only looks on the internet and does basic photo manipulation (cropping, B/W etc) - Its not worth sinking a load of cash into it becuase it will lie mostly unused. That doesnt stop this being irritating though.

I may have to face facts - I bought a turkey this christmas - Im a fool for thinking I could prop up an emachine to do limited tasks - the PC is pants and Im a halfwit for buyin it. Damn!

---

### Post by cascade9 on 2010-12-19
IMO its several things- the cache, the FSB and that the original P4s were really made for RD-RAM. The P4s were pretty much horrible untill they got a 512k cache and 533MHz FSB (really 133MHz x 4). It wasnt untill the 1MB+/800MHZ (200MHz) models that the P4s had some perfromance (***paed to AMD anyway). 

I dont know just what your motherboaard will take, but 512k/400MHz P4s (that should run just fine in any motherboard that will run a 2.6GHz celeron) in the 2.2-2.6 range ***monly go for $5-10 on ebay.

---

### Post by Sylos on 2010-12-20
Cheers for the advice - I have actually found an alternative solution - in the form of an alternative PC!

My girlfriend had this old tower she said was old and slow and useless - turns out it was made years ago by a proper geek! The guy put an Abit MB with an AMD XP 3000+ in it! It miturates all over the celeron - flash in full screen is no problem here. Actually Im kinda sad to give this thing away - the BIOS has all kinds of overclocking settings that I would love to have. The only problem is that on boot it keeps holding up posting some crap about RAID utility. Gotta figure out how to stop that.

Cheers for all the help.

---

### Post by cascade9 on 2010-12-20
Good luck with the system ;) 

BTW, I might be able to figure out whats with that RAID msg....what motherboard is it? (if you say NF7-S I'm going to laugh)

---

### Post by Sylos on 2010-12-20
Yeah man it is the NF7-S. Whats the deal with it?

---

### Post by cascade9 on 2010-12-20
LMAO. I used to own one, they are really nice, probably one of the best overclocking/underclocking socket 'a' motherboards (I think that the absolute best was some DFI but it was about 3 times the cost). ;)  

Its the SATA RAID initialising. If you arent using any SATA drives, you can turn it off in the BIOS.

---

### Post by Sylos on 2010-12-20
I thought it would be in the BIOS but I cant see any options that look likely. Any idea what it is under?

I am starting to think I may give my dad this temporarily and then swap it at a later date. The case is huge so I could give him a smaller one at some point and make out its for his benefit. Would that make me a bad person? Maybe. Probably. Maybe I should look into how much ebay has one of these beasts for.

---

### Post by cascade9 on 2010-12-20
I think its under Integrated Peripherals-> Onboard PCI device.

---

### Post by Sylos on 2011-01-16
UPDATE: I have given up on this issue for the moment as I decided to use a different MOBO and CPU for this project. However, another forum member has pointed something out that may be helpful to others suffering form this affliction.

So....

Adobe are releasing a beta of Flash 10.2 which comes with hardware acceleration - for Linux as well as windows for once! The only snag is it appears to only work for Nvidia cards as it is based on VDPAU which hasnt been adopted by intel or AMD. It can be downloaded from adobes site at the moment. It appears to suggest that you just need to uninstall the existing flash and then install the new version. Remember though - at the time I am writing this it is only BETA so could be twitchy. 

I havent tried this yet but I intend to when I next reinstall/upgrade.

Good luck to anyone trying this and huge thanks to lyovushka for bringing this to my attention.

---

