---
title: "Driver enabled!.. not"
date: 2010-07-28
forum: General Help
---

### Post by jesseafrantz on 2010-07-28
EDIT:
So basically I installed Ubuntu 8.04LTS. I tried to enable my nVidia graphics driver. It's an on-board driver, and I am using a x64 bit system. Even though it says activated, it's really not. I am getting hit with this bug: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA%20driver%20activated%20but%20not%20currently%20in%20use%20in%20ubuntu%2010.04") except NOT for ubuntu 10.04 so the fix on that page WILL NOT work for my Ubuntu 8.0.4LTS system.

Any questions read all the pages, as I said this is an edit of the original.

---

### Post by dino99 on 2010-07-28
goto synaptic and reinstall nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

are you using Lucid ? if so, remove xorg.conf as kernel deal directly with X

sudo rm -f /etc/X11/xorg.conf

---

### Post by jesseafrantz on 2010-07-28
> **dino99 said:**
> goto synaptic and reinstall nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

are you using Lucid ? if so, remove xorg.conf as kernel deal directly with X

sudo rm -f /etc/X11/xorg.conf

I am still relatively new to Ubuntu well, synaptic for that matter, how do you reinstall it in Synaptic, I can't find the package in there for that matter

---

### Post by dino99 on 2010-07-28
- system admin synaptic: on top use the search field with "nvidia"

- then select each package one by one and right click on them to reinstall

---

### Post by cllewis91592 on 2010-07-28
well i was having some problems with mine as well,i was having the same problems and could not use desktop effects.then i looked inside my very old Compaq deskpro computer and saw a wire hanging down. i promptly looked at my video card and saw it was not plugged in. after i plugged it in all worked fine.i felt stupid after the fact but was happy it worked.check your card and make sure all wires are plugged in.



if thats not it then run > gksudo nvidia-settings > this will run nvidia-settings as root and allow you to save changes to the xorg file.quoted from fenian on this page [http://ubuntuforums.org/showthread.php?t=389636](http://ubuntuforums.org/showthread.php?t=389636)

---

### Post by jesseafrantz on 2010-07-28
> **cllewis91592 said:**
> well i was having some problems with mine as well,i was having the same problems and could not use desktop effects.then i looked inside my very old Compaq deskpro computer and saw a wire hanging down. i promptly looked at my video card and saw it was not plugged in. after i plugged it in all worked fine.i felt stupid after the fact but was happy it worked.check your card and make sure all wires are plugged in.



if thats not it then run  quoted from fenian on this page [http://ubuntuforums.org/showthread.php?t=389636](http://ubuntuforums.org/showthread.php?t=389636)

my vid card in on-board :X
and when I did those commands in terminal, I can't notice a change as if a window or something was supposed to come up.

---

### Post by jesseafrantz on 2010-07-28
> **jesseafrantz said:**
> my vid card in on-board :X
and when I did those commands in terminal, I can't notice a change as if a window or something was supposed to come up.
ALSO:
I have a 64-bit system
the ubuntu version is 8.04 LTS.

---

### Post by dino99 on 2010-07-28
[http://ubuntuforums.org/showpost.php?p=6533201&postcount=4](http://ubuntuforums.org/showpost.php?p=6533201&postcount=4)

---

### Post by jesseafrantz on 2010-07-28
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=6533201&postcount=4](http://ubuntuforums.org/showpost.php?p=6533201&postcount=4)
I did the thing in there but it said it was already installed "The Acutal Driver" part.

---

### Post by jesseafrantz on 2010-07-28
*bump*

---

### Post by jtarin on 2010-07-28
> **jesseafrantz said:**
> Originally Posted by jesseafrantz  
my vid card in on-board :X
and when I did those commands in terminal, I can't notice a change as if a window or something was supposed to come up.your results from the command in a terminal ```
lspci
```this will allow us to see your video card type.

---

### Post by jesseafrantz on 2010-07-28
results from the above thread:
jesse@jesse-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control



ALSO(again) an img:
[IMG]http://i37.servimg.com/u/f37/12/67/73/25/screen10.jpg[/IMG]

---

### Post by interval1066 on 2010-07-28
Might want to do a dmesg | grep nVidia and see what that log says.

---

### Post by jesseafrantz on 2010-07-28
> **interval1066 said:**
> Might want to do a dmesg | grep nVidia and see what that log says.
it didn't bring up anything.

---

### Post by jtarin on 2010-07-28
Ok now issue the command ```
lsmod
```and post

---

### Post by jtarin on 2010-07-28
[Have you followed this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> [Have you followed this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
I have, but it's not working for me because again, I am using Ubuntu 8.0.4.x LTS

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> Ok now issue the command ```
lsmod
```and post


lsmod command in terminal:

jesse@jesse-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  268036  8 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41872  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         346264  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
evdev                  13056  3 
snd_seq_dummy           4868  0 
psmouse                40336  0 
serio_raw               7940  0 
snd_seq_oss            35584  0 
pcspkr                  4224  0 
wmi_acer                9644  0 
nvidia               7825536  24 
button                  9232  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  1 nvidia
i2c_nforce2             7680  0 
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  2 nvidia,i2c_nforce2
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ext3                  136968  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
usbhid                 32128  1 
usb_storage            74432  0 
hid                    38784  1 usbhid
libusual               20772  1 usb_storage
pata_amd               14212  0 
sata_nv                27656  2 
ata_generic             8324  0 
forcedeth              51980  0 
libata                159728  4 pata_acpi,pata_amd,sata_nv,ata_generic
ehci_hcd               37900  0 
ohci_hcd               26640  0 
scsi_mod              151692  5 sg,sd_mod,sr_mod,usb_storage,libata
usbcore               146412  7 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36616  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by jtarin on 2010-07-28
[Then I can assume you found this guide also?]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> [Then I can assume you found this guide also?]("https://help.ubuntu.com/community/NvidiaManual")
I can't figure out how to do it properly, and it looks really risky seeing as it even ask you to make a backup, is there any more safer ways?

plus "This is not the recommended way to install the driver" right on the page.



and even so, again I have 8.0.4 LTS

---

### Post by jesseafrantz on 2010-07-28
If your just now reading this thread from page 3, please read all of 1 and 2

---

### Post by jtarin on 2010-07-28
> **jesseafrantz said:**
> I can't figure out how to do it properly, and it looks really risky seeing as it even ask you to make a backup, is there any more safer ways?

plus "This is not the recommended way to install the driver" right on the page.



and even so, again I have 8.0.4 LTS[Well there is this.]("https://help.ubuntu.com/community/NvidiaManual")

> "This is not the recommended way to install the driver"This was the only way to install nvidia at one time. I can remember having to rebuild my kernel just to get it working sometimes.:p

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> [Well there is this.]("https://help.ubuntu.com/community/NvidiaManual")

This was the only way to install nvidia at one time. I can remember having to rebuild my kernel just to get it working sometimes.:p
well that sucks :\
plus: I also said I am sorta a noob at all this still, so I was really hoping for a more simple way

---

### Post by jtarin on 2010-07-28
> **jesseafrantz said:**
> well that sucks :\
plus: I also said I am sorta a noob at all this still, so I was really hoping for a more simple way
Yea! and I was a hotshot veteran then.....NOT! I agree it sucked big time, but it was a very good learning experience for me....there was no Ubuntu.You couldn't do it in a GUI, it all had to be done without X.It was worth it though as all we had up until then were S3 cards and the like. You had to configure xorg during install. I took about 20-30 minutes of configuration to get it going......if you were lucky.....and well practiced....well practiced as in installed it about 20-30 times.:D I think I could do it in my sleep this day.

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> Yea! and I was a hotshot veteran then.....NOT! I agree it sucked big time, but it was a very good learning experience for me....there was no Ubuntu.You couldn't do it in a GUI, it all had to be done without X.It was worth it though as all we had up until then were S3 cards and the like. You had to configure xorg during install. I took about 20-30 minutes of configuration to get it going......if you were lucky.....and well practiced....well practiced as in installed it about 20-30 times.:D I think I could do it in my sleep this day.
to bad they don't make Team-Viewer, or LogMeIn for linux I was ask someone to do it for me, I know it's a chance to enrich my knowledge on X and for that matter commands and the general file structure of unix-like systems but this is outrageous for me, and I have been using linux for 2/3 years so all the X stuff was pretty much just there and splash screens and menus did all the fancy work, you should see me try to install Gentoo now that was the very defintion of hot-mess I think I blew up the harddisk on that one xD but for now, thanks for your help I guess I will try to follow that guide and get my driver working since, before I using wubi but I erased my windows lol so I really wanna get the driver working or I may be in a world of trouble later. X_X


Scratch the they don't make team viewer for linux, I just found out they did :O

---

### Post by kh1116 on 2010-07-28
why dont you use 10.04 or xubuntu 10.04 if your computer doesn't meet specs. it seems like its fixed in new builds.

you could also try envy: [https://help.ubuntu.com/community/NvidiaManual#Installation with Envy/EnvyNG](https://help.ubuntu.com/community/NvidiaManual#Installation with Envy/EnvyNG)

---

### Post by jesseafrantz on 2010-07-28
> **kh1116 said:**
> why dont you use 10.04 or xubuntu 10.04 if your computer doesn't meet specs. it seems like its fixed in new builds.

you could also try envy: [https://help.ubuntu.com/community/NvidiaManual#Installation with Envy/EnvyNG]("https://help.ubuntu.com/community/NvidiaManual#Installation%20with%20Envy/EnvyNG")

Well, to be more specific about my problem, and which I really should have mentioned a lot earlier is I downloaded, a distro called gOS which uses ubuntu, there are SOME diffrences but I checked it looked at the repos and all the main files and it's identical to ubuntu. Even on the GRUB boot loader for the boot-up it says "Ubuntu 8.04.4LTS". They do not have a forum so I came here. Hoping to my driver working.

I know this sounds ludicrous but it's really REALLY like identical you should see it for your self you can barley tell it's a diffrent distro, aside from the fact it comes with google-gadgets and such.

---

### Post by jtarin on 2010-07-28
> **kh1116 said:**
> why dont you use 10.04 or xubuntu 10.04 if your computer doesn't meet specs. it seems like its fixed in new builds.

you could also try envy: [https://help.ubuntu.com/community/NvidiaManual#Installation with Envy/EnvyNG](https://help.ubuntu.com/community/NvidiaManual#Installation with Envy/EnvyNG)
I gave that link a few post ago.

---

### Post by jesseafrantz on 2010-07-28
> **jtarin said:**
> I gave that link a few post ago.
yeah, he did lol
> **jesseafrantz said:**
> If your just now reading this thread from page 3, please read all of 1 and 2

---

### Post by jesseafrantz on 2010-07-28
OKAY! 
after thinking it over I finally did that tut, how-ever I have ran into an error it told me to edit a file, and in that file I was supposed to edit something. I have an img here that will explain it all.

[IMG]http://i37.servimg.com/u/f37/12/67/73/25/screen10.png[/IMG]
As you can see in the IMG it tell's me to edit DRI under module, but there is only one listing under module and at that not even the right one! so now I am just very lost and confused!!! any one help me ? D:

---

### Post by jtarin on 2010-07-28
> Find the section "Module" and comment out DRI using the.....
If you don't have it you don't need to comment it out. To comment something out means to eliminate it from running. Xorg used to use "#" at the beginning of a line to stop something from loading or running. It was meant to be functional in that if your commenting out something didn't work you could go back and uncomment it.Your good t go at that stage. Nothing to do....move on.

---

### Post by jesseafrantz on 2010-07-29
Now I have a new problem, when it tells me to shut down my GDM it does shut down, but there is no shell-prompt while GDM is off? I tried doing a few comands but it was like it was just a text editor, there was no shell, none at all?

---

### Post by jesseafrantz on 2010-07-29
bump

---

### Post by jesseafrantz on 2010-07-29
Never mind I got the driver installed, BUT WTF EFFECTS ARE STILL NOT WORKING D:

---

### Post by jtarin on 2010-07-29
Good that you got it somewhat working.
What effects?

---

### Post by jesseafrantz on 2010-07-29
> **jtarin said:**
> Good that you got it somewhat working.
What effects?
Hello again, read here: [http://ubuntuforums.org/showthread.php?p=9652451#post9652451](http://ubuntuforums.org/showthread.php?p=9652451#post9652451)

---

### Post by kh1116 on 2010-07-29
again, why don't you use 10.04

---

