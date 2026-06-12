---
title: "strange package problem"
date: 2006-03-22
forum: General Help
---

### Post by redcell on 2006-03-22
Hi,

I've got a strange problem, whenever I want to install or remove a package with, adept, or with apt-get or with dpkg, I get the same error:

(Database inlezen ... dpkg: fout bij afhandelen van xmms-xmmplayer (--remove):
 bestandenlijst-bestand voor pakket `linux-image-2.6.12-9-386' bevat een lege bestandsnaam
Fouten gevonden tijdens behandelen van:
 xmms-xmmplayer
Afhandeling werd afgebroken omdat er te veel fouten waren.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I use Kubuntu in dutch so I will try to translate the error:

(Reading Database... dpkg: error processing xmms-xmmplayer (--remove):
filelist-file for package 'linux-image-2.6.12-9-386' contains an empty filename
Errors detected during processing:
 xmms-xmmplayer
Process terminated because of too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appreciated....

---

### Post by Barrakketh on 2006-03-22
Post the contents of /var/lib/dpkg/info/linux-image-2.6.12-9-386.list

---

### Post by redcell on 2006-03-22
thanks for the quick reply :)

Here you go:

/.
/boot
/boot/config-2.6.12-9-386
/boot/vmlinuz-2.6.12-9-386
/boot/abi-2.6.12-9-386
/boot/System.map-2.6.12-9-386
/usr
/usr/share
/usr/share/doc
/usr/share/doc/linux-image-2.6.12-9-386
/usr/share/doc/linux-image-2.6.12-9-386/Changes.gz
/usr/share/doc/linux-image-2.6.12-9-386/copyright
/usr/share/doc/linux-image-2.6.12-9-386/changelog.Debian.gz
/usr/share/doc/linux-image-2.6.12-9-386/LiloDefault.gz
/usr/share/doc/linux-image-2.6.12-9-386/debian.README.gz
/usr/share/doc/linux-image-2.6.12-9-386/Buildinfo
/usr/share/doc/linux-image-2.6.12-9-386/conf.vars.gz
/usr/share/doc/linux-image-2.6.12-9-386/buildinfo.gz
/lib
/lib/modules
/lib/modules/2.6.12-9-386
/lib/modules/2.6.12-9-386/kernel
/lib/modules/2.6.12-9-386/kernel/arch
/lib/modules/2.6.12-9-386/kernel/arch/i386
/lib/modules/2.6.12-9-386/kernel/arch/i386/crypto
/lib/modules/2.6.12-9-386/kernel/arch/i386/crypto/aes-i586.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/cpufreq-nforce2.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/gx-suspmod.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/longhaul.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/longrun.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k6.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-ich.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-lib.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpuid.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/microcode.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/msr.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/scx200.ko
/lib/modules/2.6.12-9-386/kernel/arch/i386/oprofile
/lib/modules/2.6.12-9-386/kernel/arch/i386/oprofile/oprofile.ko
/lib/modules/2.6.12-9-386/kernel/cluster
/lib/modules/2.6.12-9-386/kernel/cluster/cman
/lib/modules/2.6.12-9-386/kernel/cluster/cman/cman.ko
/lib/modules/2.6.12-9-386/kernel/cluster/cmirror
/lib/modules/2.6.12-9-386/kernel/cluster/cmirror/dm-cmirror.ko
/lib/modules/2.6.12-9-386/kernel/cluster/dlm
/lib/modules/2.6.12-9-386/kernel/cluster/dlm/dlm.ko
/lib/modules/2.6.12-9-386/kernel/crypto
/lib/modules/2.6.12-9-386/kernel/crypto/anubis.ko
/lib/modules/2.6.12-9-386/kernel/crypto/arc4.ko
/lib/modules/2.6.12-9-386/kernel/crypto/blowfish.ko
/lib/modules/2.6.12-9-386/kernel/crypto/cast5.ko
/lib/modules/2.6.12-9-386/kernel/crypto/cast6.ko
/lib/modules/2.6.12-9-386/kernel/crypto/crc32c.ko
/lib/modules/2.6.12-9-386/kernel/crypto/crypto_null.ko
/lib/modules/2.6.12-9-386/kernel/crypto/deflate.ko
/lib/modules/2.6.12-9-386/kernel/crypto/des.ko
/lib/modules/2.6.12-9-386/kernel/crypto/khazad.ko
/lib/modules/2.6.12-9-386/kernel/crypto/md4.ko
/lib/modules/2.6.12-9-386/kernel/crypto/michael_mic.ko
/lib/modules/2.6.12-9-386/kernel/crypto/serpent.ko
/lib/modules/2.6.12-9-386/kernel/crypto/sha1.ko
/lib/modules/2.6.12-9-386/kernel/crypto/sha256.ko
/lib/modules/2.6.12-9-386/kernel/crypto/sha512.ko
/lib/modules/2.6.12-9-386/kernel/crypto/tcrypt.ko
/lib/modules/2.6.12-9-386/kernel/crypto/tea.ko
/lib/modules/2.6.12-9-386/kernel/crypto/tgr192.ko
/lib/modules/2.6.12-9-386/kernel/crypto/twofish.ko
/lib/modules/2.6.12-9-386/kernel/crypto/wp512.ko
/lib/modules/2.6.12-9-386/kernel/drivers
/lib/modules/2.6.12-9-386/kernel/drivers/acpi
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/ac.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/asus_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/battery.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/button.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/container.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/dev_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/fan.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/hotkey.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/i2c-acpi-ec.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/ibm_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/pcc_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/processor.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/sony_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/tc1100-wmi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/thermal.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/toshiba_acpi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/acpi/video.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm
/lib/modules/2.6.12-9-386/kernel/drivers/atm/ambassador.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/atmtcp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/eni.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/firestream.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/fore_200e.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/he.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/horizon.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/idt77252.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/iphase.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/lanai.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/nicstar.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/suni.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/uPD98402.ko
/lib/modules/2.6.12-9-386/kernel/drivers/atm/zatm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/base
/lib/modules/2.6.12-9-386/kernel/drivers/base/firmware_class.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block
/lib/modules/2.6.12-9-386/kernel/drivers/block/DAC960.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/aoe
/lib/modules/2.6.12-9-386/kernel/drivers/block/aoe/aoe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/cciss.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/cloop.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/cpqarray.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/cryptoloop.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/floppy.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/gnbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/loop.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/nbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/aten.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/bpck.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/bpck6.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/comm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/dstr.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/epat.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/epia.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/fit2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/fit3.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/friq.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/frpw.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/kbic.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/ktti.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/on20.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/on26.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/paride.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/pcd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/pd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/pf.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/pg.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/paride/pt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/pktcdvd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/ps2esdi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/sx8.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/umem.ko
/lib/modules/2.6.12-9-386/kernel/drivers/block/xd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/bcm203x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/bfusb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/bluecard_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/bpa10x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/bt3c_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/btuart_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/dtl1_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/hci_uart.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/hci_usb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/bluetooth/hci_vhci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/aztcd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/cdrom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/cdu31a.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/cm206.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/gscd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/isp16.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/mcdx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/optcd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/sbpcd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/sjcd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cdrom/sonycd535.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/agpgart.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/ali-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/amd-k7-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/amd64-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/ati-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/efficeon-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/intel-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/sis-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/sworks-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/agp/via-agp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/applicom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/cyclades.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/drm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/i810.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/i830.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/i915.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/mga.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/r128.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/radeon.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/sis.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/tdfx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/dtlk.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/epca.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/compressor
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/compressor/zft-compressor.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/lowlevel
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/lowlevel/ftape.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/zftape
/lib/modules/2.6.12-9-386/kernel/drivers/char/ftape/zftape/zftape.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/generic_serial.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/genrtc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/hangcheck-timer.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/hw_random.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/i8k.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ip2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ip2main.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi/ipmi_devintf.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi/ipmi_msghandler.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi/ipmi_poweroff.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi/ipmi_si.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ipmi/ipmi_watchdog.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/istallion.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/lp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/moxa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/mwave
/lib/modules/2.6.12-9-386/kernel/drivers/char/mwave/mwave.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/mxser.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/n_hdlc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/n_r3964.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/nvram.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/pcmcia
/lib/modules/2.6.12-9-386/kernel/drivers/char/pcmcia/synclink_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/ppdev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/raw.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/rio
/lib/modules/2.6.12-9-386/kernel/drivers/char/rio/rio.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/rocket.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/rtc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/scx200_gpio.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/sonypi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/stallion.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/sx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/synclink.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/synclinkmp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/tipar.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/toshiba.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/tpm
/lib/modules/2.6.12-9-386/kernel/drivers/char/tpm/tpm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/tpm/tpm_atmel.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/tpm/tpm_nsc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/acquirewdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/advantechwdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/alim1535_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/alim7101_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/cpu5wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/eurotechwdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/i8xx_tco.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/ib700wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/machzwd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/mixcomwd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/pcwd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/pcwd_pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/pcwd_usb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/sbc60xxwdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/sc1200wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/sc520_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/scx200_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/softdog.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/w83627hf_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/w83877f_wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/wafer5823wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/wdt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/char/watchdog/wdt_pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/cpufreq_conservative.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/cpufreq_ondemand.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/cpufreq_powersave.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/cpufreq_stats.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/cpufreq_userspace.ko
/lib/modules/2.6.12-9-386/kernel/drivers/cpufreq/freq_table.ko
/lib/modules/2.6.12-9-386/kernel/drivers/crypto
/lib/modules/2.6.12-9-386/kernel/drivers/crypto/padlock.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/algos
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/algos/i2c-algo-bit.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/algos/i2c-algo-pca.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/algos/i2c-algo-pcf.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-ali1535.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-ali1563.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-ali15x3.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-amd756-s4882.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-amd756.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-amd8111.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-elektor.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-i801.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-i810.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-isa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-nforce2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-parport-light.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-parport.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-pca-isa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-piix4.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-prosavage.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-savage4.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-sis5595.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-sis630.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-sis96x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-stub.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-via.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-viapro.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/i2c-voodoo3.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/scx200_acb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/busses/scx200_i2c.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/adm1021.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/adm1025.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/adm1026.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/adm1031.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/asb100.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/ds1337.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/ds1621.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/eeprom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/fscher.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/fscpos.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/gl518sm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/gl520sm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/it87.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm63.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm75.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm77.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm78.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm80.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm83.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm85.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm87.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm90.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/lm92.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/max1619.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/pc87360.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/pcf8574.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/pcf8591.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/rtc8564.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/sis5595.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/smsc47b397.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/smsc47m1.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/via686a.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/w83627hf.ko

---

### Post by redcell on 2006-03-22
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/w83781d.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/chips/w83l785ts.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/i2c-core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/i2c-dev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/i2c/i2c-sensor.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-disk.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-floppy.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-generic.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-pnp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-tape.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/legacy
/lib/modules/2.6.12-9-386/kernel/drivers/ide/legacy/ide-cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/aec62xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/alim15x3.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/amd74xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/atiixp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/cmd64x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/cs5520.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/cs5530.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/cy82c693.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/generic.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/hpt34x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/hpt366.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/ns87415.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/opti621.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/pdc202xx_new.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/pdc202xx_old.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/piix.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/rz1000.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/sc1200.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/serverworks.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/siimage.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/sis5513.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/slc90e66.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/triflex.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/trm290.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/via82cxxx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/amdtp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/cmp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/core
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/core/ib_core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/core/ib_mad.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/core/ib_sa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/core/ib_umad.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/hw
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/hw/mthca
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/hw/mthca/ib_mthca.ko
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/ulp
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/ulp/ipoib
/lib/modules/2.6.12-9-386/kernel/drivers/infiniband/ulp/ipoib/ib_ipoib.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input
/lib/modules/2.6.12-9-386/kernel/drivers/input/cpad
/lib/modules/2.6.12-9-386/kernel/drivers/input/cpad/cpad.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/evbug.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/evdev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/cs461x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/emu10k1-gp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/fm801-gp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/gameport.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/lightning.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/ns558.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/gameport/vortex.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joydev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/a3d.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/adi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/analog.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/cobra.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/db9.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/gamecon.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/gf2k.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/grip.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/grip_mp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/guillemot.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/iforce
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/iforce/iforce.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/interact.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/joydump.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/magellan.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/sidewinder.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/spaceball.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/spaceorb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/stinger.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/tmdc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/turbografx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/twidjoy.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/joystick/warrior.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/keyboard
/lib/modules/2.6.12-9-386/kernel/drivers/input/keyboard/lkkbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/keyboard/newtonkbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/keyboard/sunkbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/keyboard/xtkbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/misc
/lib/modules/2.6.12-9-386/kernel/drivers/input/misc/acerhk.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/misc/pcspkr.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/misc/uinput.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/inport.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/logibm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/pc110pad.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/psmouse.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/sermouse.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mouse/vsxxxaa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/mousedev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio/ct82c710.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio/parkbd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio/pcips2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio/serio_raw.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/serio/serport.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/touchscreen
/lib/modules/2.6.12-9-386/kernel/drivers/input/touchscreen/elo.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/touchscreen/gunze.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/touchscreen/mk712.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/touchscreen/mtouch.ko
/lib/modules/2.6.12-9-386/kernel/drivers/input/tsdev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/act2000
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/act2000/act2000.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/capi
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/capi/capi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/capi/capidrv.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/capi/capifs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/capi/kernelcapi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/divert
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/divert/dss1_divert.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/avm_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/b1.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/b1dma.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/b1isa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/b1pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/b1pcmcia.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/c4.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/t1isa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/avm/t1pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon/diva_idi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon/diva_mnt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon/divacapi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon/divadidd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hardware/eicon/divas.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/avma1_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/elsa_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hfc4s8s_l1.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hfc_usb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hisax.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hisax_fcpcipnp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hisax_isac.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/hisax_st5481.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/isdnhdlc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/sedlbauer_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hisax/teles_cs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hysdn
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/hysdn/hysdn.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/i4l
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/i4l/isdn.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/i4l/isdn_bsdcomp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/icn
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/icn/icn.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/isdnloop
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/isdnloop/isdnloop.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/pcbit
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/pcbit/pcbit.ko
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/sc
/lib/modules/2.6.12-9-386/kernel/drivers/isdn/sc/sc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-crypt.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-emc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-mirror.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-mod.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-round-robin.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-snapshot.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/dm-zero.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/faulty.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/linear.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/md.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/multipath.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/raid0.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/raid1.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/raid10.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/raid5.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/raid6.ko
/lib/modules/2.6.12-9-386/kernel/drivers/md/xor.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media
/lib/modules/2.6.12-9-386/kernel/drivers/media/common
/lib/modules/2.6.12-9-386/kernel/drivers/media/common/ir-common.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/common/saa7146.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/common/saa7146_vv.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/b2c2
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/b2c2/b2c2-flexcop-pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/b2c2/b2c2-flexcop-usb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/b2c2/b2c2-flexcop.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/b2c2/skystar2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/bt8xx
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/bt8xx/bt878.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/bt8xx/dst.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/bt8xx/dst_ca.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/bt8xx/dvb-bt8xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/cinergyT2
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/cinergyT2/cinergyT2.ko

---

### Post by redcell on 2006-03-22
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/dibusb
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/dibusb/dvb-dibusb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/dvb-core
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/dvb-core/dvb-core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/at76c651.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/cx22700.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/cx22702.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/cx24110.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/dib3000-common.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/dib3000mb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/dib3000mc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/dvb-pll.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/l64781.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/mt312.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/mt352.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/nxt2002.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/nxt6000.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/or51132.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/or51211.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/sp8870.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/sp887x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/stv0297.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/stv0299.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/tda10021.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/tda1004x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/tda8083.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/tda80xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/ves1820.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/frontends/ves1x93.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/budget-av.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/budget-ci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/budget-core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/budget-patch.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/budget.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/dvb-ttpci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttpci/ttpci-eeprom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttusb-budget
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttusb-dec
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttusb-dec/ttusb_dec.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/dvb/ttusb-dec/ttusbdecfe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/em8300
/lib/modules/2.6.12-9-386/kernel/drivers/media/em8300/adv717x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/em8300/bt865.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/em8300/em8300.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/miropcm20-rds.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/miropcm20.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-aimslab.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-aztech.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-cadet.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-gemtek-pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-gemtek.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-maestro.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-maxiradio.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-rtrack2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-sf16fmi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-sf16fmr2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-terratec.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-trust.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-typhoon.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/radio/radio-zoltrix.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/adv7170.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/adv7175.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/bt856.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/btcx-risc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/bttv.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/bw-qcam.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/c-qcam.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cpia.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cpia_pp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cpia_usb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx88-blackbird.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx88-dvb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx8800.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx8802.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx88xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/dpc7146.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/hexium_gemini.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/hexium_orion.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/ir-kbd-gpio.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/ir-kbd-i2c.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/meye.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/msp3400.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/mxb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/ovcamchip
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/ovcamchip/ovcamchip.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/pms.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa5246a.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa5249.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7110.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7111.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7114.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7134
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/saa7185.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/stradis.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda7432.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda9840.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda9875.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda9887.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tea6415c.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tea6420.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tuner-3036.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tuner.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tvaudio.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tveeprom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/tvmixer.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/v4l1-compat.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/v4l2-common.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/video-buf-dvb.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/video-buf.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/videocodec.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/videodev.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/vpx3220.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/w9966.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/zr36016.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/zr36050.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/zr36060.ko
/lib/modules/2.6.12-9-386/kernel/drivers/media/video/zr36067.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message
/lib/modules/2.6.12-9-386/kernel/drivers/message/fusion
/lib/modules/2.6.12-9-386/kernel/drivers/message/fusion/mptbase.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/fusion/mptctl.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/fusion/mptlan.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/fusion/mptscsih.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o/i2o_block.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o/i2o_config.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o/i2o_core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o/i2o_proc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/message/i2o/i2o_scsi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/misc
/lib/modules/2.6.12-9-386/kernel/drivers/misc/av5100.ko
/lib/modules/2.6.12-9-386/kernel/drivers/misc/ibmasm
/lib/modules/2.6.12-9-386/kernel/drivers/misc/ibmasm/ibmasm.ko
/lib/modules/2.6.12-9-386/kernel/drivers/misc/pbe5.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mmc
/lib/modules/2.6.12-9-386/kernel/drivers/mmc/mmc_block.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mmc/mmc_core.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mmc/wbsd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/cfi_cmdset_0001.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/cfi_cmdset_0002.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/cfi_cmdset_0020.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/cfi_probe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/cfi_util.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/chipreg.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/gen_probe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/jedec_probe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/map_absent.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/map_ram.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/chips/map_rom.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/blkmtd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/block2mtd.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/doc2000.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/doc2001.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/doc2001plus.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/docecc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/docprobe.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/mtdram.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/phram.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/pmc551.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/devices/slram.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/ftl.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/inftl.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/dilnetpc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/elan-104nc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/map_funcs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/netsc520.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/nettel.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/physmap.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/pnc2000.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/sbc_gxx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/sc520cdp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtd_blkdevs.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdblock.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdblock_ro.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdchar.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdconcat.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdcore.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/mtdpart.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nand
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nand/diskonchip.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nand/nand.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nand/nand_ecc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nand/nand_ids.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/nftl.ko
/lib/modules/2.6.12-9-386/kernel/drivers/mtd/redboot.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c501.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c503.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c505.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c507.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c509.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c515.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c523.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c527.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/3c59x.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/8139too.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/82596.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/8390.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/ac3200.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/amd8111e.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/appletalk
/lib/modules/2.6.12-9-386/kernel/drivers/net/appletalk/cops.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/appletalk/ipddp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/appletalk/ltpc.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/arc-rawmode.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/arc-rimi.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/arcnet.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/capmode.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/com20020-isa.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/com20020-pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/com20020.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/com90io.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/com90xx.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/rfc1051.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/arcnet/rfc1201.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/at1700.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/atp.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/b44.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/bnx2.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/bonding

---

### Post by redcell on 2006-03-22
/lib/modules/2.6.1  ý
   [
 Q  ý 
2
5
/  .
j X [ T 2  	 } ýý^   ýM  & s 
  5   ? e ý    o ý!   ýý q   k ? ' ` Q v * ý:   ý  d  ýýýý+ ýýý  u ; 3   % ý    X  : Y ýK 	;
ý     y ý ýý	 ?ý&iý ý6ýdýýýýýpG C ýh ý|  ýý ý   U  ý x k ? , " ý   ýý   ý    ý  8 Q  ýý ýx y ýý/ 		(	7    h  
   ýý 
 % [ f ý  ýO ý
 \  
 ý ýý 
ý 
v

ý@	ý	-	)    ýýq  d 2  ) ý   F    Ry ýý2Rý A$?ýwýýýc|ý	|KýýIcýX  +  f   ý$ ý  R  ýP ý  ý ýýZ NB   ý ýW ýý X:ýý +3ý/lh ýKýý  `  ]ý)RýýýXýýýý1ýýýd>}!S0ýaýý   ý J  %  M  	ý 	j
F
ý9  

ýK

ý	=	 		x	   o	ý #  ~ }  /  ý ý  8 ýN   ý 	  ý	  ; ý ýý@  ý> ýý) H m ~{ýýý/ {  7  
 s     ýC ý    A . v  g C ý m k   X ý1  J t  ý ý I 3 - 7 / ý;  @      6 E ý| X y ! # U     r ý5 H ý & 9 ý)raýýýY

`^ ýNýýQýý#> )  t C ýý@    w w ^ ý  J ý1>5> 6#  J v  ýýr >    ý|    T ý    ýýP ýý[    ? ý0  ý       2 {  ý W  ýw  !ý ýeAýýýaý'~ýý(ýGýý #ýýý7ýýyýýýýýýý: T < ýQý  >ýýýh xnVýpxýýý44  	qýýýýýýýýý	ýýýýýýýwýýý
ý Cýýýýbýýýýýýý ýýn qg ý O ýýýý   v 1  [ ý   - 	 	 - 4 r	
l ý 	ý ý C  ( D  + ] c ý  > ;
A

ýY

   { , ýý   ýýS _	 L A o t ýd n   ý Z 	J  ý*ý-]+{ ýP&ýý+ýý*ýýý
ý8ýýýjýUý~0[ ^ ýE %   ýQ   u   ;    ýýh  A
M j F  f W ýý    ý ýN

 
 
        ý    /  @  J ýI  K        3 * j ýý ýU    ýu X ý] ýýý{  7 d ý+ %  ý  0 ý L ý/  ýý W ýý   + ý   ý% w | ýo ý@ K   ý
 ý C _   b ýV ý9 ! ýýý, M  ý  p   J
: j  D Q n        u L ) H $ 5  ýýq  ? ý ýW   ýN T ýY   ý    , ý } ý ýP  ý}       vý ý         C 1 N ýo  ;   TR  B \ d ýý C ; D $   | . I  $     ýy ý/  e ý  O ý$ ým   ý  	F 
 	 0 ý
ýo		 \ ýn ým    	 E z ý) k 3 ýT ýýh + ýh O ~  0 " f   & ýa ý9 	ý 	M S  ýýL :   ý-   ýGý oýa>1ý ý  ý {ýýýý ý ýýýý dýýýýýýý ýýýý ýýýýýýýý |Kýs8ýgý=.ý FlýVý4ý]Rý) i;VWSý ý  / ý{ ý{.   LSý     ý  ^  ýD]Bý H #St ý~ý$ ..8G+m  ýCzýýýýý7}0Pýý7ýýýýýýýýýýýýýýýýnýýýýýýýýýýýýýýýDýýýýýýýýý ýýýýýýýýýýýýýýýýýýý5ýýýýý³ýýýýtýý ýýýýýý!ýýýýhýý ýýýýý ýý?ýýýýýýýýýýýýýý?ýDýýýýýýý ýýýýýýýýýýýý:ýýýýý7ýý{ýýsBýý ýýýýýmnlýMýýXýý ýýýýý>ýý ýýýýýý ýýýýýAýýýEýýýýýýýDýýýýýýýýýTýýýýnýýýýýýýýýýýýýýýýýýýýýýýýýýý{ýýýýýýýýýýýý ýýsý@ý  GýT ýJ @ýYýýyV ,  Fýa  @ýýý ýýýý/ýýl0ýý  : ýýýýýýýýýýýýý `U\Z_ýýýdX4ýIýýýzý8ýý ýýýýýýgýý býSýl@ýýk/Býý <ýý=ýýýýýýýýýýhý	PCX= oMu [ýýýýý>ýýýýýýýýýýýýýýýýý_ýýzýýýý(ýýýýýý ýý ýýSýýýýýý;'wý&W\ "ýýý2ý ]dkWýc ýýý P6  ýq}peý c60wOV    ý OX\aýý ^uý;Q{n 0  }W #g
,aý>ýýB>4 eýýýý  # ýýZýýý ýýýý                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               


The file is quite long so i have posted it in multiple replys

---

### Post by Barrakketh on 2006-03-22
Your file appears to be corrupt.  Do the following:

[list][*]Download [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-9-386_2.6.12-9.23_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-9-386_2.6.12-9.23_i386.deb).
[*]From the directory you downloaded it from, issue the following command:
```
dpkg -c linux-image-2.6.12-9-386_2.6.12-9.23_i386.deb | awk '{print $6}' > /var/lib/dpkg/info/linux-image-2.6.12-9-386.list
```[/list]

That should fix the problem.

---

### Post by redcell on 2006-03-23
Thanx verry much, that did fix the problem indeed :)

---

### Post by Barrakketh on 2006-03-23
[QUOTE=redcell]Thanx verry much, that did fix the problem indeed :)[/QUOTE]
You're welcome :)

---

