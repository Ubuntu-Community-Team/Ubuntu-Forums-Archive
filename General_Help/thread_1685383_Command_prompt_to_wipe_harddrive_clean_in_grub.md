---
title: "Command prompt to wipe harddrive clean in grub"
date: 2011-02-10
forum: General Help
---

### Post by Mgllam1991 on 2011-02-10
Is there any commands I can type in gnu grub to wipe or format my harddrive

---

### Post by 3Miro on 2011-02-10
> **Mgllam1991 said:**
> Is there any commands I can type in gnu grub to wipe or format my harddrive

No. Formating is no a capability of Grub.

You can use a live CD.

---

### Post by Mgllam1991 on 2011-02-10
I have the cd that ubuntu sent me would that be considered a live cd? And if so how can I make it boot up on startup because ubuntu 10.10 does not want to start up it just sends me to the "pick an os menu" and when I pick an os it just gives me a bunch of text nd numbers followed by (initramfs) and also ubuntu wouldn't let me install the motherboards bios menu so I can't access it

---

### Post by 3Miro on 2011-02-10
> **Mgllam1991 said:**
> I have the cd that ubuntu sent me would that be considered a live cd? And if so how can I make it boot up on startup because ubuntu 10.10 does not want to start up it just sends me to the "pick an os menu" and when I pick an os it just gives me a bunch of text nd numbers followed by (initramfs) and also ubuntu wouldn't let me install the motherboards bios menu so I can't access it

A Ubuntu CD is a live CD (meaning you can boot your machine from it).

You should be able to access the BIOS screen by hitting a key during boot (usually del). Note that it is impossible for Ubuntu to prevent you from accessing your BIOS since the BIOS loads long before anything from Ubuntu.

Many motherboards also have an option to "select boot device" at boot (usually by pressing F12 right after you see the post screen). You can use that option to boot from the CD.

---

