---
title: "How do I restore dead mouse and keyboard input from live cd?"
date: 2011-01-01
forum: General Help
---

### Post by Vigh on 2011-01-01
Hi
 Was just wondering how I restore dead mouse and keyboard input from the live cd. Basically what happened was I was updating the machine and decided to let them run in the background while my sister's 6 year old son played some tux computer games, when he was finished he switched the entire computer off at the power button and unfortunately it was still updating in the background. Now there is no mouse or keyboard input, I cannot get into the recovery console, nor can I control a terminal from the login screen in order to successfully complete the update. This means basically the only option to fix it would be to re-install or fix the human user interface device drivers (keyboard and mouse) via the live cd, I am in need of some advice or instructions on how to go about fixing this issue.

Regards
Ant

---

### Post by Vigh on 2011-01-02
bump

---

### Post by Vigh on 2011-01-02
Reminder to self- attempt to boot into the old kernel and complete update/upgrade from old kernel.

---

### Post by happyhamster on 2011-01-02
You can try fixing your installation by chrooting from a live cd. What you do is: boot into a live session and use the hard-drive's filesystem as the session's root filesystem. Then update/upgrade. Step by step:

Boot into a live session, and mount your harddrive onto the live filesystem (using nautilus for example). Make a note at which folder it's mounted at. You can take a look with:
```

df

```
It's likely something like: /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID
Now, remount it with the dev option:
```

sudo mount -o remount,dev /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID

```
Chroot into the drive's filesystem:
```

sudo mount -t none /dev /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID/dev -o bind
sudo chroot /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID

```
You'll be in a root terminal now, and the hard-drive's filesystem will be used as the session's root filesystem. First run:
```

mount /proc
mount /sys

```
You should be able to repair the system now:
```

apt-get update
apt-get upgrade

```
Perhaps apt will complain, in that case, try:
```

apt-get install -f
dpkg --configure -a

```

Good luck.

---

### Post by Vigh on 2011-01-02
thanks heaps for the advice, should be able to figure your instructions out, will give it a try

---

### Post by Vigh on 2011-01-05
working a treat, going to purge and reinstall ubuntu-desktop as well just to make sure, thanks heaps

---

