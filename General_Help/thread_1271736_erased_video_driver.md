---
title: "erased video driver?"
date: 2009-09-21
forum: General Help
---

### Post by jesse c on 2009-09-21
Trying to get my nvidia x driver started,i googled 'nvidia driver' and found a post about enabling a 'fglrx-amdxxx' package in synaptic.Since my desktop is AMD based i thought id give it a try. applying the package stated it would uninstall the Nvidia 180.xxx driver i had enabled in 'hardware driver' previously.I thought -why not?-but i restarted my computer and it boots to a blank screen.How can i undo my mistake?Can i bring up a terminal window somehow with keyboard and if i can what should i type?

---

### Post by CatKiller on 2009-09-21
> **jesse c said:**
> Trying to get my nvidia x driver started,i googled 'nvidia driver' and found a post about enabling a 'fglrx-amdxxx' package in synaptic.Since my desktop is AMD based i thought id give it a try. 

AMD bought Ati last year. fglrx is the name of Ati's proprietary driver.

> 
applying the package stated it would uninstall the Nvidia 180.xxx driver i had enabled in 'hardware driver' previously.I thought -why not?-but i restarted my computer and it boots to a blank screen.How can i undo my mistake?Can i bring up a terminal window somehow with keyboard and if i can what should i type?

Ctrl-Alt-F1 should take you to a virtual console. Or you can use Recovery mode to get a root shell.

```
sudo apt-get install nvidia-glx-180
``` should re-install the driver (you don't need the *sudo* if you're in a root shell) You may need to enable it after you've installed it, either by editing xorg.conf or by running ```
sudo nvidia-xconfig
```

---

### Post by jesse c on 2009-09-21
CatKiller: cntrl/alt/f1 doesnt do anything(stays blank screen) and recovery mode asks for root shell log in password and my regular password is not accepted and i dont have another password as far as i remember.When GRUB menu rolls by during loadup i happened to see the fgrlx line that had [ok] next to it and underneath on next line was nvidia with [ok].Is there any way to stop grub and change the[ok] on the fgrlx line?

---

### Post by jesse c on 2009-09-21
Solved:sorry CatKiller i revued some other posts with same problem and realized that the recovery shell was not asking for log in but i guess was telling me i was logged in as root.I typed in recommended code and now im at least back where i started,but i still need to get Nvidia x-driver started,but thats another post. thanks

---

