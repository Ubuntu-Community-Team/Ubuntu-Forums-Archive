---
title: "problem with grub"
date: 2009-11-07
forum: General Help
---

### Post by entilete on 2009-11-07
[B]I recently installed Ubuntu 9.10 and Windows Vista on my HDD (I also have Windows XP in another one, but I don't have it included in the boot menu).
the problem is I updated grub and then it added Windows XP to its menu and, when I try to run Windows Vista, it just doesn't work :S. I tried to fix it, but I couldn't.

here I give you some useful information:
windows XP is installed in sda
windows vista in /dev/sdb1
and ubuntu in /dev/sdb3[/B]
Disco /dev/sda: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd6fbd6fb

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14660   117756418+   7  HPFS/NTFS
/dev/sda2           14661       30400   126431550    f  W95 Ext'd (LBA)
/dev/sda5           14661       30400   126431518+   7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xc225c225

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       14996   120448000    7  HPFS/NTFS
/dev/sdb2           14997       15057      489982+   5  Extendida
/dev/sdb3           15058       19457    35343000   83  Linux
/dev/sdb5           14997       15057      489951   82  Linux swap / Solaris

**grub.cfg**
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
set menu_color_normal=white/black
set menu_color_highlight=black/white

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb3 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set fe188d39188cf247
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	chainloader +1
}

---

