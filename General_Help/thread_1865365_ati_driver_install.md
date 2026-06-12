---
title: "ati driver install"
date: 2011-10-20
forum: General Help
---

### Post by jamil.farooq@hotmail.com on 2011-10-20
hi 


i hv some situation here with my ATI RADEON graphics card. i m trying to install the driver with script downloaded from amd site.
with command 

sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildandinstallpkg Ubuntu/oneiric


which gives me following error:


objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.heKQb3'
dh_shlibdeps -l/tmp/fglrx.heKQb3/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: error: no dependency information found for /lib/libc.so.6 (used by debian/fglrx/usr/lib/fglrx/libatiadlxx.so).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.heKQb3'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.pva5AK



does anyone have idea about what i have done wrong??

---

### Post by KingYaba on 2011-10-20
Just do
```
sudo sh ati-driver-installer-11-9-x86.x86_64.run
```

and then install it.Doing a specific build for Ubuntu isn't necessary. Once installed, be sure to follow up with this command: 

```
sudo aticonfig --initial -f
```

And then reboot.

---

### Post by jamil.farooq@hotmail.com on 2011-10-20
when i run this command it gives me following error that is why i thought to build a package first for my distr

loki_setup: Couldn't write to file: //usr/lib/xorg/modules/drivers/fglrx_drv.so
loki_setup: Couldn't write to file: //usr/lib/dri/fglrx_dri.so
loki_setup: Couldn't write to file: //usr/bin/fgl_glxgears
loki_setup: Couldn't write to file: //usr/bin/fglrxinfo
loki_setup: Couldn't write to file: //usr/bin/aticonfig
loki_setup: Couldn't write to file: //usr/bin/atiodcli
loki_setup: Couldn't write to file: //usr/bin/atiode
loki_setup: 2 Unable to find file 'install/usr/X11R6/lib/modules/dri/fglrx_dri.so' in '/home/sim-paf/Downloads/fglrx-install.mfWGnF'
loki_setup: 2 Unable to find file 'install/usr/bin/amdconfig' in '/home/sim-paf/Downloads/fglrx-install.mfWGnF'


as you see here its not writing necessary files so i can't run aticonfig

---

### Post by mastablasta on 2011-10-20
what graphics card?
 
Ubuntu should have the latest drivers in its own hardware drivers section in system administration (ie.e repositories)

---

### Post by jamil.farooq@hotmail.com on 2011-10-20
well i have tried that as well but some of my applications( more specifically flightgear is not working due to that) giving error related to [xcb] so i tried installing driver from downloaded script from ati site.

but now its not installing it 

my card is radeon HD 5800
 VGA compatible controller: ATI Technologies Inc Radeon HD 5800 Series (Cypress LE)

desperate for a solution help me 
thanx

---

### Post by KingYaba on 2011-10-20
Have you followed the instructions on the Wiki site? Did you install the prerequisite packages?  

They have you install a few things before you install the driver. 

[http://wiki.cchtml.com/index.php/Ubuntu#Installation](http://wiki.cchtml.com/index.php/Ubuntu#Installation) 

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
```
```
sudo apt-get install ia32-libs
```

And then proceed to install the driver.

---

### Post by jamil.farooq@hotmail.com on 2011-10-21
well that doesn't change anything ... i am still getting the same error.

---

### Post by varunendra on 2011-10-21
> **jamil.farooq@hotmail.com said:**
> 
 VGA compatible controller: ATI Technologies Inc Radeon HD 5800 Series (Cypress LE)5800 'series', but is it exactly 5800 or any of 5850/5870? They should be well supported by the open source drivers as suggested here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If unsure, please post outputs of:
```
sudo lshw -C display
lsmod
```

---

### Post by jamil.farooq@hotmail.com on 2011-10-24
i have printed the output of both commands


**************************************************************
lshw -C display
***************************************************************
description: VGA compatible controller
       product: Radeon HD 5800 Series (Cypress LE)
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:76 memory:d0000000-dfffffff memory:fbcc0000-fbcdffff ioport:c000(size=256) memory:fbca0000-fbcbffff
*****************************************************************

lsmod
*****************************************************************
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                961723  2 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65224  1 radeon
mxm_wmi                12859  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 radeon
drm                   196322  3 radeon,ttm,drm_kms_helper
wmi                    18744  1 mxm_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                63474  0 
i7core_edac            23254  0 
edac_core              46858  1 i7core_edac
i2c_algo_bit           13199  1 radeon
serio_raw              12990  0 
asus_atk0110           17742  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
usbhid                 41905  0 
crc_itu_t              12627  1 firewire_core
pata_jmicron           12651  0 
hid                    77367  1 usbhid
e1000e                139775  0 
xhci_hcd               72957  0 
ahci                   21634  0 
libahci                25761  1 ahci
******************************************************************

---

### Post by oldtimer7777 on 2011-10-24
This might be a bit too obvious but have you tried:

sudo jockey-gtk

Does it list the driver you need or is it empty?

> **jamil.farooq@hotmail.com said:**
> i have printed the output of both commands


**************************************************************
lshw -C display
***************************************************************
description: VGA compatible controller
       product: Radeon HD 5800 Series (Cypress LE)
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:76 memory:d0000000-dfffffff memory:fbcc0000-fbcdffff ioport:c000(size=256) memory:fbca0000-fbcbffff
*****************************************************************

lsmod
*****************************************************************
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                961723  2 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65224  1 radeon
mxm_wmi                12859  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 radeon
drm                   196322  3 radeon,ttm,drm_kms_helper
wmi                    18744  1 mxm_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                63474  0 
i7core_edac            23254  0 
edac_core              46858  1 i7core_edac
i2c_algo_bit           13199  1 radeon
serio_raw              12990  0 
asus_atk0110           17742  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
usbhid                 41905  0 
crc_itu_t              12627  1 firewire_core
pata_jmicron           12651  0 
hid                    77367  1 usbhid
e1000e                139775  0 
xhci_hcd               72957  0 
ahci                   21634  0 
libahci                25761  1 ahci
******************************************************************

---

### Post by techvish81 on 2011-10-24
don't install that driver,  the inbuilt driver is working fine and this driver will kill your system,  I had to hard reset after installing this driver,  same display card here.

---

### Post by jamil.farooq@hotmail.com on 2011-10-25
well until 11.10 i had correctly working proprietary driver. but the day i install 11.10 this driver does not work. in fact it doesn't install the driver properly as i can't run Control Center and aticonfig as well.

for that reason i deactivated the driver from proprietary driver's list and wanted to manually install it from script.

---

### Post by varunendra on 2011-10-25
Have you tried the Open Source driver as described in the guide I linked to? The proprietary one may have compatibility issues as 11.10 is rather new. I didn't read the error messages thoroughly nor did I try to interpret them, but I think going with defaults (+ Open source drivers, if necessary) should be better for this card. At least for now.

---

### Post by jamil.farooq@hotmail.com on 2011-10-25
> **techvish81 said:**
> don't install that driver,  the inbuilt driver is working fine and this driver will kill your system,  I had to hard reset after installing this driver,  same display card here.

without proprietary driver i can't access unity interface ... gnome works fine. and also with proprietary driver unity does work fine. but it doesn't install aticonfig and Control Center. and some of my applications related to graphics doesn't run in both cases.

---

### Post by jamil.farooq@hotmail.com on 2011-10-26
> **varunendra said:**
> Have you tried the Open Source driver as described in the guide I linked to? The proprietary one may have compatibility issues as 11.10 is rather new. I didn't read the error messages thoroughly nor did I try to interpret them, but I think going with defaults (+ Open source drivers, if necessary) should be better for this card. At least for now.

is this all i have to do to install opensource version of driver.??

> 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg


but it didn't work ... 
ubuntu was great before 11.10

---

### Post by varunendra on 2011-10-26
> **jamil.farooq@hotmail.com said:**
> without proprietary driver i can't access unity interface ... gnome works fine. and also with proprietary driver unity does work fine. but it doesn't install aticonfig and Control Center. and some of my applications related to graphics doesn't run in both cases.
If that is the case, have you tried the most obvious solution first? That is, goto Software Center > Edit > Software Sources, enable restricted drivers repository, let it refresh itself. Then open "Additional Drivers" and see if there is a catalyst driver available for the card.

Just like this wiki page suggests: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Using_Ubuntu-supplied_fglrx.2FCatalyst](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Using_Ubuntu-supplied_fglrx.2FCatalyst)

---

### Post by jamil.farooq@hotmail.com on 2011-10-27
yeah that was obvious i hav already done that with no avail

---

### Post by varunendra on 2011-10-27
Then I currently have no more alternate ideas since you problem STARTS with the next method on the same wiki page. Have you studies the script to see if there are any possible invalid references in it? (I'm concerned about those "can't create...", "unable to find..." error messages).

Also, have you thought about switching back to 11.04? Although it would be best if someone could figure out the problem with the current setup.


**_EDIT_:**
Ah, nevermind about 'reading' the script. I just realized it is 73MB in size :)

---

### Post by jamil.farooq@hotmail.com on 2011-10-27
> **varunendra said:**
> Then I currently have no more alternate ideas since you problem STARTS with the next method on the same wiki page. Have you studies the script to see if there are any possible invalid references in it? (I'm concerned about those "can't create...", "unable to find..." error messages).

Also, have you thought about switching back to 11.04? Although it would be best if someone could figure out the problem with the current setup.


**_EDIT_:**
Ah, nevermind about 'reading' the script. I just realized it is 73MB in size :)


script is in binary form so there is no point in reading it ... how could i switch back to 11.04 is thr any shortway except reinstalling???

---

### Post by varunendra on 2011-10-27
> **jamil.farooq@hotmail.com said:**
> how could i switch back to 11.04 is thr any shortway except reinstalling???
Unfortunately, there's no other way except reinstallation. One similar solution sometimes may be to boot choosing the older kernel from grub menu. But that (only sometimes) solves problems related with compatibility of already installed drivers, while yours is a bit different.

I did some read on dpkg-shlibdeps related problems, and it seems to be in existence for quite some time. Couldn't find a possible solution though.

As a doublecheck, make sure:

[LIST]
[*]dh_shlibdeps and dpkg-shlibdeps exist in /usr/bin directory,
[/LIST]

[LIST]
[*]linux-headers are installed for your current kernel in use,
[/LIST]

[LIST]
[*]any previous installation traces are removed as instructed in the wiki page: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)
[/LIST]

[LIST]
[*]all pre-installetion steps/checks are complete as described in the wiki page: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
[/LIST]

[LIST]
[*]All the installation steps are carried out in the same order as described on the above page.
[/LIST]
If all these steps are completed as desired, then I'm afraid only an expert who understands the script and how exactly it works may be able to help. Meanwhile, the road to reinstallation is always open :(. Alternatively, you can install 11.04 in a separate partition and wait until ubuntu releases a suitable driver for Oneiric (through "Additional Drivers" option).

---

