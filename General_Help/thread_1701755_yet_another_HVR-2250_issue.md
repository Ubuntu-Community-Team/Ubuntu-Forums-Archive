---
title: "yet another HVR-2250 issue"
date: 2011-03-06
forum: General Help
---

### Post by Victormd on 2011-03-06
Recently I had to replace my Hauppauge HVR-1600 (it was doing everything I wanted it to do but after a few years burned out) and decided to get the HVR-2250. Before purchasing I checked the forums and noticed that there was quite a bit of support and most everyone managed to get it working so I thought it would be a good idea.

The problem I have now is that, though lspci shows the card as
**Multimedia controller: Philips Semiconductors Device 7164 (rev 81)**; however, when trying to setup mythtv-backend, the card does not show up under the "capture card" section. After a few hours of research, I came across [this thread]("http://ubuntuforums.org/showthread.php?t=942403&page=22") and it seemed to be general consensus that the method worked so I tried it. Still no luck.

I ended up formatting, fresh install of Ubuntu 10.10 and then installed MythTV and still nothing. Not really sure where to go from here.

Any suggestions???

---

### Post by Victormd on 2011-03-07
Just a note...
When I say that the HVR-2250 doesn't show up, I mean, no device number under DVB cards or option to select any card, nothing...
The system is pretty much stripped down, it's a shuttle with everything onboard (AMD graphics card), Phenom II, 4 GB of RAM, and a 750GB HDD.

---

### Post by Victormd on 2011-03-07
instead of bumping, let me keep giving information:
Here's the dmesg output:
> [ 18.323796] saa7164 driver loaded
[ 18.323844] saa7164 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 18.324682] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[ 18.324688] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe400000
[ 18.324693] saa7164 0000:02:00.0: setting latency timer to 64
[ 18.484010] saa7164_downloadfirmware() no first image
[ 18.484053] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[ 18.491579] saa7164_downloadfirmware() firmware read 3978608 bytes.
[ 18.491582] saa7164_downloadfirmware() firmware loaded.
[ 18.491589] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[ 18.491595] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[ 18.491596] saa7164_downloadfirmware() BSLSize = 0x0
[ 18.491597] saa7164_downloadfirmware() Reserved = 0x0
[ 18.491598] saa7164_downloadfirmware() Version = 0x51cc1
[ 25.364345] saa7164_downloadimage() Image downloaded, booting...
[ 25.468354] saa7164_downloadimage() Image booted successfully.
[ 27.588029] saa7164_downloadimage() Image downloaded, booting...
[ 29.252034] saa7164_downloadimage() Image booted successfully.
[ 29.288807] tveeprom 3-0000: audio processor is SAA7164 (idx 43)
[ 29.288809] tveeprom 3-0000: decoder processor is SAA7164 (idx 40)
[ 29.288813] saa7164[0]: Hauppauge eeprom: model=88061
[ 29.539972] saa7164_api_i2c_read() error, ret(2) = 0x13
[ 29.540070] saa7164_dvb_register() Frontend initialization failed
[ 29.540072] saa7164_initdev() Failed to register dvb adapters on porta
[ 29.765787] saa7164_api_i2c_read() error, ret(2) = 0x13
[ 29.765866] saa7164_dvb_register() Frontend initialization failed
[ 29.765867] saa7164_initdev() Failed to register dvb adapters on portb 

---

### Post by LowSky on 2011-03-08
Victormd, from this line of code I see it is loading the wrong firmware.

[ 18.484053] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)

We neeed to delete that firmware and use the newer version that I emailed you with.
the newer verison ends in 1.0.3-3.fw
Did you run the code I gave you? you never mentioned that in your PM?

```

sudo apt-get install mercurial libncurses5-dev unzip && wget -c http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip && wget -c http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip && wget -c http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw && wget -c http://www.steventoth.net/linux/hvr22xx/extract.sh && sh extract.sh && sudo cp *fw /lib/firmware && hg clone http://kernellabs.com/hg/saa7164-stable/ && cd saa7164-stable && make CONFIG_DVB_FIREDTV:=n && sudo make install && sudo reboot
```

this will take a while to run but works

---

### Post by Victormd on 2011-03-08
I did run it (I sent you 2 PMs yesterday... :))

I get these errors towards the end:
> Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/victor/tvtuner/saa7164-stable/v4l'
make[1]: Entering directory `/home/victor/tvtuner/saa7164-stable/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-28-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/victor/tvtuner/saa7164-stable/v4l/firmware'
make[2]: Leaving directory `/home/victor/tvtuner/saa7164-stable/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/victor/tvtuner/saa7164-stable/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/victor/tvtuner/saa7164-stable/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-28-generic-pae/build
make -C /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/home/victor/tvtuner/saa7164-stable/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  CC [M]  /home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.o
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c:314: error: implicit declaration of function 'kzalloc'
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c:314: warning: assignment makes pointer from integer without a cast
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c:365: warning: assignment makes pointer from integer without a cast
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.c:1314: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/victor/tvtuner/saa7164-stable/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/victor/tvtuner/saa7164-stable/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/victor/tvtuner/saa7164-stable/v4l'
make: *** [all] Error 2

---

### Post by Victormd on 2011-03-08
Also, I deleted **v4l-saa7164-1.0.3.fw** from **/lib/firmware** and dmesg is still trying to pull it up.
> [   15.979613] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe400000
[   15.979619] saa7164 0000:02:00.0: setting latency timer to 64
[   16.140009] saa7164_downloadfirmware() no first image
[   16.140052] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   16.141150] saa7164_downloadfirmware() Upload failed. (file not found?)


BTW, thank you so much for walking me through this... :)

---

### Post by Victormd on 2011-03-08
Could [this]("https://patchwork.kernel.org/patch/102502/") be the source and solution to the errors when I compile V4L??

EDIT: Guess not, tried it and still received an error when compiling...

---

### Post by Victormd on 2011-03-08
Should I do a fresh install of 10.04 or am I in for the same issues??
EDIT: downgraded to 10.04 and was able to compile. However, I now get this from dmesg:
> [   10.975799] saa7164 driver loaded
[   10.975837] saa7164 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.975985] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   10.975991] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe400000
[   10.975997] saa7164 0000:02:00.0: setting latency timer to 64
[   11.144388] saa7164_downloadfirmware() no first image
[   11.144433] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   11.144437] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   11.502800] saa7164_downloadfirmware() firmware read 4038864 bytes.
[   11.502802] saa7164_downloadfirmware() firmware loaded.
[   11.502809] saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
[   11.502815] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.502816] saa7164_downloadfirmware() BSLSize = 0x0
[   11.502817] saa7164_downloadfirmware() Reserved = 0x0
[   11.502819] saa7164_downloadfirmware() Version = 0x1d1c
[   18.376031] saa7164_downloadimage() Image downloaded, booting...
[   18.480029] saa7164_downloadimage() Image booted successfully.
[   20.612030] saa7164_downloadimage() Image downloaded, booting...
[   22.276436] saa7164_downloadimage() Image booted successfully.
[   22.313467] tveeprom 3-0000: audio processor is SAA7164 (idx 43)
[   22.313469] tveeprom 3-0000: decoder processor is SAA7164 (idx 40)
[   22.313472] saa7164[0]: Hauppauge eeprom: model=88061
[   22.599625] saa7164_api_i2c_read() error, ret(2) = 0x13
[   22.599698] saa7164_dvb_register() Frontend initialization failed
[   22.599700] saa7164_initdev() Failed to register dvb adapters on porta
[   22.830952] saa7164_api_i2c_read() error, ret(2) = 0x13
[   22.831025] saa7164_dvb_register() Frontend initialization failed
[   22.831026] saa7164_initdev() Failed to register dvb adapters on portb

---

### Post by Victormd on 2011-03-10
Ok, so after a lot of wasted time and messing around I decided to check the card itself, formated my comp. and installed Windows XP (to test the same HW setup) and what do you know, the card was DOA!!! sent it back to Amazon... let's see what happens...

---

### Post by nh79 on 2011-03-21
I seem to be having the same problems with the HVR-2200.

I am trying to install it on a new machine running Mythbuntu.

At the moment I have downloaded the firmware and copied it to /lib/firmware.
Then have used the "options saa7164 card=4" in a modprobe configuration file. This options gets further through the loading than the others.

Building either saa7164-dev or saa7164-stable fails with errors at the "tuner-xc2028.0" file. So I have not completed the make or make install steps.

The output of dmesg is failing at saa7164_api_i2c_read()
> 
dmesg |grep saa7164
[   12.405836] saa7164 driver loaded
[   12.405931] saa7164 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.413153] CORE saa7164[0]: subsystem: 0070:8953, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   12.413173] saa7164[0]/0: found at 0000:0b:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfbc00000
[   12.413189] saa7164 0000:0b:00.0: setting latency timer to 64
[   12.580043] saa7164_downloadfirmware() no first image
[   12.580115] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.753282] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   12.753291] saa7164_downloadfirmware() firmware loaded.
[   12.753324] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   12.753336] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.753342] saa7164_downloadfirmware() BSLSize = 0x0
[   12.753348] saa7164_downloadfirmware() Reserved = 0x0
[   12.753354] saa7164_downloadfirmware() Version = 0x51cc1
[   19.616020] saa7164_downloadimage() Image downloaded, booting...
[   19.720026] saa7164_downloadimage() Image booted successfully.
[   21.860018] saa7164_downloadimage() Image downloaded, booting...
[   23.528028] saa7164_downloadimage() Image booted successfully.
[   23.547444] saa7164_api_i2c_read() error, ret(1) = 0x13
[   23.629837] saa7164_api_i2c_read() error, ret(2) = 0x13
[   23.630172] saa7164_dvb_register() Frontend initialization failed
[   23.630228] saa7164_initdev() Failed to register dvb adapters on porta
[   23.631227] saa7164_api_i2c_read() error, ret(1) = 0x13
[   23.631548] saa7164_dvb_register() Frontend initialization failed
[   23.631603] saa7164_initdev() Failed to register dvb adapters on portb
So my questions are-

1. Should I try using the newer firmware 1.0.3-3? If so, do I need to rename the file or change the card=? option for modprobe.

2. Would it be better to try to get one of the saa1764 source version to build and install? Has anyone solved the errors that Victormd and I experience when building?

I tried the card in a Windows XP machine at work and it installed with no problems. I lack the appropriate software to test it and have no ariel connection however it appears to be working in the device manager. So I think I can rule out a hardware problem.

---

### Post by Victormd on 2011-03-22
> 1. Should I try using the newer firmware 1.0.3-3?
That's the version I tried - I deleted the previous versions in the folder. Not sure about the modprobe setting, I didn't go through any of that. I sent my card back and replaced my old HVR-1600 with another 1600 and, since I formatted my mythbox, all I had to do was add the firmware to /lib/firmware, reboot and the card was detected. This is what I was expecting from the HVR-2250.

I talked to Steven Toth and this was his response:
> The card isn't being detected correctly by the driver. Card type 7
probably isn't the right profile for your hardware. Each card that
Hauppauge ship I own and check personally. When I know the card works
I add support in the driver tree and push the patches to
kernellabs.com (then upstream).

No amount of poking and guessing is going to help you. No amount of
re-installing 10.10 will help. Either Hauppauge changed the card
recently or the tree is broken and I'd need to patch it. Either is
possible although I suspect the former.

So for your second question, if it's not working with the ubuntu driver, I'd try the kernellabs.com version. If that doesn't work, check Steven's site for more info.

---

### Post by nh79 on 2011-03-23
Thanks for the tips but it didn't fix the problems.

Without being able to build the driver the kernel still searched for the old firmware file which does not work with rev 81 of the saa7164.

I guess I need to wait until Steven Toth of someone else gets there hands on the updated card and makes it work.

I installed a trial of Windows 7 with media center on the machine and everything works well. Maybe the easiest solutions is to give up on MythTV and cough up for a windows license.

---

### Post by Victormd on 2011-03-23
> Without being able to build the driver the kernel still searched for the old firmware file which does not work with rev 81 of the saa7164.
Why couldn't you build the driver? I don't know that the driver is what specifies the firmware to use - it should search for the latest version in /lib/firmware. The reason I say this is because Ubuntu comes with the driver for the HVR-2200 - I have some links that I used to try to get it working - I'll check my bookmarks when I get home and I'll post them here for you to try them out.

I Wouldn't go with Windows Media Center - I've tried both and MythTV is just so much more versatile the WMC. I feel your pain in trying to get everything working, been there, but once you do, you'll appreciate the effort.

---

### Post by ronbus on 2011-03-30
I built the driver using the old version of the firmware and an old kernel and it took me a while to figure out I needed to do a "make distclean" before running the make again so it built for the updated kernel and with the new firmware.  While that got the new correct firmware loaded, it didn't solve my issue with the saa7164_api_i2c_read() errors.

I get the lockups even when I'm only watching live TV on a single tuner.  I haven't turned off the EIT, but I'm not sure that would solve my problem.  I  do have an AMD CPU and an on-board ATI video card.  The card seems to work perfectly until I get the lockups.

I'm thinking of creating a cron job to see if the i2c_read() errors have started every minute and have it unload and reload the kernel modules.  Does anyone know if that would work?

---

### Post by ronbus on 2011-03-31
Unloading and reloading the saa7164 module didn't seem to work.  I was hoping it would be as simple as

```
sudo rmmod saa7164
sudo modprobe saa7164
```

but it "Failed to register dvb adapters on porta".

Maybe I need to provide some different options to modprobe to force it to load the firmware again.  I'll keep looking.

---

### Post by Ubu_Fester on 2011-12-06
I have three tuners: HVR-1600 (single) and HVR-2250 (dual).  My HVR-2250 (with dual tuners) has been working fine for the last 10 months.  I used Lowsky's instructions -- which worked great.  Last couple of weeks, anytime I record from the 2250, the recorded program looks like it recorded, but is (blank).

Typing dmesg, I get the following (portion of output):

[HTML]dmesg | grep --max-count=20 saa7164
081] saa7164_api_i2c_read() error, ret(1) = 0xc
[292554.216094] saa7164_cmd_send() No free sequences
[292554.216099] saa7164_api_i2c_read() error, ret(1) = 0xc
[292554.216112] saa7164_cmd_send() No free sequences
[292554.216117] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216131] saa7164_cmd_send() No free sequences
[292554.216136] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216149] saa7164_cmd_send() No free sequences
[292554.216153] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216169] saa7164_cmd_send() No free sequences
[/HTML]From lspci, I get:
[HTML]03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)[/HTML]
Is it possible that an automatic update messed with my settings?  How can I get my 2250 working normally again?

I'm on ubuntu 10.10 and mythtv 0.23.1
Thanks in advance!

---

### Post by Ubu_Fester on 2011-12-07
Sorry, false alarm!!  I rebooted and looks like the 2250 tuner is back up and running fine on my HTPC.

Ubu Fester:)

---

### Post by vidtek on 2012-03-04
> **Ubu_Fester said:**
> I have three tuners: HVR-1600 (single) and HVR-2250 (dual).  My HVR-2250 (with dual tuners) has been working fine for the last 10 months.  I used Lowsky's instructions -- which worked great.  Last couple of weeks, anytime I record from the 2250, the recorded program looks like it recorded, but is (blank).

Typing dmesg, I get the following (portion of output):

[HTML]dmesg | grep --max-count=20 saa7164
081] saa7164_api_i2c_read() error, ret(1) = 0xc
[292554.216094] saa7164_cmd_send() No free sequences
[292554.216099] saa7164_api_i2c_read() error, ret(1) = 0xc
[292554.216112] saa7164_cmd_send() No free sequences
[292554.216117] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216131] saa7164_cmd_send() No free sequences
[292554.216136] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216149] saa7164_cmd_send() No free sequences
[292554.216153] saa7164_api_i2c_write() error, ret(1) = 0xc
[292554.216169] saa7164_cmd_send() No free sequences
[/HTML]From lspci, I get:
[HTML]03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)[/HTML]
Is it possible that an automatic update messed with my settings?  How can I get my 2250 working normally again?

I'm on ubuntu 10.10 and mythtv 0.23.1


Thanks in advance!

Guys-

One thing I've learned over the last 5 years messing about with linux and Mythtv is to DISABLE ALL AUTO-UPDATES.

Sorry for the shout, but once you get your B/E and F/E working leave them alone! 
Tony

---

