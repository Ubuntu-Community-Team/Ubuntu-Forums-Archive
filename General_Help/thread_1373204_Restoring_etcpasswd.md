---
title: "Restoring /etc/passwd"
date: 2010-01-05
forum: General Help
---

### Post by Vunutus on 2010-01-05
I was messing around with vipw and accidentally wiped the whole file. Luckily, I have a backup copy.

Is it safe to just paste the backup into any old file and "cp <file> /etc/passwd", or is there any special procedure?

I'd appreciate urgent help. As I understand it, things are fine for now but if I restart very bad things will happen since root is gone and such

---

### Post by audiomick on 2010-01-05
Hallo.
I assume you are sure your backup is good.

Try
```
gksu gedit /etc/passwd
```

if the file is still there, it will open it, if not it will create it. Then paste the contents of your backup in and save it.

The "gksu" opens gedit as root, which allows you to edit an existing /etc/passwd, and gives the one you create the right permissions.

---

### Post by michy99 on 2010-01-05
I think that would work, but of course only root can write to /etc so```
sudo cp <file> /etc/passwd
```

---

### Post by Vunutus on 2010-01-05
Erm so my next problem is that I cannot sudo with a bad /etc/passwd file. Is there any way around this short of mounting my system from a livecd?

---

### Post by oldos2er on 2010-01-05
You can try resetting your password: [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by Leppie on 2010-01-05
boot into either the recovery console or single user mode, this should provide you with a root shell

---

### Post by Vunutus on 2010-01-05
Are there any possible complications with doing this? Keep in mind this is Ubuntu Server (hardy 8.04), and my /etc/passwd file currently contains a single lowercase h.

If I restart the server, select recovery mode from GRUB, and type "passwd root" followed by my password, can I then reboot as normal, log in as root, restore my backed up /etc/passwd, then reboot and have an operational system again?

EDIT: Specifically I'm asking because I've found threads like [this]("http://ubuntuforums.org/showthread.php?t=439115") where people were having trouble (although that is from an older version).

---

### Post by sisco311 on 2010-01-05
> **Vunutus said:**
> Are there any possible complications with doing this? Keep in mind this is Ubuntu Server (hardy 8.04), and my /etc/passwd file currently contains a single lowercase h.

If I restart the server, select recovery mode from GRUB, and type "passwd root" followed by my password, can I then reboot as normal, log in as root, restore my backed up /etc/passwd, then reboot and have an operational system again?

EDIT: Specifically I'm asking because I've found threads like [this]("http://ubuntuforums.org/showthread.php?t=439115") where people were having trouble (although that is from an older version).

Boot a Live CD, mount the root partition and restore the file.

---

### Post by Vunutus on 2010-01-05
> **sisco311 said:**
> Boot a Live CD, mount the root partition and restore the file.

I should also mention that I use software RAID, so I'm not sure how a live CD will handle that

---

