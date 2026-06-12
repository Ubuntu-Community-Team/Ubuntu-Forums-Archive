---
title: "why is my font so messy and why win7 appears twice in grub"
date: 2011-04-03
forum: General Help
---

### Post by elliotn on 2011-04-03
hi guys plz see the attached screenshot.

My fonts sometimes look like that, even in the menus etc.

How can i make win7 appear once in grub?

---

### Post by elliotn on 2011-04-03
bump

---

### Post by oldfred on 2011-04-03
Not too many of us know about burg. 

I think the fonts question is specific to burg and what it is using.

It shows you have two installs of windows - one in sda & one in sdb. Is that not correct?

---

### Post by RJ12 on 2011-04-03
Do you have another installation of Windows on a different hdd? It could also be a recovery partition.

---

### Post by elliotn on 2011-04-04
> **RJ12 said:**
> Do you have another installation of Windows on a different hdd? It could also be a recovery partition.

I only have one windows installed, in an ntfs partition there is a folder named boot, in that folder there is 2 files named BCD and BCD.LOG if i delete bcd windows boot gets corrupt but in grub 1 windows7 shows.

---

### Post by elliotn on 2011-04-04
any ideas

---

### Post by oldfred on 2011-04-04
Windows installs a small 100MB boot/recovery partition that has the BCD & bootmgr. I think the os prober looks for those files and the boot flag to know what is windows bootable. But if your main install is on the sdb and you repaired that partition you may have also added the BCD & bootmgr. Then both would show as bootable, but both BCD's would boot the same main install.

to confirm my guess:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Mark Phelps on 2011-04-04
The MS Windows Repair Startup tool is not the smartest utility around -- and if you did do a repair using it, it likely did as oldfred suggested.

A side-effect of placing the boot loader files on sdb is that it would have updated the MBR to point to sdb instead of sda.  So, if you delete the boot loader files from sdb, you will no longer be able to boot.

---

