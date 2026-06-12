---
title: "Unable to boot"
date: 2010-07-20
forum: General Help
---

### Post by seangee on 2010-07-20
Just returned from hols to find my server stuck after a reboot:
GRUB loading.
error: no such partition
grub rescue>

System is 9.10 server (64 bit) booting off a USB stick with 4 1Tb drives in RAID 5 and an external USB disk for backup. I have a backup USB stick and can't boot off that either (same results) so am assuming its not the boot disk.

All disks / partitions seem to check out ok. 
syslog shows nothing strange until it stopped at 

Jul 10 10:57:01 fileserver CRON[17203]: (root) CMD (ping -c 2 192.168.17.254 > /dev/null 2>&1)
(manual keepalive to external VPN server :D)

I booted off my NBR live CD and ran boot_info_script. Have attached the results. Nothing else strange in the logs. Last unattended upgrade was 2 days earlier - log also attached.

Afraid I don't know where to go next. Have temporarily attached the backup disk to my desktop and turned that into a SAMBA server but keen to get back quickly (and the server does other things too!!)

---

### Post by drs305 on 2010-07-20
Two disclaimers: I don't use RAID and I don't use servers...  ;-)

The boot info script shows that Grub is installed in both sda and sde. The sda grub points to sda1, which is merely an extended partition. At this point, I was going to tell you to make sure your BIOS is set to boot sde first.

Looking at sde, Grub looks at sde1 and your files appear to exist in that location. However, looking at the menu entries, they point to your kernels on *sdf* and not *sde*:
> 
menuentry "Ubuntu, Linux 2.6.31-22-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-22-server **root=/dev/sdf1** ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-server
}

Try editing the menu at boot by holding down the SHIFT key (assuming you are booting to sde).

Highlight the first entry, then press "e" to get into the edit mode.

Cursor to the "root=/dev/sdf1" and change it to "root=/dev/sde1".

CTRL-x to boot.

If it boots, run "sudo update-grub" and see if /boot/grub/grub.cfg corrects the entries to properly reflect the location of your kernels.

---

### Post by seangee on 2010-07-20
Arghh must try harder. Was so convinced it was system I missed the obvious - thanks for the clues

> At this point, I was going to tell you to make sure your BIOS is set to boot sde first.
...
 (assuming you are booting to sde).I was assuming that too because that's the way I configured my bios.:rolleyes: Turns out the bios had reset itself and was indeed trying to boot sda.

Thankfully there's nowt wrong after all...

---

