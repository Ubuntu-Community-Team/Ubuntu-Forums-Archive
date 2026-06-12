---
title: "How to remove an entry from the GRUB 2 menu?"
date: 2009-12-23
forum: General Help
---

### Post by Daan on 2009-12-23
Hi all,

I want to remove an entry for Windows Vista (actually for HP_RECOVERY) from my GRUB 2 menu in Ubuntu 9.10. In the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") elsewhere on these forums I read that I then need to remove a file or part of a file in /etc/grub.d . However, the only file there that contains the text "Windows" is a rather complicated bit of code that seems to be designed to automatically detect OS's.

```
root@schmauck:/etc/grub.d# ls
00_header      05_debian_theme  20_memtest86+  40_custom
00_header.bak  10_linux         30_os-prober   README
root@schmauck:/etc/grub.d# grep -li windows *
30_os-prober
```

How do I remove an entry?

---

### Post by wilee-nilee on 2009-12-23
Have you upgraded your windows set up and the HP recovery is not relevant? A little more of a explanation might help.

---

### Post by 73ckn797 on 2009-12-23
If you have eliminated Windows or upgraded you may need to open a terminal and enter:
```
sudo update-grub2
```

I believe that would make any changes needed.

---

### Post by Daan on 2009-12-24
Hi,

Thanks for your responses.

I installed Ubuntu as soon as I got my new laptop. The installer gave me a GRUB menu with two entries for "Vista": one on sda1, where Windows actually is, and one for sda3, a partition labeled "HP_TOOLS". I want to remove this last entry, because on my previous HP laptop there were also additional entries for Vista in the GRUB menu, but choosing one of them resulted in GRUB being skipped at next boot, and the system entering an infinite loop of reboots without actually entering any OS as I know them. So I want to remove the entry for sda3, if there is an easy way.

```
root@schmauck:/home/daan# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
done
root@schmauck:/home/daan#
```

---

### Post by Leppie on 2009-12-24
backup your current 30_os-prober and open it with an editor:
```
$sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &
```

search for this section in the file:
> for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

add this after this section:
```
# Added to remove Windows Recovery
if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda3" ] ; then
continue
fi
# End Added
```

save and run:
```
$sudo update-grub
```

NOTE: you may have to check the exact menu entry and amend it accordingly in the to be added piece of code:
```
$cat /boot/grub/grub.cfg | grep Vista
```

---

### Post by Daan on 2009-12-25
Thanks, that is very useful. I have followed your directions, and now

```
root@schmauck:/etc/grub.d# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
root@schmauck:/etc/grub.d#
```

:-)

---

### Post by Leppie on 2009-12-25
you're welcome
fijne feestdagen :)

---

### Post by robfish on 2011-03-06
Thanks from me too. I had the same problem with an Asus laptop and this fix worked a treat.

---

### Post by mr_sparxx on 2011-05-26
Just the same as robfish. Thanks a lot, mate!

---

