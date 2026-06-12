---
title: "Can't boot. Error: unknown command &quot;terminal output&quot;"
date: 2010-10-30
forum: General Help
---

### Post by oobermensch on 2010-10-30
Ok I know I screwed up something. I was using Ubuntu 10 minutes ago without a hitch. Then I tried reducing the time I needed to select something in GRUB. So basically, I found this command:
> gksudo gedit /etc/default/grub

Now, I get this error:

> Error: Unknown Command "terminal output"
Error: file not found

I got it when I tried reducing the GRUB_TIMEOUT from the code above. I feel so furious now because I knew it was a bad idea to fix something that isn't broke. Can my Wubi install still be saved?

Man this sucks. I love Ubuntu so much for me to be separated from it with this stupid error. ](*,)

---

### Post by viralmeme on 2010-10-30
> **oobermensch said:**
> I get this error: I got it when I tried reducing the GRUB_TIMEOUT

[GRUB_TIMEOUT]("http://ubuntuforums.org/showthread.php?t=1438267")

---

### Post by oobermensch on 2010-10-30
Ok I read some of the stuff in there. I was able to mount my Wubi virtual disk in a Ubuntu live cd. I was also going to edit the grub file in /etc/default/ but the thing is, I am not logged in as root in that drive, so I can't save my edits. When I do gksudo nautilus, I am able to log in as root, but since it is a virtual drive, it doesn't appear on the left pane.

Btw, the mount point of my virtual disk, according to Disk Utility is /mnt. If I do manage to edit is and save it, I need to run sudo update-grub, right? But how can I make it so, that the update-grub is for my virtual disk, and not for my live disk?

---

### Post by oobermensch on 2010-10-30
Never mind. Tried gksudo nautilus /mnt and boom. Anyway, restored the original value for GRUB_TIMEOUT back to 10. Going to reboot now. Wish me luck.

---

### Post by Quackers on 2010-10-30
Good luck :-)

---

### Post by oobermensch on 2010-10-30
Ack. No dice. I think it's because I haven't done update-grub. But I don't know how to update the grub of a virtual disk. Do I need to put some extra parameters? I tried sudo update-grub /mnt without any luck. Still getting the terminal_output error.

---

### Post by oobermensch on 2010-10-30
Bump. Anyone else?

---

### Post by oobermensch on 2010-10-31
So I guess I had no other choice but to reinstall Ubuntu. Up and running now. Thankfully, I backed up all my Compiz settings (which I spent hours and hours on trying to configure all the fancy shmancy effects) and some other stuff.

---

