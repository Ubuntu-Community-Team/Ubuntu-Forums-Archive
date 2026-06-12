---
title: "No GUI after grub recovery"
date: 2009-08-20
forum: General Help
---

### Post by ldvjn on 2009-08-20
Hello,
 
I am new to Ubuntu and I am having a problem with the xserver starting.
 
Originally, I had a dual boot Ubuntu 9.04 and Linux Mint. I removed Linux Mint by the partition editor in ubuntu. Then when I rebooted, the boot loader gave a error 22. So I followed some steps I found to recover the grub boot loader, by means of the live cd. 
 
It worked, and now I can boot Ubuntu, but now my GUI doesn't come up. It just loads to command prompt. are these two problems related? What could I do to reset it, if thats what I need to do?
 
Thanks

---

### Post by rednano12 on 2009-08-20
Try hitting CTRL-ALT-F7. That should bring you into the GUI.

If that doesn't work, your GDM might be switched off. Try the following command to turn it back on. 

```
sudo /etc/init.d/gdm start
```

---

### Post by ldvjn on 2009-08-20
rednano12,
 
I tried to CTRL-ALT-F7, and that didn't work. It just went to a blank screen that had a flashing prompt.
 
Next I ran the command:   
sudo /etc/init.d/gdm start
 
The reply stated that gdm was already running and then it aborted gdm.
So then I ran gdm stop, then gdm start and the screen flickered a couple of times. 
I then pressed CTRL-ALT-F7, and that still didn't work for me. 
 
I did notice right before ubuntu boots to the command prompt, there was an error shown:
 
(EE) VESA(0): Driver can't support depth 24
(EE) Screens found, but none have a useable configuration
 
 
Fatal server error
no screens found

---

