---
title: "Burn Multiple Live CDs on one DVD"
date: 2009-10-31
forum: General Help
---

### Post by jadhav333 on 2009-10-31
I would like to burn multiple versions of Ubuntu live CDs/Installation CDs on to one DVD, such that on booting that DVD, it will present a menu of options to select one of the versions of Ubuntu and boot into it..

I know it can be done in MagicISO (windows program) via WINE for Windows Operating sytems as shown here..

[http://www.magiciso.com/tutorials/miso-create-multi-os-cd.htm]("http://www.magiciso.com/tutorials/miso-create-multi-os-cd.htm")

I am unable to apply the technique to Ubuntu as Ubuntu has different folder structure that Win Installation CDs..

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-10-31
1. Unpack all ISOs to /live
2. Make one /live/isolinux/isolinux.cfg for all kernels
3. Run: ```
# cd /live
# mkisofs -N -J -R -D -o /m_boot.iso -b /live/isolinux/isolinux.bin -c /live/boot.catalog -no-emul-boot -boot-load-size 4 -boot-info-table .
# qemu -cdrom /m_boot.iso -boot d
```

Also on the same page: [http://pcquest.ciol.com/content/enterprise/2005/105070101.asp](http://pcquest.ciol.com/content/enterprise/2005/105070101.asp)
Found this searching google... haven't tried it but hope it helps.

---

### Post by jadhav333 on 2009-10-31
Thanks SIN, the link you provided explains it all.. :)

---

