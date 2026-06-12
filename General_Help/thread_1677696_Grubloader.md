---
title: "Grubloader"
date: 2011-01-29
forum: General Help
---

### Post by Krabs on 2011-01-29
I'm use ubuntu 8.10 ( on a msi 645 notebook ) and i'm trying to shutdown from grub. I have add these entries to menu.lst after the ### END AUTOMAGIC KERNEL LIST 
 
title Halt
halt
 
I only get a black screen but the pc is still running someone said it only put grub to sleep or something. I also tried this commands 

sudo shutdown -h now
or init 0, poweroff... but there all "unrecognized commands" in grub...
 
Is there a possibilty to shutdown from grub.

---

### Post by ajgreeny on 2011-01-29
Not with a command as far as I'm aware.  Just press the button!

---

### Post by tredegar on 2011-01-29
> sudo shutdown -h now
or init 0, poweroff...
These are all linux commands. grub hasn't loaded linux yet, so they will not work.

---

### Post by TheHackOps on 2011-01-29
First off -h is hibernate not power off and why in the world would you want to shut down from grub?

---

### Post by OldBoy44 on 2011-01-29
Hi - My comment is a little off-topic,

Just a friendly comment to TheHackOps! I do not use Windows but there are many Ubuntu users who do, who may not find your signature very amusing.

Cheers,  :P

---

### Post by Krabs on 2011-01-29
_Command:_ **halt** *@option{--no-apm}* The command halts the computer. If the @option{--no-apm} option is specified, no APM BIOS call is performed. Otherwise, the computer is shut down using APM. Some other users of ubuntu has no problem with the halt command and the pc shutdown properly.

---

### Post by ajgreeny on 2011-01-29
> **TheHackOps said:**
> First off -h is hibernate not power off and why in the world would you want to shut down from grub?
No it's not; the **-h** in the **sudo shutdown** command is for halt, not hibernate, **-r** is for reboot.

---

