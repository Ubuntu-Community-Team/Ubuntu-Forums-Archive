---
title: "Hibernation / Supsend Fails in Lucid Lynx 10.04"
date: 2010-06-13
forum: General Help
---

### Post by gozo311 on 2010-06-13
I have 12Gb of ram, a 24Gb swap partition (which appears active in the system monitor).  When trying to hibernate, the screen turns off for 5 seconds, then immediately awakens and brings me to the login screen.

Here is my /var/log/pm-suspend.log :

```

Initial commandline parameters:
Sun Jun 13 11:28:30 PDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux ubuntu-beast 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
fglrx                2353422  0
nls_utf8                1421  1
hfsplus                77769  0
isofs                  33399  1
binfmt_misc             7960  1
ppdev                   6375  0
snd_hda_codec_atihdmi     3023  1
snd_hda_codec_realtek   278890  1
snd_hda_intel          25645  2
snd_pcm_oss            41394  0
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87850  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1782  0
snd_seq_oss            31219  0
snd_seq_midi            5829  0
snd_rawmidi            23388  1 snd_seq_midi
nls_iso8859_1           4633  0
arc4                    1473  2
fbcon                  39270  71
nls_cp437               6351  0
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
rt61pci                21414  0
crc_itu_t               1715  1 rt61pci
rt2x00pci               6905  1 rt61pci
rt2x00lib              32133  2 rt61pci,rt2x00pci
bitblit                 5811  1 fbcon
led_class               3732  1 rt2x00lib
softcursor              1565  1 bitblit
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              238128  2 rt2x00pci,rt2x00lib
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              148386  2 rt2x00lib,mac80211
vga16fb                12757  1
psmouse                64608  0
vfat                   10802  0
fat                    55350  1 vfat
usblp                  12407  0
xhci                   40958  0
soundcore               8052  1 snd
eeprom_93cx6            1765  1 rt61pci
vgastate                9857  1 vga16fb
serio_raw               4918  0
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
asus_atk0110           10033  0
lp                      9336  0
parport                37160  2 ppdev,lp
usbhid                 40988  0
hid                    83376  1 usbhid
ohci1394               30260  0
usb_storage            49833  0
ieee1394               94675  1 ohci1394
sky2                   48803  0
             total       used       free     shared    buffers     cached
Mem:      12323964    1745900   10578064          0      14208     108044
-/+ buffers/cache:    1623648   10700316
Swap:     25848576     159060   25689516
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance:
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sun Jun 13 11:28:33 PDT 2010: performing hibernate
Sun Jun 13 11:28:37 PDT 2010: Awake.
Sun Jun 13 11:28:37 PDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sun Jun 13 11:28:59 PDT 2010: Finished.

```

I have an ASUS P6X58D Premium motherboard and an Intel i7 CPU.

I also tried setting up a swap file [COLOR="Blue"][as so]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/")[/COLOR].  That resulted in the same behavior.  Here is my current /etc/fstab (with a swap partition setup during a Lucid re-install):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=802752f5-597f-4686-8cb1-8726cfc30ae6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=22fbd8df-1aa7-4dee-840f-ac63b8ee47b8 none            swap    sw              0       0

```

Any help is appreciated.  Thanks.

---

### Post by techunit on 2010-06-13
First of all I want you to know with that much ram the most swap your going to need is about 2 GB and thats going pretty far. I assume that you have the ati or nvidia restricted drivers these can cause problems. I also would like to point out that suspending and hibernation are not really designed for a desktop environment. 

The ATI and NVIDIA drivers can cause problems with suspend and hibernate.

ATI drivers can cause problems where the system wont respond from standby and hibernate will return you immediately to the unlock screen

For The NVIDIA drivers I don't know.

---

### Post by gozo311 on 2010-06-13
Thanks techunit.  Very helpful info.
Yeah, I initially had no swap because I have to try REALLY hard to need it with this much RAM.  However, I really like to hibernate my PC at night, so I made a huge swap partition to see if it would work.  I suppose it won't.  It's only about 15 cents a night for the kWh's, but that adds up, and isn't very "green" of me...[-X  I guess I'll have to power down more in Ubuntu.  Or use Windows 7 more, where hibernation works perfectly.

And yes, I have an ATI Radeon graphics card.  My 'lspci | grep ATI' :
```

03:00.0 VGA compatible controller: ATI Technologies Inc Device 68d9
03:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]

```

You called it.

---

### Post by efflandt on 2010-06-13
Does suspend work (suspend does not use swap).

The data included shows **fglrx** proprietary ATI module.  I am not sure if that has issues, but I do know that in order to get suspend and hibernate to work (and help sluggish video) with default radeon module for my older ATI X1300, I had to disable kernel modesetting (kms) driver with **nomodeset** kernel boot parameter.  That is worth a shot.  But if tested by editing grub from its menu, you may also have to enter that when waking from hibernate.

For a different computer with nVidia I had to blacklist the intel_agp module used and enable NvAGP in xorg.conf instead, but I do not see any agp modules posted (and none are used for my radeon).

To hibernate you do need at least as much swap as you have RAM, and it has to be a swap "partition", not swap "file" unless you do something special.  I know that in the distant past there was a limit to usable swap file size, but not sure if there is still a limit.  An old swap mini HOWTO said "2.4.x and 2.5.x kernels support swap spaces of up to 64 GiB in size" and we are on 2.6.x.

---

### Post by gozo311 on 2010-06-13
Thanks for the response.  Suspend does not work.  It just takes me to a log in screen.

I also tried adding "nomodeset" to GRUB_CMDLINE_LINUX in the /etc/default/grub file - then ran 'sudo update-grub'.  That didn't seem to fix anything.  Is that what you meant I should try?

Yeah, no AGP here.  Guess I'll have to keep poking at it.  I'm going to try [this driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English"): 

Good idea or no?

---

### Post by pegranka on 2010-06-26
I have just succeeded in getting suspend to work on my HP nx6125 laptop. It worked fine with kubuntu 8.04, but I could not resume once I upgraded to 10.04.
I have a HP nx6125, which has a Radeon XPRESS 200M video card.

If I ran "sudo s2ram -n" I saw that I could not suspend when using a framebuffer (NOFB). lsmod showed 2 framebuffer drivers - vga16fb and fbcon.
I disabled the first by adding it to /etc/modprobe.d/blacklist-framebuffer.conf
I could then suspend if I booted in recovery mode (no X, and hence no radeon or fbcon drivers).
Whenever the radeon driver loaded, it also loaded fbcon. To prevent this I had to disable KMS, which I did by:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
After this I can now suspend and resume because fbcon is not loaded when the radeon driver loads.

You could check if your machine is listed in /usr/lib/pm-utils/video-quirks, and see what the problem may be.

---

### Post by rasp1331 on 2010-07-19
Thanks pegranka, your suggestion worked perfectly. I've got an Acer Aspire 5024 laptop.

---

### Post by hugo_koopmans on 2010-07-19
HI I have a Sony Vaio SZ61 which now won't suspend anymore after upgrade to Lucid.

When I had Karmic 9.10 running , I could suspend and not hybernate...

now I cannot do suspend, which is anoying... I will try suggestion here if I can find the time today

hugo

---

### Post by hugo_koopmans on 2010-07-19
so i have an SZ61 which has the following quirks:
  addquirk --quirk-s3-bios
  addquirk --quirk-s3-mode

in /usr/lib/pm-utils/video-quirks

so what does that tell me?

---

### Post by acs236 on 2010-07-19
Similar problem here, and I've tried all the "fixes" I have found on this forum (and elsewhere) to no avail.  I'm pretty sure the issue stems from the nvidia driverse that I'm using.  Mine will go into suspend mode, but when I try to make it up, I get a blank screen with a cursor, and can't do anything.  It's pretty frustrating, and I have to say I've been booting into Windows 7 more frequently.

---

### Post by hugo_koopmans on 2010-07-19
when trying sudo s2ram -n i get:

Machine unknown
This machine can be identified by:
    sys_vendor   = "Sony Corporation"
    sys_product  = "VGN-SZ61XN_C"
    sys_version  = "J002W9XN"
    bios_version = "R0122S5"
See [http://suspend.sf.net/s2ram-support.html](http://suspend.sf.net/s2ram-support.html) for details.

If you report a problem, please include the complete output above.

so I just tried s2ram -f which gave me a terminal login but no keyboard

....

---

### Post by pegranka on 2010-07-19
hugo_koopmans - as your machine is in the quirks database, these quirks should be automatically used if you run s2ram. If s2ram fails, try s2ram -f. Also try without X running, and read /usr/share/doc/uswsusp/README.s2ram-whitelist.gz for possible further hints. Also look at /var/log/pm-suspend.log.

---

### Post by anjames on 2010-08-28
> **pegranka said:**
> I have just succeeded in getting suspend to work on my HP nx6125 laptop. It worked fine with kubuntu 8.04, but I could not resume once I upgraded to 10.04.
I have a HP nx6125, which has a Radeon XPRESS 200M video card.

If I ran "sudo s2ram -n" I saw that I could not suspend when using a framebuffer (NOFB). lsmod showed 2 framebuffer drivers - vga16fb and fbcon.
I disabled the first by adding it to /etc/modprobe.d/blacklist-framebuffer.conf
I could then suspend if I booted in recovery mode (no X, and hence no radeon or fbcon drivers).
Whenever the radeon driver loaded, it also loaded fbcon. To prevent this I had to disable KMS, which I did by:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
After this I can now suspend and resume because fbcon is not loaded when the radeon driver loads.

You could check if your machine is listed in /usr/lib/pm-utils/video-quirks, and see what the problem may be.

My laptop is a Toshiba Portege M200 with an NVIDIA Go card, which is not listed in the video-quirks listed above. Since upgrade to Lucid, the screen goes all garbled (ie bad mode) when I hibernate (s2disk, which used to work). Once or twice it resumed, but now it seems to regularly resume to a garbled screen and freeze entirely. I tried passing nomodeset in grub but I get similar garbling when I do that.

For some reason both vesafb AND fbcon are loaded, even though vesafb appears in the blacklist:
```
$ grep vesafb /etc/modprobe.d/blacklist-framebuffer.conf
blacklist vesafb

```

Also, is it strange to have intel_agp loaded since I don't have an intel graphics card?

Previously X used the nv graphics driver, but now that doesn't load, despite the explicit driver line in the Device section of xorg.conf:
```
$ grep nv /etc/X11/xorg.conf
	Driver	"nv"
$ lsmod | grep nv
$

```

All these drivers where I don't seem to need them, and where I explicitly blacklist them, and where I explicitly request them in configs seems a bit strange.

I have the following modules loaded:
```
$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
dm_crypt               11331  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
ath5k                 121792  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
mac80211              205146  1 ath5k
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8708  0 
snd_timer              19098  2 snd_pcm,snd_seq
ath                     7611  1 ath5k
pcmcia                 33024  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
yenta_socket           20408  1 
btusb                  10925  2 
rsrc_nonstatic         10015  1 yenta_socket
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
lp                      7028  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
parport                32635  2 ppdev,lp
toshiba_acpi            8662  0 
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
vesafb                  3542  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nouveau               467048  1 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
drm                   162409  3 nouveau,ttm,drm_kms_helper
intel_agp              24119  1 
video                  17375  0 
e100                   28211  0 
mii                     4381  1 e100
i2c_algo_bit            5028  1 nouveau
output                  1871  1 video
agpgart                31724  3 ttm,drm,intel_agp

```

I've always stayed away from the proprietary nvidia drivers since they mess up hibernation. How do I get my suspend back? :confused:

---

### Post by anjames on 2010-08-28
The vesafb autoloading appears to be an error in initramfs-tools:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/87158?comments=all](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/87158?comments=all)

---

### Post by anjames on 2010-08-30
Update: It occurred to me that the reason I was still hibernatable just after upgrade was that I hadn't rebooted into the new kernel:

```
title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root		(hd0,1)
#kernel		/vmlinuz-2.6.32-24-generic root=UUID=22578c46-436c-4302-b1cd-bba53d865367 ro vga=795 resume=/dev/hda5 verbose
kernel		/vmlinuz-2.6.32-24-generic root=UUID=22578c46-436c-4302-b1cd-bba53d865367 ro resume=/dev/hda5 verbose
initrd		/initrd.img-2.6.32-24-generic

```

It was using the above kernel which apparently caused my hibernation problems, perhaps due to the fact that it loads vesafb instead of nvidiafb as my older kernel does:

```
$ uname -a
Linux amaterasu 2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686 GNU/Linux
$ lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
dm_crypt               12928  0 
arc4                    1660  2 
ecb                     2524  2 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
pcmcia                 36808  0 
snd_intel8x0m          13896  0 
snd_intel8x0           30168  2 
ath5k                 124772  0 
mac80211              181140  1 ath5k
led_class               4096  1 ath5k
yenta_socket           24296  1 
ath                     8060  1 ath5k
snd_ac97_codec        101216  2 snd_intel8x0m,snd_intel8x0
rsrc_nonstatic         11644  1 yenta_socket
iTCO_wdt               10944  0 
ac97_bus                1532  1 snd_ac97_codec
btusb                  11856  2 
joydev                 10240  0 
pcmcia_core            36592  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               93052  3 ath5k,mac80211,ath
snd_pcm                75296  3 snd_intel8x0m,snd_intel8x0,snd_ac97_codec
snd_timer              22276  1 snd_pcm
pcspkr                  2332  0 
nvidiafb               42812  1 
fb_ddc                  2076  1 nvidiafb
iTCO_vendor_support     3456  1 iTCO_wdt
i2c_algo_bit            5760  1 nvidiafb
vgastate                9628  1 nvidiafb
lp                      8964  0 
snd                    59204  9 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
intel_agp              27676  1 
soundcore               7264  1 snd
shpchp                 32272  0 
parport                35340  2 ppdev,lp
agpgart                34988  1 intel_agp
video                  19380  0 
psmouse                57332  0 
toshiba_acpi           10744  0 
serio_raw               5280  0 
snd_page_alloc          9156  3 snd_intel8x0m,snd_intel8x0,snd_pcm
output                  2780  1 video
dm_raid45              84228  0 
e100                   32292  0 
mii                     5212  1 e100
xor                    15620  1 dm_raid45

```

Anyway, it's fixed for now by reverting to the old kernel 2.6.31-22, which again seems to have a slightly different module setup, especially lack of the vesafb forced autoloading in the newer kernel. For anyone interested, the differences in loaded kernels are listed below:

```
$ diff -y mods_2.6.31-22_sort mods_2.6.32-24_sort
ac97_bus             						ac97_bus             
aes_generic          					      <
aes_i586             					      <
agpgart              						agpgart              
arc4                 						arc4                 
ath                  						ath                  
ath5k                						ath5k                
binfmt_misc          						binfmt_misc          
bitblit              						bitblit              
							      >	bluetooth            
bnep                 						bnep                 
bridge               						bridge               
btusb                						btusb                
cfg80211             						cfg80211             
dm_crypt             						dm_crypt             
dm_raid45            						dm_raid45            
							      >	drm                  
							      >	drm_kms_helper       
e100                 						e100                 
ecb                  					      <
fbcon                						fbcon                
fb_ddc               					      <
font                 						font                 
i2c_algo_bit         						i2c_algo_bit         
intel_agp            						intel_agp            
iTCO_vendor_support  					      <
iTCO_wdt             					      <
joydev               						joydev               
							      >	l2cap                
led_class            						led_class            
lp                   						lp                   
mac80211             						mac80211             
mii                  						mii                  
nvidiafb             					      |	nouveau              
output               						output               
parport              						parport              
pcmcia               						pcmcia               
pcmcia_core          						pcmcia_core          
pcspkr               					      <
ppdev                						ppdev                
psmouse              						psmouse              
							      >	rfcomm               
rsrc_nonstatic       						rsrc_nonstatic       
							      >	sco                  
serio_raw            						serio_raw            
shpchp               						shpchp               
snd                  						snd                  
snd_ac97_codec       						snd_ac97_codec       
snd_intel8x0         						snd_intel8x0         
snd_intel8x0m        					      |	snd_mixer_oss        
snd_page_alloc       						snd_page_alloc       
snd_pcm              						snd_pcm              
							      >	snd_pcm_oss          
							      >	snd_rawmidi          
							      >	snd_seq              
							      >	snd_seq_device       
							      >	snd_seq_dummy        
							      >	snd_seq_midi         
							      >	snd_seq_midi_event   
							      >	snd_seq_oss          
snd_timer            						snd_timer            
softcursor           						softcursor           
soundcore            						soundcore            
stp                  						stp                  
tileblit             						tileblit             
toshiba_acpi         						toshiba_acpi         
vgastate             					      |	ttm                  
							      >	vesafb               
video                						video                
xor                  						xor                  
yenta_socket         						yenta_socket    
```


And for some reason the grub updater seems to be bad about adding 'resume=/dev/hda5' to the kernel line when I install new kernels, but I caught that before it caused me any headaches. ;-)

---

### Post by SaintDanBert on 2010-11-04
> **techunit said:**
> First of all I want you to know with that much ram the most swap your going to need is about 2 GB and thats going pretty far.

_Answer Part #1_

**Suspend** of any sort wants a swap [highlight]partition[/highlight].
The various release notes (recently) state that suspend fails unless the swap partition is at least as large as physical ram. This suggests that you need 12 GB swap with 12 GB ram.

Ah!? There is a wrinkle. As other posters suggest, you are not likely to do swapping with that much ram. Frankly, even 4 GB seems to be enough to avoid "swapping." 

This does not mean that your system will never write into swap space.

Because you might have some swap space bytes in use, suspend actually wants a little extra (lagnaippe) swap space over and above the size of physical ram. Canonical Support suggest 0.5 GB.

I write this because of the post that suggests you could reduce the size of your swap space drastically. Reduce to 12.5 GB or 13 GB? Yes!
Reduce to 2 GB or similar? Not if you want to suspend.

_Answer Part #2_

There are numerous bug reports that connected USB devices in general and SD card readers in specific result in various suspend and resume failures. Simply **umount** the USB drives before taking that system nap.

Bonne chance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-11-04
<GoodLaugh>
I took a Master's Degree in computer science during the late seventies.
My operating systems instructor made a big deal of an IBM sponsored study of a new feature called, "virtual memory." After spending a lot of time and money, the study concluded that "... virtual memory systems worked best with lots of physical memory..."
</GoodLaugh>

Ya Think?
~~~ 8d;-/ Dan

---

