---
title: "Major Hardware Problems"
date: 2012-06-19
forum: General Help
---

### Post by EienTatsu on 2012-06-19
Over the past month or two I've been having some major hardware problems. First off my WD 2TB caviar green drive had a bunch of bad sectors and then I started getting I/O errors from the drive. So I bought a new drive and migrated the data over. Well about 2 weeks ago I began getting the errors again on my / drive(120GB SSD). And as of today both my replacement WD 3TB and my SSD are giving me errors. So I re-installed Ubuntu 12.04 LTS x64 on the SSD using the same drive as the /home partition. Now I keep getting freezeups and if I look at CTRL+ALT+F1 I see the image attached.

Both drives are plugged into sata 6 ports on a Asus P7P55D-E Pro motherboard. Any help would be much appreciated since I need my computer up and running.

---

### Post by Bobhuber on 2012-06-19
> **EienTatsu said:**
> Over the past month or two I've been having some major hardware problems. First off my WD 2TB caviar green drive had a bunch of bad sectors and then I started getting I/O errors from the drive. So I bought a new drive and migrated the data over. Well about 2 weeks ago I began getting the errors again on my / drive(120GB SSD). And as of today both my replacement WD 3TB and my SSD are giving me errors. So I re-installed Ubuntu 12.04 LTS x64 on the SSD using the same drive as the /home partition. Now I keep getting freezeups and if I look at CTRL+ALT+F1 I see the image attached.

Both drives are plugged into sata 6 ports on a Asus P7P55D-E Pro motherboard. Any help would be much appreciated since I need my computer up and running.
Boot from a live cd and run fsck on the drive and see what happens. Reinstalling on a bad drive wont fix anything. You might also try zeroing out the SSD to see if that might help. Do a google search to get info on how to do that for your drive and what it does if you need more info.

---

### Post by EienTatsu on 2012-06-19
> **Bobhuber said:**
> Boot from a live cd and run fsck on the drive and see what happens. Reinstalling on a bad drive wont fix anything. You might also try zeroing out the SSD to see if that might help. Do a google search to get info on how to do that for your drive and what it does if you need more info.
I already tried fsck. I can zero out the SSD but the problem drive keeps changing.(AKA its saying all drives are failing)

---

### Post by Bobhuber on 2012-06-19
> **EienTatsu said:**
> I already tried fsck. I can zero out the SSD but the problem drive keeps changing.(AKA its saying all drives are failing)
If you think the drives are good then either the controller is going bad (as stated in your heading major hardware problems)or something else has changed . Are  you using the same Kernel ? Have you had a recent upgrade that might cause the problem? Are you using an Ext 4 file system ? Also if you have one try a Sata 3 port on the MB.

---

