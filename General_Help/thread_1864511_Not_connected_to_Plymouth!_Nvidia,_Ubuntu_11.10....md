---
title: "Not connected to Plymouth! Nvidia, Ubuntu 11.10..."
date: 2011-10-19
forum: General Help
---

### Post by Jelster64 on 2011-10-19
Hey, I recently installed Ubuntu 11.10 on my new laptop, and as soon as it's installed it's using Ubuntu 2D. So I went to the menu of my video card driver thingy (it's a NVIDIA GT 520M, Cuda 1GB it says on the sticker on my laptop) and it says I'm not using it! So I had to run the command nvidia-xconfig as root. So I just opened up terminal and used sudo nvidia-xconfig and as soon as I restarted the laptop, it said it wasn't connected to Plymouth! What should I do about that? Please help!

---

### Post by Jelster64 on 2011-10-19
BUMP

Please? Anyone?

---

### Post by sadrak on 2011-10-27
same with ati here ... after entering password a short message about not connecting to plymouth is visible, then the loginscreen is back ...

i dont find hints in any logfile (X/dmesg/syslog/...).

Another account works fine! Its only my main-account :(

---

### Post by sadrak on 2011-10-27
OK, my problem is encrypted home + lightdm ...

lightdm want to start a xfce4-session, that come back and exit after ~0 Seconds and i am back at login. Accounts without encrypted home works fine!

```

Oct 27 09:25:59 Fish-PC kernel: [   41.150988] Valid eCryptfs headers not found in file header region or xattr region
Oct 27 09:25:59 Fish-PC kernel: [   41.150992] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Oct 27 09:25:59 Fish-PC kernel: [   41.904330] [fglrx] IRQ 47 Disabled
Oct 27 09:26:00 Fish-PC acpid: client 978[0:0] has disconnected

```

I added two new accounts, one with encryption, one without. Only without working. gdm & lighdm are effected. Also when i login my account at other tty and then try to login not work.

P.S.: I have a ati card, so it cannot a nvidia problem (like many other problems describe)

---

