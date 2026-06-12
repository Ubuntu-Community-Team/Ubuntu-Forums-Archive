---
title: "I am getting this error . . ."
date: 2010-07-06
forum: General Help
---

### Post by WSPerm on 2010-07-06
I keep getting this error when I try to install Adobe flash player 
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.  

I had it installed just fine, then i restarted my computer and its gone. . . I am brand new to Ubuntu.  Just installed it yesterday.  Thank you

---

### Post by Samulus on 2010-07-06
It wants you to run the command  sudo dpkg --configure -a in the terminal to fix the problem. The problem probably occured because the computer was shut down or crashed while it was trying to install flash earlier.  Run the command sudo dpkg --configure -a in the terminal and then try to install Adobe Flash again.

---

### Post by hansdown on 2010-07-06
Welcome to the forum,WSPerm.

You need to run tat command in a terminal, to fix this.

Click applications> accessories> terminal.

Copy and paste this, and hit enter.

```
sudo dpkg --configure -a
```

You will be asked for your password. You won't see it as you type.

Enter it, and hit enter.

---

### Post by WSPerm on 2010-07-06
Ok got it to do the configure now it wants me to install grub, and im clicking install but its not doing it...

---

### Post by hansdown on 2010-07-06
> **WSPerm said:**
> Ok got it to do the configure now it wants me to install grub, and im clicking install but its not doing it...

Could you please post exactly what the message is?

---

