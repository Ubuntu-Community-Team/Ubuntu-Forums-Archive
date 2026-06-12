---
title: "Require sudo password on partition mount"
date: 2010-04-30
forum: General Help
---

### Post by WorMzy on 2010-04-30
It appears that Lucid has done away with the gksu prompt that used to greet you when you try to mount a partition. Is there any known way of restoring this? I have a number of partitions which I would rather have protected by a password (even though I know that booting a live cd will give anyone access to any mountable partition, no questions asked). I've had a quick look in gconf and found nothing that looks like it would control this behaviour, but it's quite likely that I overlooked something. Does anybody have any ideas?

---

### Post by Premium Jersey Milk on 2010-04-30
Get Mount manager through synaptic. Run from system-admin-mount manager.

Select the drive on the left side, edit permissions from administrator to everyone in the right side panel.

Hope this helps, I had the same problem as you this morning and this worked for me.

---

### Post by WorMzy on 2010-04-30
Thank you for the reply, but that seems to be the inverse of what I am trying to achieve. I want to be prompted for my sudo user password when I try to mount a partition, currently it just mounts the drive without the prompt.

---

### Post by mc4man on 2010-05-01
In a terminal go 
```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

For the first listed override change the ResultActive=yes to

ResultActive=auth_admin_keep

Or if you want to 'deactivate' all three included overrides then simply

```
sudo mv /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla.bak
```

First option is probably the best

---

### Post by WorMzy on 2010-05-01
Excellent, that's exactly what I was looking for. Thank you.

---

### Post by maestrobwh1 on 2010-05-01
I want to do the opposite. I am the only user of my laptop and I want my data partition to be mounted and unmounted at will without a password prompt. Since Lucid does not have the "Policykit-Authorization" gui from SystemSettings (kde), I cannot pull this off now.  I tried editing the above file and changed "admin" to my username but that made no difference.

I could just add it to fstab, but I should not have to.  I feel Lucid KDE removed some decent user functionality by removing the "frontend" to policykit.

Is there a way to accomplish the bypassing of the password prompt?

---

### Post by SoFl W on 2010-05-24
> **mc4man said:**
> In a terminal go <SNIP>

Thank you, This helped me as well.

---

### Post by SoFl W on 2010-06-24
I finally got around to installing 10.4 on my desktop and applied this.  However I now need to use a password when I use a USB drive.
Is there anyway to require a password for a certain (Windows) partition but not for USB/external drives?

---

### Post by clearblue on 2010-08-09
@mc4man:  RESPECT

I added an entry for the partitions i do not want in /etc/fstab and the symbols in nautilus disappeared imediatly when i saved fstab. 

But the entries with the option users disappear too.  #-o

I hope the ability for normal users to mount the fstab entries also disappears.

---

### Post by chaemil on 2010-08-18
help. this is not working in ubuntu studio 10.04....

---

