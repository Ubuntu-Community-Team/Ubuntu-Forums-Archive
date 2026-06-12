---
title: "What distro would you recommend?"
date: 2010-07-06
forum: General Help
---

### Post by Mr_VeRiTy on 2010-07-06
Hi, I'm deciding on weather or not to switch distro, I like Ubuntu Lucid, but My wireless connection drops every 5 minutes. What distro would you recommend?

I use ubuntu for:
[LIST]
[*]Web surfing
[*]Watching movies
[*]Playing games on wine
[*]Audio and Video editing
[*]Listening To music
[*]Reading Ebooks
[*]Tons of other stuff
[/LIST]

I Like Gnome and don't like KDE so a distro that has gnome installed by default is preferred.

---

### Post by false_chicken on 2010-07-06
Have you tried to locate the problem with your wireless/post a question about it here?

---

### Post by Mr_VeRiTy on 2010-07-06
> **false_chicken said:**
> Have you tried to locate the problem with your wireless/post a question about it here?

yes but to no avail, it's something to do with the kernel, i think.

---

### Post by philinux on 2010-07-06
> **Mr_VeRiTy said:**
> yes but to no avail, it's something to do with the kernel, i think.

Try selecting an older kernel from grub.

---

### Post by Mr_VeRiTy on 2010-07-06
> **philinux said:**
> Try selecting an older kernel from grub.

hmmmn, the thought hadn't come to mind, will this affect anything else?

---

### Post by nothingspecial on 2010-07-06
> **Mr_VeRiTy said:**
> yes but to no avail, it's something to do with the kernel, i think.

You realise that all linux distros use the linux kernel (modified to some extent in some cases) and your problem may not go away by switching distros.

---

### Post by Mr_VeRiTy on 2010-07-06
> **nothingspecial said:**
> You realise that all linux distros use the linux kernel (modified to some extent in some cases) and your problem may not go away by switching distros.

Yes but surely not everyone using linux has a wireless problem and me and my brother (who uses ubuntu karmic) are the only people I know who has one.

---

### Post by nothingspecial on 2010-07-06
I don`t know what your problem is, and yes, I do not have a wireless problem in Ubuntu, Slackware or Puppy.

But if your wireless issue is related to the kernel, then I`m assuming it is to do with your specific card and the kernel module it uses. 

If the kernel module is buggy then switching distros may not help.

What is your card and problem?

---

### Post by Mr_VeRiTy on 2010-07-06
> **nothingspecial said:**
> I don`t know what your problem is, and yes, I do not have a wireless problem in Ubuntu, Slackware or Puppy.

But if your wireless issue is related to the kernel, then I`m assuming it is to do with your specific card and the kernel module it uses. 

If the kernel module is buggy then switching distros may not help.

What is your card and problem?
 Every 5-15 minutes my wireless connection drops to 50KB/s and in some cases just disconnects, my wireless card is (when i did "sudo lshw") "RTL8187SE Wireless LAN Controller" made by "Realtek Semiconductor Co., Ltd."

---

### Post by TroN-0074 on 2010-07-06
> **Mr_VeRiTy said:**
> Every 5-15 minutes my wireless connections drops to 50KB/s and in some cases just disconnects, my wireless card is (when i did "sudo lshw") "RTL8187SE Wireless LAN Controller" made by "Realtek Semiconductor Co., Ltd."

You can try a different Wireless manager, I believe there are more open sources software for wireless stuff

---

### Post by Mr_VeRiTy on 2010-07-06
> **TroN-0074 said:**
> You can try a different Wireless manager, I believe there are more open sources software for wireless stuff
Do you mean things like wcid?

---

### Post by philinux on 2010-07-06
> **Mr_VeRiTy said:**
> hmmmn, the thought hadn't come to mind, will this affect anything else?

Did the wireless drop out occur with the older kernel. If so don't bother.

You could try wicd instead of network-manager. It's easy to swap between the two by installing either. Installing one un-installs the other. 

A reboot is needed IIRC.

---

### Post by Mr_VeRiTy on 2010-07-06
> **philinux said:**
> Did the wireless drop out occur with the older kernel. If so don't bother.

You could try wicd instead of network-manager. It's easy to swap between the two by installing either. Installing one un-installs the other. 

A reboot is needed IIRC.
I was using a broadband dongle with karmic before lucid, the day I installed lucid was the same day my internet got activated so any kernel older than lucid I haven't used.
There are 4 or 5 kernels listed in grub two of which are pae mode which one do I choose (I dont remember what they were called)

---

### Post by nothingspecial on 2010-07-06
Having a dig, I can see a few problems with this card.

Try using ndiswrapper. See [COLOR=Red][here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")[/COLOR]

---

### Post by ankit singh on 2010-07-06
You go for a kernel update.It may be solved(it solves many issues of networking and audio)
Follow this steps
--------------------------------------------------------------------------------------------
Go to this websit [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
[SIZE=4]select the [/SIZE][COLOR=#000000][FONT=Times New Roman][SIZE=4][v2.6.34-lucid/]("http://ubuntuforums.org/v2.6.34-lucid/")[U] folder
[/U][/SIZE] [SIZE=4]and download these files(Note:If[/SIZE][/FONT][/COLOR][SIZE=4][COLOR=#ffffff][FONT=Times New Roman][COLOR=#000000][FONT=Lucida Grande]** you use the [COLOR=#bf0000]64 [/COLOR]- please download the files of the [COLOR=#bf0000]64 bit[/COLOR] and install them.S**[/FONT][/COLOR][/FONT][/COLOR][/SIZE][SIZE=4]imilarly for amd)[/SIZE]

> [COLOR=#ffffff][FONT=Times New Roman][COLOR=#000000][FONT=Lucida Grande][B]
[SIZE=3]linux-headers-2.6.34-020634_2.6.34-020634_all.deb[/SIZE]
[/B][/FONT][/COLOR][/FONT][/COLOR]**[SIZE=3][COLOR=#ffffff][FONT=Times New Roman][COLOR=#000000]linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb[/COLOR][/FONT][/COLOR][/SIZE]**
[SIZE=3][COLOR=#ffffff][FONT=Times New Roman][COLOR=#000000][FONT=Lucida Grande]**linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb**[/FONT][/COLOR][/FONT][/COLOR][/SIZE]After that instal this files in the very order i listed above just to make sure everything goes alright.After that reboot. Now u r running a ubuntu 2..6.34
If anything goes wrong u can boot through previous kernel in grub and uninstall these kernel via synaptic.
Hope this kernel update resolves ur networking issues

---

### Post by Mr_VeRiTy on 2010-07-06
> **nothingspecial said:**
> Having a dig, I can see a few problems with this card.

Try using ndiswrapper. See [COLOR=Red][here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")[/COLOR]
I looked [here]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Realtek_RTL8187SE") and It says that ndiswrapper worked perfectly with my card but, how do i disable the current driver and install the windows one with ndiswrapper (or whatever i'm meant to do)

---

### Post by ankit singh on 2010-07-06
Always have data back-up

---

### Post by Mr_VeRiTy on 2010-07-06
> **ankit singh said:**
> Sorry the reply i gave was for lucid.I thought u use lucid.
I do use lucid

---

### Post by ankit singh on 2010-07-06
> **Mr_VeRiTy said:**
> I do use lucid

I edited the post

---

### Post by nothingspecial on 2010-07-06
It`s all in the link.

To find which module is claiming your wireless type ```
lsmod
```

Then add that module to /etc/modprobe.d/blacklist.conf

Then use ndis-gtk to add the windows driver.

It`s in the link.

---

### Post by Mr_VeRiTy on 2010-07-06
I'm not sure what i'm looking at the output of lsmod was
```

Module                  Size  Used by
michael_mic             1732  4 
arc4                    1153  2 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_intelhdmi    11622  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203312  1 
snd_hda_intel          22037  1 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
joydev                  8708  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  285891  3 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29297  1 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   163034  4 i915,drm_kms_helper
psmouse                63245  0 
i2c_algo_bit            5028  1 i915
snd                    54148  16 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24415  2 i915
serio_raw               3978  0 
agpgart                31788  2 drm,intel_agp
video                  17375  1 i915
lp                      7028  0 
soundcore               6620  1 snd
output                  1871  1 video
rtl8187se             159947  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
nbd                     8335  0 
ahci                   32200  3 
r8169                  34300  0 
mii                     4381  1 r8169

```

---

### Post by Mr_VeRiTy on 2010-07-06
*Bump*

---

### Post by dnguyen1963 on 2010-07-06
I have been a long time user of Ubuntu (still am on some of my machines), but Lucid has been giving me too many problems.  My work machine is running PCLinuxOS/Xfce for a long time now without any problem.  I know many Linux users do not like PCLinuxOS for reasons that I do not comprehend, but it has been very stable for me.  Fedora 13 is another stable OS for me, but other users have reported problems similar to that of Lucid.  I have tried all of the top 20 distros (from distros.com) and PCLinuxOS/Fedora 13 are the only distros that gave me no trouble.  Good luck.

---

### Post by Mr_VeRiTy on 2010-07-06
> **dnguyen1963 said:**
> I have been a long time user of Ubuntu (still am on some of my machines), but Lucid has been giving me too many problems.  My work machine is running PCLinuxOS/Xfce for a long time now without any problem.  I know many Linux users do not like PCLinuxOS for reasons that I do not comprehend, but it has been very stable for me.  Fedora 13 is another stable OS for me, but other users have reported problems similar to that of Lucid.  I have tried all of the top 20 distros (from distros.com) and PCLinuxOS/Fedora 13 are the only distros that gave me no trouble.  Good luck.
Thanks but ndiswrapper seems to have fixed my connection problens :)

---

### Post by philinux on 2010-07-06
> **Mr_VeRiTy said:**
> Thanks but ndiswrapper seems to have fixed my connection problens :)

Just out of interest to anyone following this. Did you have to remove or disable the ubuntu driver?

---

### Post by Mr_VeRiTy on 2010-07-06
> **philinux said:**
> Just out of interest to anyone following this. Did you have to remove or disable the ubuntu driver?

no it used the windows xp one and has the ubuntu one as an alternate one

---

### Post by philinux on 2010-07-06
> **Mr_VeRiTy said:**
> no it used the windows xp one and has the ubuntu one as an alternate one

I might try this on GF's lappy which has a similar problem. 

Was it easy to use ndiswrapper?

---

### Post by Mr_VeRiTy on 2010-07-06
> **philinux said:**
> I might try this on GF's lappy which has a similar problem. 

Was it easy to use ndiswrapper?

yes all i had to was install ndisgtk download the driver and install it from within ndisgtk then do something about "loading module".  instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by cottfcfan on 2010-07-06
A bit off topic but i concur with dnguyen1963.
It appears that the 2.6.32 kernel has caused no end of niggly problems.
I started using Fedora 13 and its as stable as you can get (for me anyway). But it uses a later 2.6.33 kernel.
 Installing the later 2.6.34 kernel on Ubuntu 10.04 does seem to improve stability quite considerably.

---

### Post by oleink on 2010-07-06
> **Mr_VeRiTy said:**
> yes but to no avail, it's something to do with the kernel, i think.

First off that'll likely be a problem no matter which distro you are using.  It depends on your workarounds (which btw most workarounds will work in ubuntu so if you find a workaround that works it doesn't necessarily mean switching distros.)  2nd I'd like to ask how you are running the card now?  What driver and how are you running the driver (which software)??

---

### Post by nothingspecial on 2010-07-06
> **Mr_VeRiTy said:**
> *Bump*

Sorry, I had to get the kids from school, feed them, drop them at various evening activities........etc

Looks like you got it sorted anyway. Nice one. :D

---

