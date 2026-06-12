---
title: "I can't install any pckage"
date: 2010-11-26
forum: General Help
---

### Post by aliirani on 2010-11-26
Hello all
I have a skit problem.
When i want install some deb package, bash sending this error:

```
Setting up alsa-driver-linuxant (1.0.20.3) ...
Building modules for the 2.6.32-21-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.1665.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
```Is there any idea for correct this problem?

---

### Post by sikander3786 on 2010-11-26
Please post the output of

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by Hippytaff on 2010-11-26
Also what does the log say
```

cat /tmp/alsa-driver-linuxant.1665.log

```

---

### Post by aliirani on 2010-11-26
```
ali@ali-desktop:~$ sudo apt-get install -f
[sudo] password for ali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up alsa-driver-linuxant (1.0.20.3) ...
Building modules for the 2.6.32-21-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.1474.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
 Errors were encountered while processing:
  alsa-driver-linuxant
  E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```

  ali@ali-desktop:~$ sudo dpkg --configure -a
  Setting up alsa-driver-linuxant (1.0.20.3) ...
  Building modules for the 2.6.32-21-generic kernel, please wait... done.
  ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.9814.log
  dpkg: error processing alsa-driver-linuxant (--configure):
   subprocess installed post-installation script returned error exit status 2
   Errors were encountered while processing:
    alsa-driver-linuxant
```

```
ali@ali-desktop:~$ cat /tmp/alsa-driver-linuxant.9814.log
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
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
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
checking for directory with kernel source... /lib/modules/2.6.32-21-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.32-21-generic
checking for GCC version... ./configure: eval: line 5073: syntax error near unexpected token `)'
./configure: eval: line 5073: `my_compiler_version=4.4.3-4ubuntu5)'
./configure: line 5073: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires
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
checking for directory to store kernel modules... /lib/modules/2.6.32-21-generic/kernel/sound
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
checking for kernel linux/gpio.h... yes
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
checking for hrtimer_get_expires... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
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
checking for driver version... 1.0.20
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
checking for builtin _Bool support... yes
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
        make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
        make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
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
                                                CC [M]  /usr/lib/alsa-driver-linuxant/acore/control.o
                                                  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc.o
                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/device.o
                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/isadma.o
                                                        CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound_oss.o
                                                          CC [M]  /usr/lib/alsa-driver-linuxant/acore/info_oss.o
                                                            CC [M]  /usr/lib/alsa-driver-linuxant/acore/vmaster.o
                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/jack.o
                                                                LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd.o
                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-hwdep.o
                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-timer.o
                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-hrtimer.o
                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-pcm.o
                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-page-alloc.o
                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-rawmidi.o
                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/mixer_oss.o
                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/pcm_oss.o
                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/pcm_plugin.o
                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/io.o
                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/copy.o
                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/linear.o
                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/mulaw.o
                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/route.o
                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/rate.o
                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/acore/oss/snd-mixer-oss.o
                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/acore/oss/snd-pcm-oss.o
                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_device.o
                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_dummy.o
                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi_emul.o
                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi_event.o
                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi.o
                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_virmidi.o
                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq.o
                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_lock.o
                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_clientmgr.o
                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_memory.o
                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_queue.o
                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_fifo.o
                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_prioq.o
                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_timer.o
                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_system.o
                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_ports.o
                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_info.o
                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq.o
                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-device.o
                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi-event.o
                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-dummy.o
                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-virmidi.o
                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi.o
                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi-emul.o
                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss.o
                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_init.o
                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_timer.o
                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_ioctl.o
                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_event.o
                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_rw.o
                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_synth.o
                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_midi.o
                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_readq.o
                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_writeq.o
                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/snd-seq-oss.o
                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/drivers/aloop.o
                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/drivers/dummy.o
                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mtpav.o
                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mts64.o
                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/portman2x4.o
                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/drivers/serial-u16550.o
                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/drivers/virmidi.o
                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-aloop.o
                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-dummy.o
                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-virmidi.o
                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-serial-u16550.o
                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-mtpav.o
                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-mts64.o
                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-portman2x4.o
                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/mpu401_uart.o
                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/mpu401.o
                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/snd-mpu401-uart.o
                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/snd-mpu401.o
                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_lib.o
                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_synth.o
                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_seq.o
                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_midi.o
                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_drums.o
                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_oss.o
                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/snd-opl3-lib.o
                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/snd-opl3-synth.o
                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_lib.o
                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_mixer.o
                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_proc.o
                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_seq.o
                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_synth.o
                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/yrw801.o
                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/snd-opl4-lib.o
                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/snd-opl4-synth.o
                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/drivers/pcsp/pcsp.o
                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/drivers/pcsp/pcsp_lib.o
                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/pcsp/pcsp_mixer.o
                                                                                                                                                                                                                                                  In file included from /usr/lib/alsa-driver-linuxant/drivers/pcsp/pcsp_mixer.c:2:
                                                                                                                                                                                                                                                  /usr/lib/alsa-driver-linuxant/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp_mixer.c: In function ‘pcsp_treble_info’:
                                                                                                                                                                                                                                                  /usr/lib/alsa-driver-linuxant/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp_mixer.c:54: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/drivers/pcsp/pcsp_input.o
                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/drivers/pcsp/snd-pcsp.o
                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_core.o
                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_hwdep.o
                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_pcm.o
                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_mixer.o
                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_cmd.o
                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_uer.o
                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/snd-vx-lib.o
                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/i2c/cs8427.o
                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/i2c/i2c.o
                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/i2c/tea6330t.o
                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-tea6330t.o
                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-i2c.o
                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-cs8427.o
                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4114.o
                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4117.o
                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4xxx-adda.o
                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/pt2258.o
                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/tea575x-tuner.o
                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4117.o
                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4xxx-adda.o
                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4114.o
                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-pt2258.o
                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-tea575x-tuner.o
                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/adlib.o
                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/als100.o
                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/azt2320.o
                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/cmi8330.o
                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/dt019x.o
                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/es18xx.o
                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opl3sa2.o
                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/sc6000.o
                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/sgalaxy.o
                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/sscape.o
                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-adlib.o
                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-als100.o
                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-azt2320.o
                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-cmi8330.o
                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-dt019x.o
                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-es18xx.o
                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-opl3sa2.o
                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sc6000.o
                                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sgalaxy.o
                                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sscape.o
                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/ad1816a.o
                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/ad1816a_lib.o
                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/snd-ad1816a.o
                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1848/ad1848.o
                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/ad1848/snd-ad1848.o
                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4231.o
                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4236.o
                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4236_lib.o
                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4231.o
                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4236.o
                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/es1688_lib.o
                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/es1688.o
                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/snd-es1688.o
                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/snd-es1688-lib.o
                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_main.o
                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_io.o
                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_irq.o
                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_timer.o
                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mem.o
                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mem_proc.o
                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_dram.o
                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_dma.o
                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_volume.o
                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_pcm.o
                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mixer.o
                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_uart.o
                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_reset.o
                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusclassic.o
                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusextreme.o
                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusmax.o
                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/interwave-stb.o
                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/interwave.o
                                                                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusclassic.o
                                                                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gus-lib.o
                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusmax.o
                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusextreme.o
                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-interwave.o
                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-interwave-stb.o
                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_classic.o
                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd.o
                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_midi.o
                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle_mixer.o
                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle.o
                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/snd-msnd-pinnacle.o
                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/snd-msnd-lib.o
                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/snd-msnd-classic.o
                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/miro.o
                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti92x-ad1848.o
                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti92x-cs4231.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti93x.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti92x-ad1848.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti92x-cs4231.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti93x.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-miro.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_synth.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_callback.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_patch.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_pcm.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/es968.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb_common.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb_mixer.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16_csp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16_main.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8_main.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8_midi.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sbawe.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb-common.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16-dsp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb8-dsp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb8.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sbawe.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-es968.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16-csp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-emu8000-synth.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_fx.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_synth.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_midi.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/snd-wavefront.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/isa/wss/wss_lib.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/isa/wss/snd-wss-lib.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/misc/ac97_bus.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/pci/ad1889.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/pci/als300.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/pci/als4000.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/pci/atiixp_modem.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/pci/atiixp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/pci/azt3328.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/pci/bt87x.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/pci/cmipci.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs4281.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs5530.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/pci/ens1370.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/pci/ak4531_codec.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ens1371.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/pci/es1938.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/pci/es1968.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/pci/fm801.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/pci/intel8x0.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/pci/intel8x0m.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/pci/maestro3.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme32.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme96.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/pci/sis7019.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/pci/sonicvibes.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/pci/via82xx_modem.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/pci/via82xx.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ad1889.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-als300.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-als4000.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-atiixp.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-atiixp-modem.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-azt3328.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-bt87x.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cmipci.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cs4281.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cs5530.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ens1370.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ens1371.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-es1938.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-es1968.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-fm801.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-intel8x0.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-intel8x0m.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-maestro3.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-rme32.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-rme96.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-sis7019.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-sonicvibes.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-via82xx.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-via82xx-modem.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_codec.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_pcm.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_proc.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/snd-ac97-codec.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/pci/ali5451/ali5451.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      LD [M]  /usr/lib/alsa-driver-linuxant/pci/ali5451/snd-ali5451.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/asihpi.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpioctl.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpimsginit.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpicmn.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpifunc.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpidebug.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpidspcd.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpios_linux_kernel.o
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      /usr/lib/alsa-driver-linuxant/pci/asihpi/hpios_linux_kernel.c: In function ‘HpiOs_DelayMicroSeconds’:
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      /usr/lib/alsa-driver-linuxant/pci/asihpi/hpios_linux_kernel.c:34: error: implicit declaration of function ‘schedule_timeout_uninterruptible’
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make[4]: *** [/usr/lib/alsa-driver-linuxant/pci/asihpi/hpios_linux_kernel.o] Error 1
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make[3]: *** [/usr/lib/alsa-driver-linuxant/pci/asihpi] Error 2
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make[2]: *** [/usr/lib/alsa-driver-linuxant/pci] Error 2
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      make: *** [compile] Error 2
```

---

### Post by sikander3786 on 2010-11-26
```
sudo apt-get install --reinstall alsa-driver-linuxant
```

If that is unsuccessful,

```
sudo apt-get remove --purge alsa-driver-linuxant
```

and then

```
sudo apt-get install alsa-driver-linuxant
```
Please keep on posting the outputs.

**Hippytaff** might come up with some other suggestion as well ;-)

---

### Post by Hippytaff on 2010-11-26
Maybe try
```

sudo apt-get dist-upgrade

```
 
then if it still doesn't work try installing the alsa module again

---

### Post by aliirani on 2010-11-27
> **sikander3786 said:**
> ```
sudo apt-get install --reinstall alsa-driver-linuxant
```If that is unsuccessful,

```
sudo apt-get remove --purge alsa-driver-linuxant
```and then

```
sudo apt-get install alsa-driver-linuxant

Please keep on posting the outputs.

**Hippytaff** might come up with some other suggestion as well ;-)[/QUOTE]
Thanks!
My problem is solved with this code:
[CODE]sudo apt-get remove --purge alsa-driver-linuxant
```
How doing "--purge" code?

---

### Post by Hippytaff on 2010-11-27
Looks as though you have removed the driver :-)

---

### Post by sikander3786 on 2010-11-27
> **Hippytaff said:**
> Looks as though you have removed the driver :-)
Reinstall?

```
sudo apt-get install alsa-driver-linuxant
```

---

### Post by aliirani on 2010-11-28
I wanted remove this driver:D

---

