---
title: "please help with a very complex issue..."
date: 2011-01-21
forum: General Help
---

### Post by u-noob-tu on 2011-01-21
im posting here because my issue touches several different areas. today i bought a PC game called "world in conflict". i had read on wine hq that it works almost flawlessly so i installed it. no problems. when i launch the game, i get a warning about "no 3d hardware detected" and i get a black screen that goes away after 1 second to reveal my desktop. i guess its crashing. so i looked on wine hq and found that i needed to do a quick little fix that should have worked, but as you can guess it didnt. heres the link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9237]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9237"). i did a superhuman amount of digging through the internet looking for fixes of any kind, and found a lot of dead ends. some things i found were somewhat helpful. it seems that my graphics card is to blame, or more specifically, the driver. i discovered that if i have the open source driver for my graphics card (its a ATI Radeon Mobility 3650 265mb), then i will get weaker 3d graphics (which is probably why the game is crashing). BUT, i dont know if i have that driver or not as i can find no way of figuring that out. im inclined to think i do have it, because when i installed ubuntu i was only asked to install 2 additional drivers, and both were for my wireless. but that might not even be the problem, as i cant figure out exactly what is making the game crash on start up. so i did some more digging, and found this: [http://ubuntuforums.org/showthread.php?t=1273767&highlight=radeon+3650+drivers]("http://ubuntuforums.org/showthread.php?t=1273767&highlight=radeon+3650+drivers"). i looked over the steps until i saw something about configuring "xorg.conf". for some reason i decided to make sure i had that. good thing i did, because it didnt exist. after some MORE digging around and made a new one (so far as i can tell it looks okay). then i hit another snag. the guide says to go into /usr/share/ati directory. i dont have one. confused, i found that on some computers that have an ATI card also have another card that does most of the work (in my case, an intel card). i read that you could manually switch cards by using the bios. i tried but the option wasnt there. i had already downloaded the propriatery driver for my card from AMD (i havent done anything with it yet). i read that i have to remove the old driver before installing the new one, but i cant find the old one. its like i dug myself in a hole in the middle of a maze. i have no idea what to do next. help?

---

### Post by Timmer1240 on 2011-01-21
Go to administration hardware drivers and let it search your hardware to see what driver your using it may be possible to switch to a better driver for your card there.Good luck.

---

### Post by Timmer1240 on 2011-01-21
If you get the right driver installed I would get Play on linux installed and install the game through that and has a better chance of working for you.

---

### Post by u-noob-tu on 2011-01-22
> **Timmer1240 said:**
> Go to administration hardware drivers and let it search your hardware to see what driver your using it may be possible to switch to a better driver for your card there.Good luck.

I read that somewhere, but all I can find under administration is additional drivers. The hardware section doesn't have anything with drivers.

---

### Post by DOSIX on 2011-01-22
go to a terminal and type 
```

lsmod

```

reply with the output please.
this will list all the modules (drivers) compiled and working with your kernel.

---

### Post by Timmer1240 on 2011-01-22
[http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.14&lang=us&rev=10.4&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.14&lang=us&rev=10.4&ostype=Linux%20x86)

---

### Post by Timmer1240 on 2011-01-22
remember google is your friend!

---

### Post by u-noob-tu on 2011-01-22
heres the output: 


ryan@ryan-Studio-1737:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
vboxnetadp              6614  0 
vboxnetflt             18657  0 
vboxdrv               214831  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  1 
joydev                  8767  0 
snd_hda_intel          22107  4 
arc4                    1165  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
i915                  294989  5 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
uvcvideo               55847  0 
drm_kms_helper         30200  1 i915
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
drm                   168092  5 i915,drm_kms_helper
dell_wmi_aio            1733  0 
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   168681  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  1 b43
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                    9536  0 
dell_wmi                2852  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
dell_laptop             5730  0 
psmouse                59033  0 
cfg80211              144470  2 b43,mac80211
snd                    49038  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  1 dell_laptop
serio_raw               4022  0 
mtd                    18877  2 sm_common,nand
intel_agp              26694  2 i915
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19198  2 
firewire_ohci          21042  0 
tg3                   123310  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
libahci                21664  1 ahci
led_class               2633  2 b43,sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
ssb                    39288  1 b43

---

### Post by u-noob-tu on 2011-01-22
> **Timmer1240 said:**
> [http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.14&lang=us&rev=10.4&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.14&lang=us&rev=10.4&ostype=Linux%20x86)

so, i just run the install? is that it? i swear, if thats all i have to do and i did all that work for nothin... :D

---

### Post by DOSIX on 2011-01-22
try downloading and installing [this]("http://www.opendrivers.com/driver/248794/ati-radeon-hd-3600-hd-3650-hd-3670-driver-radeonhd-1.2-linux-free-download.html") driver.

---

### Post by DOSIX on 2011-01-22
but try his fix first.

---

### Post by Timmer1240 on 2011-01-22
Try em both its hard to know which one will work if mine doesnt help try Dosix's driver its hard to know unless you try!

---

### Post by endotherm on 2011-01-22
> **u-noob-tu said:**
> I read that somewhere, but all I can find under administration is additional drivers. The hardware section doesn't have anything with drivers.

just to clarify, do you have virtualbox installed in ubuntu, or is ubuntu running in virtualbox? if it is a vbox instance, then you have to install a vbox driver, which usually doesn't do good 3DA. vmware player is slightly better if that is the case. 

if it's a hardware install, for drivers, in Maverick the "Additional Drivers" utility is what you might be looking for. if you haven't checked it out, take a look. in prior versions of ubuntu the tool was called "Hardware Drivers" and before that, "Restricted Drivers". obviously there is controversy behind the naming...

for ATI drivers, I usually go to ATI.com and download theirs if I can't find a good one in the Additional drivers util. they download to you a .run file, so I just open a terminal and run 
```
cd /path/to/.run/directory/
sudo sh ./<filename>.run

```then just walk through the wizard. for some reason, their package always requires a new shell, hence the "sudo sh ..."
there is an ATI driver for your card at [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

as for xorg.conf, it is no longer very pertinent to a Maverick install. since 8.04 the xorg has been slowly losing relevance. they aren't used by default anymore, so if you don't have one, that is because no peice of software you have has tried to configure it for use. Nvidia vid cards for instance still store some of their settings in xorg.conf and will create one if it does not exist. you may have reason to create one, and it will be used if present, but if you have created and edited one, remember to delete it before trying a new type solution to your problem. it can cause problems if bad settings are left there. 

this really shouldn't be a messy issue. my best advice is to be sure to try all the easy approaches before getting more exotic. the developers spent a lot of time focusing on the easy methods, and the more complex stuff is subject to change on a much faster basis. I've learned (through pain) over the years, that when Ubuntu makes something easier in a new version, you are much better off taking the new path, instead of trying to do things the same way as your last version.

---

### Post by u-noob-tu on 2011-01-22
> **DOSIX said:**
> try downloading and installing [this]("http://www.opendrivers.com/driver/248794/ati-radeon-hd-3600-hd-3650-hd-3670-driver-radeonhd-1.2-linux-free-download.html") driver.

im getting an error during the compiling process when i run ./configure. it says that i have 2 missing packages: xorg-server and fontsproto. i looked in synaptic and couldnt find either.

---

### Post by u-noob-tu on 2011-01-22
how does the install process work? do i just go through the wizard, reboot and done?

---

### Post by endotherm on 2011-01-22
> **u-noob-tu said:**
> how does the install process work? do i just go through the wizard, reboot and done?
yup. the first option is to either install, or create a deb file. obviously, I would just install. 
you can choose a custom install which gives you two additional options, but I usually don't have to touch them. other than that, it does the rest. after that, you use the catalyst control center to configure it. for changes like resolution/refresh, screen position, and enabling extra monitors, be sure to run the "as admin" or "as root" launcher, since those changes do write to the xorg (or at least they used to), and require root to do it. for everything else however, run the tool as you, since you want your settings applied to your user.   

up to Lucid, I had to use the ati proprietary driver on lots of installs (largely HD 4200's) but now I find that the repository driver (in additional drivers) now has a fully functional driver for a lot more card models. 

I prefer the repository drivers because they automatically update/reinstall everytime you have a kernel or xorg update. the proprietary drivers become unlinked from the install every time the kernel is updated, and you have to rerun the installer wizard to recompile them for the new kernel and install the mods. 

that said, the proprietary driver works just fine if thats what you have to do. just put off your kernel updates until you have time to do a quick driver reinstallation.

---

### Post by u-noob-tu on 2011-01-22
this just wont end... i ran the sh command an i get this error in the terminal: 


$ sudo sh ./ati-driver-installer-10-12-x86.x86_64.run
Created directory fglrx-install.YPQDIO
Verifying archive integrity...Error in MD5 checksums: 48c2e8ce1f504f07a0985afe489b26e3 is different from dfc5d2753d97882b67eb453b85ff8dbc
 
what does that even mean?

aaaargh ](*,)

---

### Post by endotherm on 2011-01-22
oh, btw, the driver I linked above is 64bit. if you run a 32bit ubuntu, then jsut go to this page:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and fill the search with
```

Notebook graphics
Radeon Mobility
Mobility Radeon HD 3xxx Series
Linux x86

```

---

### Post by endotherm on 2011-01-22
> **u-noob-tu said:**
> this just wont end... i ran the sh command an i get this error in the terminal: 


$ sudo sh ./ati-driver-installer-10-12-x86.x86_64.run
Created directory fglrx-install.YPQDIO
Verifying archive integrity...Error in MD5 checksums: 48c2e8ce1f504f07a0985afe489b26e3 is different from dfc5d2753d97882b67eb453b85ff8dbc
 
what does that even mean?

aaaargh ](*,)

that means that the file did not download correctly. try downloading it again.

basically the checksum is calculated before the file is downloaded, and after. if the calculation returns a differant value than the one that was gen'ed before sending, then the package data changed somewhere. 
if your curious, check out: [https://secure.wikimedia.org/wikipedia/en/wiki/Simple_file_verification](https://secure.wikimedia.org/wikipedia/en/wiki/Simple_file_verification)

---

### Post by u-noob-tu on 2011-01-22
> **endotherm said:**
> that means that the file did not download correctly. try downloading it again.

basically the checksum is calculated before the file is downloaded, and after. if the calculation returns a differant value than the one that was gen'ed before sending, then the package data changed somewhere. 
if your curious, check out: [https://secure.wikimedia.org/wikipedia/en/wiki/Simple_file_verification](https://secure.wikimedia.org/wikipedia/en/wiki/Simple_file_verification)

i think i might have gotten that cuz you directed me to a 64 bit file, and i use 32 bit.

---

### Post by endotherm on 2011-01-22
> **u-noob-tu said:**
> i think i might have gotten that cuz you directed me to a 64 bit file, and i use 32 bit.
very possible. sorry bout that. I use 64bit almost exclusively...

---

### Post by u-noob-tu on 2011-01-22
> **endotherm said:**
> very possible. sorry bout that. I use 64bit almost exclusively...

no harm done :P

i tried that link you gave me and it actually gave me the same file (???). so now im trying the link DOSIX gave me. its a slightly older driver (10.4 vs 10.12), but hopefully itll work.

EDIT: youve got to be kidding me... now the terminal is telling me that sh cant open the file without telling me why.

EDIT 2: my bad, i was typing it wrong (missed a character). but im still getting the checksum error.

---

### Post by u-noob-tu on 2011-01-22
crap not good.... i finally was able to install the driver and thought everyhting was okay because i got no errors at bootup and i could see everything. i went to check the catalyst control center and i get a message saying that no driver is installed. so i put aticonfig in a terminal and got "no driver detected". i THINK its not working because i didnt uninstall the old driver (xserver-xorg something). it seems that the old one is still working but the mouse cursor is looking like its loading. there are instructions here  [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_Catalyst.2Ffglrx") on uninstalling, but im not sure i should do that since i already installed the new driver. this just will not end....

---

### Post by u-noob-tu on 2011-01-22
*BUMP* this is kinda urgent not sure what to do.

---

### Post by u-noob-tu on 2011-01-22
okay, i think i am very close! i managed to uninstall the new ati driver which i added without uninstalling the old driver with no trouble. everything is back to normal. but, im at a loss as to how im to uninstall the old driver and put the new one on. i found this link: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_Catalyst.2Ffglrx"),but this tutorial seems to be for compiling th driver from source, not an installer file. anyone have any suggestions?

---

### Post by DOSIX on 2011-01-22
that doesn't build anything from source. it says that if you downloaded and installed the drivers directly then you can skip the first command.

---

### Post by u-noob-tu on 2011-01-22
> **DOSIX said:**
> that doesn't build anything from source. it says that if you downloaded and installed the drivers directly then you can skip the first command.

okay, but the question about uninstalling still remains. the author gives this command: "$ sudo apt-get remove --purge xserver-xorg-video-radeon", is that what i need to do? and after that i run the install for the new driver?

EDIT: okay i got the install to work without a hitch, but when i run "aticonfigure" i get "no supported adapters detected" and i cant find a straight answer on how to fix it. also, my xorg.conf isnt detecting the new driver. this is what it says:

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"

it should say something like "fglrx" ive gotten this far! help me go all the way!

EDIT 2: okay, i might have figured out what the is causing the no supported adapters error. two days ago i made a "xorg.conf" file as a possible fix to installing this driver (obviously it didnt work). i think the issue is that since i have one aticonfig is unable to access or change it for some reason, though ive read that it should be able to. i might try deleting the xorg file and running aticonfig again. does anyone object and/or have suggestions?

---

### Post by endotherm on 2011-01-22
yes deleting the xorg will help.

if you ever want to default your ati driver configuration (reset it to shipped) run this command:
```
sudo aticonfig --initial
```[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

All I can advise is that you reread my posts on page 2. I think theres one or two you missed, probably because I was editing them at the same time you were reading.

definitely delete the old xorg. It will likely interfere with each new solution you try.

many folks reccomend using EnvyNG to remove ati proprietary drivers, and it may help you install the latest driver as well. Envy is a tool to install binary proprietary drivers from nvidia.com and ati.com, with a couple simple clicks. it;s less used nowadays because most people have few problems with the repository driver or the proprietary install, but if you are still having trouble, it is a good tool to try.

---

### Post by u-noob-tu on 2011-01-22
okay, ive followed all the instructions ive been given to a letter... but I STILL cant get aticonfig to run! it says there are no supported adapters, and the xorg.conf file isnt showing any available drivers in the "device" section. it just says "driver options are..." when i go into additional drivers there are no ati drivers listed. as far as i can tell, nothing went wrong with the install, i just cant use aticonfig. i have no idea what to do. i am so close to getting this working! ATI WHY DO YOU HAVE TO MAKE IT SO HARD?!?!?!?!

EDIT: I just keep hitting walls :( since I couldn't get ati config to work I went ahead and ran the uninstall script. I had read earlier that the fglrx driver could be found in synaptic. So I went there and found it, removed all the xserver-xorg packages and installed it. I also found the VESA driver and removed that too (I had read that it was the default low end driver). So I rebooted my system and got to the desktop, but it was slow loading and the mouse wait cursor was on the whole time. So I went to the catalyst control center and guess what?!? No supported adapters found! I am at my wits end!!! The funny part is, I'm probably going to figure out it was really easy and I just screwed it up... 

Does ANYONE have ANY ideas?!?!

EDIT 2: okay, i managed to get things back to normal. I have followed every tutorial i could possibly find. i dont want to give up and have wasted $15 on a good game (my laptop is the only computer in my house that could handle the game). any last suggestions?

---

### Post by DOSIX on 2011-01-23
to be honest with you, i remember my friend jorge (the one who turned me on to ubuntu way back in the days when 8.04 was the newest version) used ubuntu on a toshiba satelite with an ATI Radeon graphics card, and i remember he used to always tell me how they were such a pain because there never seemed to be perfect driver support for them. when he would use 3d accelerated graphics, his screen would flicker. my suggestion to you is that if you can't find the perfect fix, try to get as much of a fix as possible. my computer has motherboard graphics, so i can't really help you anymore than just telling you about drivers and modules. sorry. :-#

---

### Post by u-noob-tu on 2011-01-23
it might not be such a pain; i probably just made it a lot harder than it really is cuz im still a n00b. anyways, thanks for the help. i think i might have found the fix this time. i looked at the release notes for the driver and it listed several things i didnt have and created dependency issues (though, annoyingly, the installer told me it had worked anyway). it seems that i need XFree86-mesa-libgl and Xfree86-libs, but i havent a clue if i have them or where to get them if i dont. i couldnt find them in synaptic, so im kinda stuck again.

---

### Post by DOSIX on 2011-01-23
[This]("http://ubuntuforums.org/archive/index.php/t-206285.html") seems like it will help.

---

### Post by u-noob-tu on 2011-01-23
> **DOSIX said:**
> [This]("http://ubuntuforums.org/archive/index.php/t-206285.html") seems like it will help.

Yeah, actually I figured out the issue. Somehow I overlooked the fact that my computers radeon chip is the "discrete" graphics chip and the real graphics chip is actually an intel x3100. Looking into that now. Thanks for all the help though. I guess this is solved.

---

### Post by DOSIX on 2011-01-24
no problem.

---

