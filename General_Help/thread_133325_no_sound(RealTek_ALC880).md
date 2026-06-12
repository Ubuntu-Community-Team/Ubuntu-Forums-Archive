---
title: "no sound(RealTek ALC880)"
date: 2006-02-20
forum: General Help
---

### Post by inovermyheadd on 2006-02-20
Hello, I did a fresh install of ubuntu and I don't have any sound.  Does anyone know how to get sound to work with this sound device?

I appreciate it:) 

Donald




Intel High Definition Audio 5.1/7.1 Channel Surround Sound w/S/PDIF port (RealTek ALC880)
3D Surround sound
Full Duplex
Built-in stereo speakers
Mic-in, Line in/S/PDIF Out and Headphone-out ports

---

### Post by inovermyheadd on 2006-02-20
ok cool, so I was wrong and my soundcard was detected...but I can't run the sound through headphones.  Is there anyway to get this to work?

I appreciate it!

thanks

---

### Post by inovermyheadd on 2006-02-23
Still can't figure this one out:)

---

### Post by Protostar on 2006-02-23
Can you hear sound from the speakers themselves?

---

### Post by inovermyheadd on 2006-02-23
I can hear from the speakers...but when I have my headphones in I can not hear from them at all.  When my headphones are in I can also hear my computer speakers.

---

### Post by inovermyheadd on 2006-03-05
a friendly bump

---

### Post by Bruce_C on 2006-03-05
You need the driver.  [Click here.]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs")  Look for the Unix(Linux) link at the bottom.  
The file should have an install script.

You might need other packages before you can successfully install the driver.  I can't remember what they were exactly, but here are the packages that I can remember:
build-essentials
linux-headers
g++ (or gcc?)
ncurses

Use synaptic to find and install these packages.  If my post is not thorough enough, let me know.

---

### Post by inovermyheadd on 2006-03-05
hey thanks for the reply, but I honestly don't know what I am doing.

I'm pretty sure I have downoladed:  build-essentials
linux-headers
g++ (or gcc?)

from installing other stuff but not ncurses....

What else do I have to do?

---

### Post by inovermyheadd on 2006-03-05
ok update...I used the automatic install and have the drivers on my computer...the bad thing is that now I have zero sound.

The installation process seems to have killed my alsa 1.0.10 driver which had some sound working (though not through my headphone jack)

hehe, so basically I am really lost now...I appreciate any help you can give

---

### Post by Bruce_C on 2006-03-06
So do you have ncurses installed now?  If not, install it and rerun the install script again.  

If that fails try installing the drivers manually.  Instructions are in the Readme.txt file.  I believe you can skip Step 2.  Report back with your errors.

---

### Post by inovermyheadd on 2006-03-06
ok problem.... automatic install failed

first off here are the steps for manual:

[PHP]Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.9b_1.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.9b_1.
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.[/PHP]

Ok so I don't understand step 4.  I lack a modules.conf  I have a /etc/modules  is that where that code is supposed to go?

Secondly...do I copy that exact code into "modules.conf" ?

Steps 1 and 3 look seem to have worked nicely

I still lack sound.  hehe, this is a good learning process though...

What now?

I tried to edit /etc/modprobe.d but it says I cannot edit it b/c it is a "regular file"

---

### Post by Bruce_C on 2006-03-06
I think I skipped Step 4.  I don't remember doing the tasks that Step 4 describes.  It's been a long while since I worked with this stuff.

I don't know what the problem is.  You do have the volume turned on right?  ALSA sets the volume to zero everytime you boot up.

Can you copy and paste the results after running these commands:
./configure
make
make install
./snddevices

I'd like to compare them.

---

### Post by inovermyheadd on 2006-03-06
I recently reformatted because I messed something else up hehe...I experiment too much I guess.

I will try it all again later and update ya.

Question:  So your computer's headphone jack completely works?  

When you put in the headphone jack it muts the external speakers and what not?

B/C no matter what I do I hear nothing through the headphone jack.

Anyway...thanks for the help thus far.:)

---

### Post by Bruce_C on 2006-03-07
[QUOTE=inovermyheadd]
So your computer's headphone jack completely works?  
When you put in the headphone jack it muts the external speakers and what not?
[/QUOTE]

Yes and yes.  

I have a few issues of with sound though.  I can't hear audio when there is a movie playing in my web browser while listening to music via xmms.  It's not a big deal for me so I've left it as is.

Hopefully, the next install will yield better results.

---

### Post by inovermyheadd on 2006-03-07
Ok, I did it, and I now have no sound again, I noticed that my volume control only has "volume" and "In Gain" on the OSS Mixer and

Only "PCM" on the HDA(Alsa Mixer) Is that common?

[PHP]inovermyhead@wifi-81-13:~/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$ sudo ./configure
Password:
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
checking for current directory... /home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.12-10-686/build
checking for directory with kernel build...
checking for kernel version... 2.6.12-10-686
checking for GCC version... Kernel compiler: gcc 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8) Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
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
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... module
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.12-10-686/kernel/sound
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... "yes"
checking for processor type... i686
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
checking for driver version... 1.0.9b
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "yes"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for class_simple... "yes"
checking for new unlocked/compat_ioctl... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... all
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
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
inovermyhead@wifi-81-13:~/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$ sudo make
make dep
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[4]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[4]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[4]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26'
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'

ALSA modules were successfully compiled.

inovermyhead@wifi-81-13:~/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$ sudo make install
find /lib/modules/2.6.12-10-686/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/acore
cp snd-hpet.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.12-10-686/kernel/sound/acore
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.12-10-686/kernel/sound/acore/oss
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/oss'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-dummy.ko snd-seq-instr.ko snd-seq-midi-emul.ko snd-seq-midi-event.ko snd-seq-midi.ko snd-seq-virmidi.ko snd-seq.ko /lib/modules/2.6.12-10-686/kernel/sound/acore/seq
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/acore/seq/instr
cp snd-ainstr-fm.ko snd-ainstr-gf1.ko snd-ainstr-iw.ko snd-ainstr-simple.ko /lib/modules/2.6.12-10-686/kernel/sound/acore/seq/instr
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/instr'
make[3]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.12-10-686/kernel/sound/acore/seq/oss
make[3]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq/oss'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/seq'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/i2c'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/drivers
cp snd-aloop.ko snd-dummy.ko snd-mtpav.ko snd-portman2x4.ko snd-serial-u16550.ko snd-serialmidi.ko snd-virmidi.ko /lib/modules/2.6.12-10-686/kernel/sound/drivers
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/pcsp'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/drivers/opl3
cp snd-opl3-lib.ko snd-opl3-synth.ko /lib/modules/2.6.12-10-686/kernel/sound/drivers/opl3
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl3'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/drivers/opl4
cp snd-opl4-lib.ko snd-opl4-synth.ko /lib/modules/2.6.12-10-686/kernel/sound/drivers/opl4
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/opl4'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/drivers/mpu401
cp snd-mpu401-uart.ko snd-mpu401.ko /lib/modules/2.6.12-10-686/kernel/sound/drivers/mpu401
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/mpu401'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/drivers/vx
cp snd-vx-lib.ko /lib/modules/2.6.12-10-686/kernel/sound/drivers/vx
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers/vx'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/drivers'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/isa'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/synth'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/pci
cp snd-atiixp-modem.ko snd-atiixp.ko snd-intel8x0.ko snd-intel8x0m.ko snd-via82xx-modem.ko snd-via82xx.ko /lib/modules/2.6.12-10-686/kernel/sound/pci
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/pci/ac97
cp snd-ac97-codec.ko snd-ak4531-codec.ko /lib/modules/2.6.12-10-686/kernel/sound/pci/ac97
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ac97'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/pci/ali5451
cp snd-ali5451.ko /lib/modules/2.6.12-10-686/kernel/sound/pci/ali5451
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/ali5451'
make[2]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
mkdir -p /lib/modules/2.6.12-10-686/kernel/sound/pci/hda
cp snd-hda-codec.ko snd-hda-intel.ko /lib/modules/2.6.12-10-686/kernel/sound/pci/hda
make[2]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci/hda'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pci'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/usb'
make[1]: Entering directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
make[1]: Leaving directory `/home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/pcmcia'
/sbin/depmod -a 2.6.12-10-686
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/inovermyhead/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/include/sound /usr/include/sound; \
else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
                install -m 644 -g root -o root $f /usr/include/sound; \
        done \
fi
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

inovermyhead@wifi-81-13:~/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26$ sudo ./snddevices
Creating /dev/mixer?... done
Creating /dev/sequencer... done
Creating /dev/midi0?... done
Creating /dev/dsp?... done
Creating /dev/audio?... done
Creating /dev/sndstat... done
Creating /dev/music... done
Creating /dev/dmmidi?... done
Creating /dev/dmfm?... done
Creating /dev/amixer?... done
Creating /dev/adsp?... done
Creating /dev/amidi?... done
Creating /dev/admmidi?... done
create symbolic link `/dev/mixer' to `/dev/mixer0'
create symbolic link `/dev/midi' to `/dev/midi00'
create symbolic link `/dev/dsp' to `/dev/dsp0'
create symbolic link `/dev/audio' to `/dev/audio0'
create symbolic link `/dev/sequencer2' to `/dev/music'
create symbolic link `/dev/adsp' to `/dev/adsp0'
create symbolic link `/dev/amidi' to `/dev/amidi0'
rm: cannot remove `/dev/snd': Is a directory
Creating /dev/snd/control?... done
Creating /dev/snd/seq... done
Creating /dev/snd/timer... done
Creating /dev/snd/hw??... done
Creating /dev/snd/midi??... done
Creating /dev/snd/pcm??p... done
Creating /dev/snd/pcm??c... done
ALSA loader devices
Creating /dev/aload?... done
Creating /dev/aloadSEQ... done
[/PHP]

There are my results.

Maybe I just don't know how to unmute...

---

### Post by Bruce_C on 2006-03-07
Here is what my Volume Control looks like:
HDA Intel (Alsa Mixer)
-Headphone
-CD
-Microphone0

Realtek ALC889 (OSS Mixer)
-Volume
-Microphone
-CD
-PCM-2


From what you provided things look nearly identical, except for the kernel.  Mine is 2.6.12-9-386.  Some of the output seems to be missing.  Your 'sudo make install' is cut short and I don't see the output for ./snddevices.  Try pasting those outputs again.

---

### Post by inovermyheadd on 2006-03-10
is there a way to start my audio drivers from scratch without reformatting?  because my speakers worked fine before my intervention...well besides the headphone jack.

---

### Post by inovermyheadd on 2006-03-12
still working on this one...

---

### Post by gewone on 2008-06-05
Just wanted to say that I experienced the same problem with an integrated Intel chip using ACL880 or something like that, Realtek anyways. I had the same issue like the orig. poster; mixer icon by still no snd output. Strange, I thought at first. Then it hit me: not good at all, mixer but still no sound means gonna-be-a-living-hell-to-felsöka.

Anyways, solved it by sudo apt-get install almost-any-wildcard-including-alsa. Now the sound works, even though it seems to have difficulties loading the driver instantly with .MOV (qt) clips, like 1/3 of the times I run them (koffeine) I get the error about no drivers will load.

Gah..


Just realized that I just 'upped' a ~2 year old post. Hope I won't get banned or anything..

---

