---
title: "Ubuntu Login Loop After Metacity/Compiz Uninstall"
date: 2011-06-18
forum: General Help
---

### Post by Long_Live_Linux on 2011-06-18
I was sick of the metacity themes on my machine and decided to disable them with "metacity --replace". 

However, when I restarted my machine, the changes didn't take affect. So I decided to remove compiz, emerald, and metacity all together as I don't usually use all of their features. I did this while the windows were still in their metacity/emerald eyecandy.

Then I rebooted my machine and tried to login. I typed my password and it looked like it was going to log me in, but then the screen went blank, and I was back to the login screen.

Interestingly, I noticed that my mouse does not appear on the login screen at all.

I've tried booting in recovery mode, but I can't even get to that. And when I type "alt+ctrl+f1" to get into a terminal, my computer freezes.

Please help, I'm totally lost here and about to just nuke the entire system. Thank you very much in advance.

---

### Post by Long_Live_Linux on 2011-06-18
bump

---

### Post by Long_Live_Linux on 2011-06-18
The .xsessions-error message was:
```
34 Can't open /home/superuser/.profile
```
So I deleted the  .profile with a live CD.

Now I booted into the system and it opened up a terminal window (although it looks like it's xterm not gnome) but that's it. It's a terminal window on a blank desktop. Whenever I try to do anything like "ls" or "sudo (install some program or stop a service)" it says:
```
sudo: unable to change to sudoers gid: Operation not permitted
```

Any thoughts or ideas?

---

### Post by wildmanne39 on 2011-06-18
> **Long_Live_Linux said:**
> The .xsessions-error message was:
```
34 Can't open /home/superuser/.profile
```
So I deleted the  .profile with a live CD.

Now I booted into the system and it opened up a terminal window (although it looks like it's xterm not gnome) but that's it. It's a terminal window on a blank desktop. Whenever I try to do anything like "ls" or "sudo (install some program or stop a service)" it says:
```
sudo: unable to change to sudoers gid: Operation not permitted
```

Any thoughts or ideas?
Hi, this should work to give you root on a livecd.
Livecd use a root

```
sudo -i nautilus
```
opens the root file browser window in the live cd, no password required.

---

### Post by Long_Live_Linux on 2011-06-19
Thanks for the tip, but I just ended up nuking the system and installing 11.04 on it (much better btw - love the unity desktop).

The combination of graphics card driver issues, file system issues, and grub issues make this nuking inevitable.

---

### Post by wildmanne39 on 2011-06-19
> **Long_Live_Linux said:**
> Thanks for the tip, but I just ended up nuking the system and installing 11.04 on it (much better btw - love the unity desktop).

The combination of graphics card driver issues, file system issues, and grub issues make this nuking inevitable.
Hi, your welcome.

---

### Post by dFlyer on 2011-06-19
Please mark as resoled.

---

