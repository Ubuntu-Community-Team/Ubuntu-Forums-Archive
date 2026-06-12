---
title: "Grub2 configuration in Webmin (or I need install a new webmin module?)"
date: 2009-11-23
forum: General Help
---

### Post by Patagon on 2009-11-23
Hello

**I need the "Path to grub executable" in the webmin configuration**


I have this message from webmin:
The GRUB executable  was not found on your system. Maybe GRUB is not installed, or the module configuration is incorrect.

*I have a one hdd with 3 partitions (2 ext4):*
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4053    32555691   83  Linux
/dev/sda2            4054       90715   696112515   83  Linux
/dev/sda3           90716       91201     3903795   82  Linux swap / Solaris


**My config is: (incomplete)**

*Configurable options*
Install GRUB on disk/partition: **(hd0)**	


*System configuration*
GRUB menu configuration file: **/boot/grub/grub.cfg** 	
Path to grub executable **???**	
File for device name mappings 	* Get from GRUB


> root@atlantis:/home/master# find / -iname "grub"
/etc/webmin/grub
/etc/default/grub
/boot/grub
/usr/lib/grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/share/recovery-mode/options/grub
/usr/share/webmin/grub
/usr/share/webmin/blue-theme/grub
/usr/share/webmin/caldera/grub



Bye and thanks :KS

---

### Post by rudger on 2009-12-05
After about an hour of digging around on this and coming across your post heres what I've found.

There will have to be a new/tweaked webmin module for GRUB2.

I finally found where you can add custom settings to GRUB2. It's /etc/grub.d/40_custom
The final config is generated from grub-mkconfig and tacks the 40_custom file on the tail of /boot/grub/grub.cfg

Seeing the 10_linux 30_os-prober files makes me think with GRUB 2 they try to find any available bootable OS on any mounted file system, at least thats best guest, I've not looked into it.

So yeah, with GRUB2 someone is going to need to create a new webmin module, I'm still mixed on whether GRUB2 is "better" in that the menu.lst is gone and with the scripting in the new "menu". It doesn't appear that the current 1.490 default GRUB module can handle it, and frankly I'm scared to let it try without webmin having any knowledge of GRUB2 at it's current release.

P.S. 
I'm not dual booting with GRUB2 yet, so I don't know where any Windows OSes would be configured, if it's the custom directory or if os-prober finds them.

---

### Post by s1c on 2012-01-05
Hello. I know its been a long time since this topic started but I wanted to give a more clear answer.
As rudger already suggested ,in order to configure the GRUB2 module inside Webmin you need to set it like that:

[B]GRUB menu configuration file:   /etc/grub.d/40_custom
or
[/B]**GRUB menu configuration file: **/etc/grub.d/05_debian_theme
[B]
[/B]**Path to grub executable:            /usr/sbin/grub-mkconfig**

---

### Post by oldos2er on 2012-01-05
And with that we'll put this thread back to sleep.

---

