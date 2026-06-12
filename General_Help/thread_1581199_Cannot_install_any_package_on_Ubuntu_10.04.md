---
title: "Cannot install any package on Ubuntu 10.04"
date: 2010-09-24
forum: General Help
---

### Post by lyuba on 2010-09-24
The problem emerged when I started to make the internal microphone and external speakers work ([http://ubuntuforums.org/showthread.php?t=1575993](http://ubuntuforums.org/showthread.php?t=1575993)).

In either kernel 2.6.32-24 or 2.6.35-15 - cannot install any package with apt-get.

Here is the error I get when installing just anything [http://pastie.org/1179707](http://pastie.org/1179707)

Basically, here is it:

```
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3620.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxslt1-dev (1.1.26-1ubuntu1) ...
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Appreciate the ideas on how to help this sooo much!

---

### Post by andrewthomas on 2010-09-24
> **lyuba said:**
> 
```
ERROR: Build failed. Please review the build log at **/tmp/alsa-driver-linuxant.3620.log**
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxslt1-dev (1.1.26-1ubuntu1) ...
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What does the log file say?  I would just uninstall the offending package and try again.

---

### Post by lyuba on 2010-09-25
Thank you for your answer, it worked! I still have the sound problems, but at least it doesn't block the other work  :)

---

### Post by rtmmina on 2011-02-08
> **andrewthomas said:**
> What does the log file say?  I would just uninstall the offending package and try again.

I have the same problem, and I don't have enough experience in finding the offending packages, here is my log file
===========================
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
make -C ioctl32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make -C oss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make -C seq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make -C oss mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make -C l3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make -C other mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
make -C mpu401 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make -C opl3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make -C opl4 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make -C pcsp mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make -C ad1816a mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make -C ad1848 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make -C cs423x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make -C es1688 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make -C gus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make -C msnd mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make -C opti9xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make -C sb mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make -C wavefront mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make -C wss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make -C emux mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
make -C ac97 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make -C ali5451 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make -C asihpi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make -C au88x0 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make -C aw2 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make -C ca0106 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make -C cs46xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make -C cs5535audio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make -C echoaudio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make -C emu10k1 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make -C hda mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make -C ice1712 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make -C korg1212 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make -C mixart mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make -C nm256 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make -C oxygen mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make -C pcxhr mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make -C pdplus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make -C riptide mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make -C rme9652 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make -C trident mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make -C vx222 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make -C ymfpci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make -C core mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make -C fabrics mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make -C soundbus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make -C i2sbus mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make -C atmel mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/atmel'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/atmel'
make -C au1x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make -C blackfin mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make -C davinci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make -C fsl mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make -C omap mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make -C pxa mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make -C s3c24xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make -C sh mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
make -C caiaq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make -C usx2y mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make -C pdaudiocf mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
rm -f *.orig *.rej *~ .#*
rm -f linux/* asm/* media/*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/include'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/test'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *.orig *.rej *~ .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.32-28-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.32-28-generic
checking for GCC version... ./configure: eval: line 5023: syntax error near unexpected token `)'
./configure: eval: line 5023: `my_compiler_version=4.4.3-4ubuntu5)'
./configure: line 5023: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/2.6.32-28-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for usb_endpoint_dir_in and related functions... yes
checking for usb_endpoint_xfer_control... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for fmode_t... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.19
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for bool... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -pvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.32-28-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hrtimer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_misc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/rawmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/wrappers.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc_driver.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/init.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/info.o
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_entry_prepare’:
/usr/lib/alsa-driver-linuxant/acore/info.c:161: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_register’:
/usr/lib/alsa-driver-linuxant/acore/info.c:1020: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/info.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [compile] Error 2
==========================
Would help finding such error, also how to trace this kind of problems?
Thanks,

-Ramez

---

