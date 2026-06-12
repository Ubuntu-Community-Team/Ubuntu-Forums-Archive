---
title: "Sound Blaster Live! Issues"
date: 2006-06-08
forum: General Help
---

### Post by AngryKidJoe on 2006-06-08
**Product:** SB0410 SBLive! 24-bit
**info.linux.driver:** CA0106

Ubuntu is defaulting to the onboard sound. I've done multiple searches and have yet to find a solution. When I go to **System > Preferences > Sound** and Switch from my onboard to CA0106, the option doesn't stay. I can open it again and again and it defaults to the onboard. Also, when I open up alsamixer the only options I have to modify for the the Live! card are Line-In & Mic-In.

After trying a couple fixes, my onboard doesn't work anymore and I get 
[I][INDENT][Couldn't open audio]
Please Check that:
Your sound card is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard[/INDENT][/I]
Any help would be greatly appreciated and feel free to use my IM contacts.

**EDIT:** I just booted up Neverwinter Nights and the sound worked, but it works no where else.

---

### Post by jazzmuzik on 2006-06-08
Turn off your onboard sound system in the system BIOS. Then Ubuntu will be forced to use the only remaining sound system.

---

### Post by AngryKidJoe on 2006-06-08
That solved the issue of the Sound Preference option permenantly set on On-Board. The *[Couldn't Open Audio]* error is now gone but now I have no sound and it is not muted in alsamixer. There's still the issue of the only options in alsomixer being *Line-In* and *Mic-In*.

---

### Post by AngryKidJoe on 2006-06-09
I'm still searching around for solutions, mainly on these forums and via Wikipedia. Anyone suggest any other leads?

---

### Post by Sutekh on 2006-06-09
Do you have the correct module for the SB Live! 24bit card.
```
lsmod | grep snd
``` You should have the **snd_ca0106** module listed next to [B]snd.


[/B]You should also create an ~/.asoundrc file so that the SB card is used as default over the onboard, I'd recommend this over disabling the onboard.  Having two sound cards can be useful.

First find out what card number the SB Live one is
```

cat /proc/asound/cards
``` Then create the ~/.asoundrc file to set the default card
```
gedit ~/.asoundrc
``` Then paste in these lines, changing the bold **card 0** with whatever the SB card is listed as.
```
pcm.!default {
    type hw
    **card 0**
}
ctl.!default {
    type hw           
    **card 0**
}
```
I hope this helps out.

---

### Post by AngryKidJoe on 2006-06-10
It brings up the text editor file and I just click save and that should save it to it's default directory, correct?

**EDIT:** Alright, now I have this error:
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

[B]EDIT 2: [COLOR="DarkGreen"]GOT THIS FIXED, skip it, only here for reference.[/COLOR]
[/B][By following these instructions](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106#opt), I get this:
```
sudo ./configure --with-cards=ca0106 --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc4a
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.15-23-386/build
checking for directory with kernel build...
checking for kernel version... 2.6.15-23-386
checking for GCC version... Kernel compiler: gcc 4.0.3 (Ubuntu 4.0.3-1ubuntu5) Used compiler: gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
checking for built-in ALSA... "no"
checking for existing ALSA module... "yes"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "yes"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
Removing a dummy linux/workqueue.h.
checking for kernel linux/dma-mapping.h... "yes"
Removing a dummy linux/dma-mapping.h.
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
Removing a dummy linux/device.h.
checking for kernel linux/jiffies.h... "yes"
Removing a dummy linux/jiffies.h.
checking for kernel linux/compat.h... "yes"
Removing a dummy linux/compat.h.
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
Removing a dummy linux/moduleparam.h.
checking for kernel linux/syscalls.h... "yes"
Removing a dummy linux/syscalls.h.
checking for kernel linux/firmware.h... "yes"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.15-23-386/kernel/sound
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... "yes"
checking for processor type... i486
checking for i386 machine type... default
checking for SMP... "no"
checking for Video device support in kernel... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "yes"
checking for snprintf... "yes"
checking for vsnprintf... "yes"
checking for scnprintf... "yes"
checking for sscanf... "yes"
checking for vmalloc_to_page... "yes"
checking for old kmod... "no"
checking for PDE... "yes"
checking for pci_set_consistent_dma_mask... "yes"
checking for pci_dev_present... "yes"
checking for msleep... "yes"
checking for msleep_interrupt... "yes"
checking for tty->count is the atomic type... "no"
checking for video_get_drvdata... "yes"
checking for io_remap_pfn_range... "yes"
checking for kcalloc... "yes"
checking for saved_config_space in pci_dev... "yes"
checking for new pci_save_state... "yes"
Removing local linux/pnp.h.
checking for driver version... 1.0.9rc4a
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "yes"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for new unlocked/compat_ioctl... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... ca0106
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
ln: creating symbolic link `include/sound' to `../alsa-kernel/include': Permission denied
make: *** [include/sound/version.h] Error 1
find /lib/modules/2.6.15-23-386/kernel/sound -name 'snd*.*o' | xargs rm -f
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/bluetooth/snd-bt-sco.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/oss/snd-mixer-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/oss/snd-pcm-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/instr/snd-ainstr-fm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/instr/snd-ainstr-gf1.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/instr/snd-ainstr-iw.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/instr/snd-ainstr-simple.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/oss/snd-seq-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-device.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-dummy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-instr.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-midi-emul.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-midi-event.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-midi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq-virmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/seq/snd-seq.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-hwdep.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-page-alloc.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-pcm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-rawmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-rtctimer.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd-timer.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/core/snd.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/mpu401/snd-mpu401.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/opl3/snd-opl3-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/opl4/snd-opl4-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/opl4/snd-opl4-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/vx/snd-vx-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/snd-dummy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/snd-mtpav.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/snd-serial-u16550.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/drivers/snd-virmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/other/snd-ak4114.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/other/snd-ak4117.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/other/snd-ak4xxx-adda.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/other/snd-tea575x-tuner.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/snd-cs8427.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/snd-i2c.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/i2c/snd-tea6330t.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/ad1816a/snd-ad1816a-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/ad1816a/snd-ad1816a.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/ad1848/snd-ad1848-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/ad1848/snd-ad1848.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4231-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4231.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4232.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4236-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4236.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/es1688/snd-es1688-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/es1688/snd-es1688.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-gus-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-gus-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-gusclassic.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-gusextreme.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-gusmax.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-interwave-stb.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/gus/snd-interwave.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/opti9xx/snd-opti93x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-emu8000-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-es968.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb-common.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb16-csp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb16-dsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb16.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb8-dsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb8.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sbawe.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/wavefront/snd-wavefront.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-als100.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-azt2320.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-cmi8330.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-dt019x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-es18xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-opl3sa2.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-sgalaxy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-sscape.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ac97/snd-ac97-bus.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ac97/snd-ac97-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ac97/snd-ak4531-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ali5451/snd-ali5451.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/au88x0/snd-au8810.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/au88x0/snd-au8820.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/au88x0/snd-au8830.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ca0106/snd-ca0106.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/cs46xx/snd-cs46xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/emu10k1/snd-emu10k1x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/hda/snd-hda-intel.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ice1712/snd-ice1712.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ice1712/snd-ice1724.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/korg1212/snd-korg1212.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/mixart/snd-mixart.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/nm256/snd-nm256.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/rme9652/snd-hdsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/rme9652/snd-hdspm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/rme9652/snd-rme9652.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/trident/snd-trident-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/trident/snd-trident.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/vx222/snd-vx222.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/ymfpci/snd-ymfpci.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-ad1889.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-als4000.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-atiixp-modem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-atiixp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-azt3328.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-bt87x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-cmipci.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-cs4281.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-ens1370.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-ens1371.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-es1938.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-es1968.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-fm801.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-intel8x0.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-intel8x0m.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-maestro3.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-rme32.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-rme96.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-sonicvibes.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-via82xx-modem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pci/snd-via82xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/pcmcia/vx/snd-vxpocket.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/synth/emux/snd-emux-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/synth/snd-util-mem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/usb/usx2y/snd-usb-usx2y.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/usb/snd-usb-audio.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.15-23-386/kernel/sound/usb/snd-usb-lib.ko': Permission denied
make: *** [install-modules] Error 123

```

---

### Post by AngryKidJoe on 2006-06-10
After using [this tutorial](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106#opt) there are no sound card options under **System -> Preferences -> Sound**, ALSAMixer does not work, and Neverwinter Nights will not boot, but DooM 3 will.
[quote="alsamixer error"]ALSA lib conf.c:1165:(parse_def) NVidia does not exists
ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:1:38:No such file or directory
ALSA lib conf.c:2837:(snd_config_hook_load) /home/akj/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: No such file or directory
[/quote]
[quote="Neverwinter Nights error"]mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/akj/.kde/socket-AngryPenguin.
can't create mcop directory
[/quote]

---

