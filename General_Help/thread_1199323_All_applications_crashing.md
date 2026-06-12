---
title: "All applications crashing"
date: 2009-06-28
forum: General Help
---

### Post by gruntlips_ on 2009-06-28
I just booted up and everything seemed normal except that all the applications I opened (firefox, thunderbird, and open office) crashed. I rebooted and things seem ok.  Is there a way to troubleshoot/figure out what might have happened?  I am concerned about the stability of my system and potentially losing any data.

I have a serval and am running 9.04.

Thanks.

- gl

---

### Post by kokkus on 2009-06-28
Things like this can happen if for example a broken package is in your You can try following.
1. Restart the pc, go to recovery mode in grub and "repair broken packages". Or you can try an earlier kernel.

---

### Post by gruntlips_ on 2009-06-28
Thanks kokkus.  According to my synaptic package manager I have no broken packages.  I think I am most concerned about either some hardware problem like bad ram or HD or something in the OS that maybe I could investigate using some log files.  This has come right on the heels of successfully fixing another problem associated with my grub after some kind of routine either kernel or grub update. ([http://ubuntuforums.org/showthread.php?t=1193817](http://ubuntuforums.org/showthread.php?t=1193817))

---

### Post by Steelmourne on 2009-06-28
Recently, kernel updates were issued so you are probably using 2.6.28-13. Try restarting the pc, hitting esc and selecting the previous kernel - 2.6.28-11 with the arrow keys and hitting enter. You could have a look at system logs under administration > log viewer.

---

### Post by gruntlips_ on 2009-06-28
Yeah, I am using 2.6.28-13 and all my problems seemed to start when I upgraded to that kernel.  Anything in particular I should look for in the logs?  There is a lot of stuff in there and none of it is very obvious.

Thanks.

- gl

---

