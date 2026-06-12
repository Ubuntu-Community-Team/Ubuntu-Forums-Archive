---
title: "Pc doesn't boot after updating to 11.10"
date: 2011-10-13
forum: General Help
---

### Post by sirvinniei on 2011-10-13
See thread name, whenever i boot THE pc i get a black screen with à few lines saying: *starting Bluetooth *pulsaudio configured for per-user sessions saned disabled; edit etc/default/saned *stopping save kernel messages *starting CUPS pro ring spooler/server *stopping anachronisme(h)ronistic cron ountfall not connected to Plymouth

---

### Post by effenberg0x0 on 2011-10-13
Can you get to recovery? When booting the PC, hold the SHIFT key to see Grub Options. Recovery is most likely the second. Select it.

At some point it will ask you what you want to to do in recovery. You want it to drop you to a root shell prompt".

After login, run this:
```

**mount -o rw,remount /**

```In it, type sudo nano /etc/default/grub and make sure you change the following line to look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset".
```Make sure you don't have the words: "Quiet", or "splash" anywhere in this file.

Press CTRL+X, Y, <Enter> to save and exit.

Now run the following command in the console:
```
sudo update-grub

```And reboot the PC:
```
sudo reboot now

```Report back.

Regards,
Effenberg

---

### Post by sirvinniei on 2011-10-13
Strange, i can open recovery mode but cant select any of the options. It seems like my keyboard is fully disabled when opening recovery mode

---

### Post by effenberg0x0 on 2011-10-13
Is it a USB or wireless keyboard?

Regards,
Effenberg

---

### Post by sirvinniei on 2011-10-13
> **effenberg0x0 said:**
> Is it a USB or wireless keyboard?

Regards,
Effenberg

It is à wireless USB keyboard,

---

### Post by sirvinniei on 2011-10-13
> **sirvinniei said:**
> It is à wireless USB keyboard,

Edit: i tried with à wired keyboard and it worked till i needed to safe, it saus THE. File was read only

---

### Post by effenberg0x0 on 2011-10-13
I edited my original post with a command to set the filesystem in read-write mode, so you can save your changes to /etc/default/grub.


Regards,
Effenberg

---

### Post by sirvinniei on 2011-10-13
When i tried the last code i got to the login screen but it wasnt responsive at all. And now when i try to boot i get black screen with a lot of lines with the last line saying: not connected to Plymouthrulescested block devices

---

### Post by sirvinniei on 2011-10-14
Btw sorry for double post but ubuntu still works with previous kernel, its 3.0 that causes problems i think

---

### Post by sirvinniei on 2011-10-14
Whoops posted the same message twice, some moderator pLease delete this  post

---

