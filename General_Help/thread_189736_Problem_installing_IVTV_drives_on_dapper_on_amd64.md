---
title: "Problem installing IVTV drives on dapper on amd64"
date: 2006-06-05
forum: General Help
---

### Post by Sureshot324 on 2006-06-05
The ivtv drivers worked fine on my breezy amd64 installation, but I can't seem to get them working on dapper.  The problem seems to be they can't find the firmware.  I've been following the guide at

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

and have made the changes in this thread:

[http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv](http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv)

I'm putting all the firmware files in /lib/firware instead of /usr/lib/hotplug/firmware.  Her is the output when I run dmesg:

```
[   40.694141] ivtv:  ==================== START INIT IVTV ====================
[   40.694144] ivtv:  version 0.4.4 (tagged release) loading
[   40.694145] ivtv:  Linux version: 2.6.15-23-amd64-generic SMP preempt gcc-4.0
[   40.694147] ivtv:  In case of problems please include the debug info between
[   40.694149] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   40.694151] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   40.694201] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[   40.694239] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 58
[   40.694247] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   40.733603] tveeprom: ivtv version
[   40.733606] tveeprom: Hauppauge: model = 26552, rev = B268, serial# = 7865027
[   40.733609] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[   40.733611] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[   40.733613] tveeprom: audio processor = CX25843 (type = 25)
[   40.733615] tveeprom: decoder processor = CX25843 (type = 1e)
[   40.733618] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[   40.772895] input: PC Speaker as /class/input/input2
[   40.803289] FDC 0 is a post-1991 82077
[   40.903423] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[   40.903429] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   41.303724] irda_init()
[   41.303739] NET: Registered protocol family 23
[   41.331193] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   41.374914] ts: Compaq touchscreen protocol output
[   41.422429] cx25840 2-0044: unable to open firmware v4l-cx25840.fw
[   41.469910] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[   41.471973] Unable to handle kernel NULL pointer dereference at 0000000000000008 RIP:
[   41.471978] <ffffffff801552de>{finish_wait+78}
[   41.471985] PGD 3cd1a067 PUD 3cd1b067 PMD 0
[   41.471988] Oops: 0002 [1] PREEMPT SMP
[   41.471991] CPU 0
[   41.471992] Modules linked in: tsdev sir_dev cx25840 irda tuner psmouse floppy pcspkr crc_ccitt sk98lin tveeprom ivtv nvidia i2c_algo_bit af_packet usblp usbhid skge videodev snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd emu10k1_gp gameport soundcore shpchp pci_hotplug i2c_nforce2 i2c_core sg evdev ext3 jbd ide_generic ohci1394 forcedeth ieee1394 ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk generic sd_mod amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[   41.472023] Pid: 3523, comm: kIrDAd Tainted: PF     2.6.15-23-amd64-generic #1
[   41.472026] RIP: 0010:[<ffffffff801552de>] <ffffffff801552de>{finish_wait+78}
[   41.472031] RSP: 0018:ffff81003abedef8  EFLAGS: 00010002
[   41.472034] RAX: 0000000000000000 RBX: ffff81003abedf30 RCX: 00000000c0000100
[   41.472037] RDX: 0000000000000000 RSI: 0000000000000202 RDI: ffffffff888f6d40
[   41.472040] RBP: ffff81003abedf18 R08: ffff81003abec000 R09: 0000000000000000
[   41.472043] R10: 0000000000000000 R11: ffffffff8029f1d0 R12: ffffffff888f6d40
[   41.472047] R13: ffffffff888f6700 R14: ffffffff8037bb20 R15: 00002aaaaaac4000
[   41.472051] FS:  00002aaaaadfb6d0(0000) GS:ffffffff80447800(0000) knlGS:0000000000000000
[   41.472053] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   41.472056] CR2: 0000000000000008 CR3: 000000003cd19000 CR4: 00000000000006e0
[   41.472060] Process kIrDAd (pid: 3523, threadinfo ffff81003abec000, task ffff81003e17a200)
[   41.472062] Stack: ffff81003a39bf18 00000000000092de 00002aaaaaac4000 ffffffff888f2a8f
[   41.472067]        0000000000000000 ffff81003e17a200 ffffffff801387b0 0000000000000000
[   41.472072]        0000000000000000 ffff810037a3d740
[   41.472074] Call Trace:<ffffffff888f2a8f>{:sir_dev:irda_thread+207} <ffffffff801387b0>{default_wake_function+0}
[   41.472092]        <ffffffff80110dfe>{child_rip+8} <ffffffff888f29c0>{:sir_dev:irda_thread+0}
[   41.472112]        <ffffffff80110df6>{child_rip+0}
[   41.472118]
[   41.472119] Code: 48 89 42 08 48 89 10 48 89 5b 08 48 89 5d 18 48 8b 1c 24 48
[   41.472127] RIP <ffffffff801552de>{finish_wait+78} RSP <ffff81003abedef8>
[   41.472132] CR2: 0000000000000008
[   41.472133]  <6>note: kIrDAd[3523] exited with preempt_count 1
[   41.501383] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   41.508086] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[   41.529909] tda9887 2-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[   41.529917] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[   42.157561] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[   42.157566] ivtv0: did you put the firmware in the hotplug firmware directory?
[   42.157568] ivtv0 warning: failed loading encoder firmware
[   42.157571] ivtv0 warning: Error loading firmware -3!
[   42.157573] ivtv0: Error -3 initializing firmware.
[   42.160040] ivtv0: Error -12 on initialization
[   42.160047] ivtv: probe of 0000:01:07.0 failed with error -12
[   42.160056] ivtv:  ====================  END INIT IVTV  ====================

```

It seems like it's not finding any of the firmware files, but they definatly are in /lib/firmware and it should be able to find them, no?

I looked at the firmware guide on ivtvdrivers.org, and it says to find your hotplug directory, look at the firmware.agent file in /etc/hotplug, but i dont' have an /etc/hotplug directory, and I did a file search and I don't seem to have a firmware.agent file anywhere.

In the /lib/firmware directory, theres a folder called 2.6.15-23-amd64-generic, so I thought that might be the hotplug directory in the amd64 version of dapper, but I copied all the files there and it still don't work.

Anyone have any ideas?

---

### Post by mattkenn4545 on 2006-06-05
Are they in a sub-directory in the firmware directory?

If so move them out and see if that works.

Also no matter what I did I ended up having to reboot and it worked fine.

Also where are you getting the firmware from?

---

### Post by Sureshot324 on 2006-06-06
They're in /lib/firmware, not a sub directory.  There is a subdirectory in /lib/firmware called 2.6.15-23-amd64-generic.  I tried copying all the firmware files to that subdirectory thinking that may be where the hotplug directory is for the amd64 version of ubuntu, but that didn't work so I deleted them.  They're not back in /lib/firmware.

I'm getting the firmware with these commands from the Hyams guide:

wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)

---

### Post by mattkenn4545 on 2006-06-06
Ok took a closer look and the firmware should be in /lib/firmware/'uname -r'/ Otherwords in /lib/firmware/2.6.15-23-amd64-generic/

Try copying the file firmware.tar.gz which is found on ([http://www.ivtvdriver.org/index.php/Firmware](http://www.ivtvdriver.org/index.php/Firmware)) to the above directory

Direct link to the file
[http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)

Note you may need to reboot to get everything working

To others what is the command to 'reinitialze' the kernel modules

---

### Post by mattkenn4545 on 2006-06-06
Here is how I got it working (please forgive the somewhat unorganize mess it is)

ivtv driver see ([http://www.ivtvdriver.org](http://www.ivtvdriver.org))
1. Download the tarball for the driver and the firmware
2. Install the req packages
	module-assistant
	build-essential
3. # sudo module-assistant prepare (Install all the packages that it recommends)
4. Extract the source tarball somewhere
5. # cd <path where extracted>/ivtv-*
6. Enter ALL of this in terminal

make
sudo make install

cd /lib/modules/`uname -r`/kernel/drivers/media/video/
sudo mv msp3400.ko msp3400.ko.old 
sudo mv tveeprom.ko tveeprom.ko.old
sudo mv tuner.ko tuner.ko.old
sudo mv tda9887.ko tda9887.ko.old

7. cd <path where extracted>/ivtv-*/driver

8. # sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/media/video/

9. Extract the firmware somewhere
10. # sudo cp <where the firmware is>/* /lib/firmware/'uname -r'/
11. sudo modprobe ivtv
12. check for errors with load with 'dmesg'
13. if there is reboot and try again
14. test with cat /dev/video0 > test.mpg
that should give you a mpg that should be playable in totem

note you can also use mplayer /dev/video0 to see the video 'live'

---

### Post by Sureshot324 on 2006-06-07
I figured it out.  The firmware actually has to go to /lib/firmware/2.6.15-23-amd64-generic.  I had tried that before but I forgot to remake the symboitic link, which was still pointing to the old location at /lib/firmware.  It's working great now.

---

