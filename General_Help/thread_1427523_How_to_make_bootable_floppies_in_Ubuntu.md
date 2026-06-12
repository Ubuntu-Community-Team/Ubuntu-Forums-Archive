---
title: "How to make bootable floppies in Ubuntu?"
date: 2010-03-11
forum: General Help
---

### Post by The Soul Man on 2010-03-11
Anyone know a good program which can make floppies bootable?
I have looked in Synapitc with no luck, I only found floppy formaters.
Can anyone help me?

Regards
The Soul Man

---

### Post by Daveski on 2010-03-11
What OS are you hoping to boot from floppy?

---

### Post by The Soul Man on 2010-03-12
> **Daveski said:**
> What OS are you hoping to boot from floppy?
KolibriOS ( [http://kolibrios.org/](http://kolibrios.org/) ) Do you know a better distro which can boot from floppy?
Thanks for answering :)

---

### Post by c0nfusedami on 2010-03-12
I wish I could use my old 5.25" flopy's just for show.

---

### Post by plucky on 2010-03-12
> **The Soul Man said:**
> KolibriOS ( [http://kolibrios.org/](http://kolibrios.org/) ) Do you know a better distro which can boot from floppy?
Thanks for answering :)

1. Download the 7zip file to your desktop and extract the files.
    I had to install 7zip on my system to open the file.

2. CD to the directory where the files are.

3. Then in a terminal window ```
sudo dd if=kolibri.img of=/dev/fd0
```
   This will copy the bootable image to the floppy.

4. Reboot and make sure the floppy is the first boot device.

This worked for me.

Good Luck

---

### Post by The Soul Man on 2010-03-23
Thanks! Worked just fine for me too !

---

