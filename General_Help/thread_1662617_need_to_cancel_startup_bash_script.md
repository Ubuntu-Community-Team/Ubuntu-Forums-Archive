---
title: "need to cancel startup bash script"
date: 2011-01-08
forum: General Help
---

### Post by badperson on 2011-01-08
Hi,
I made a mistake on my home server. I installed the eXist xml db, and wrote a bash script so that it would start up when the machine boots up. 

But now, the server just hangs before the system asks for a user logon, so I can't ssh into the machine, and when I have the monitor and keyboard hooked up to it, it's not letting me logon or cancel the script. 

Anyway to kill the current running process and get to the logon, so I can delete that bash script? 

thanks, 
bp

---

### Post by tredegar on 2011-01-08
I am surprised that one broken script causes your boot process to fail, to the extent that even **sshd** is not being started. Anyway...

At the grub menu choose Recovery
Then choose "Root shell"
Remove or disable the offending script.
type **reboot**

---

