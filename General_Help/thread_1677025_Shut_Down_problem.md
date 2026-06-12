---
title: "Shut Down problem"
date: 2011-01-28
forum: General Help
---

### Post by Alan.Brown on 2011-01-28
I have just finished installing Ubuntu 10.10 onto a new machine - HP Pavilion All-In-One 200-5220a - and it is working a treat!!!

Only problem is when I try to shut down or restart the computer seems to begin the procedure (ie applications close and the gnome panels disappear) then it hangs and I have to stop the computer by manually switching off.

There do not appear any other problems.

Help please.

TIA

Alan

---

### Post by amsterdamharu on 2011-01-28
If you press control + alt + F1,F2,...F8 you might see some output. My guess it'll say "system halted".

This usually happens when a system is started with some apic or apci option off.

---

### Post by Alan.Brown on 2011-01-28
Thanks for your reply

> If you press control + alt + F1,F2,...F8 you might see some output. 

As the system tried to close down, all applications close, then the panels close, then everything hangs.   I cannot access the keyboard to do as you suggest.

If I enter ```
reboot -f
``` the systems will reboot normally without hanging.

I am still investigating.

Thanks

Alan

---

### Post by amsterdamharu on 2011-01-28
The /var/log/kern file might give you an idea what's happening.

This usually contains a lot of info and when you reboot it is hard to see what it did last when you shut down. I think if you have a live CD it's easier to boot off that after the failed shutdown and then mount your Ubuntu partition to pen the kern file (it's just a text file).

It will be in (your Ubuntu partition on the harddisk)/var/log/kern and the last line is probably what crashed it.

---

### Post by Alan.Brown on 2011-02-09
**amsterdamharu**

Thanks for your reply.

I had a look at **kern.log** and other logs and could not find any relevant message at the exact time I tried to restart.

However, I found the following in **/var/log/auth.log** at the exact time.

> Feb 10 11:55:31 HP-200-5220a polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.23, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
But I don't know what it means and would be grateful for help.

**sudo reboot** and **sudo reboot -p** only work with the **-f** option so some process is hanging but can be forced to close.

I am running Windows 7, openSuSE 11.3 and Puppy Linux 5.2 on the same computer and have no trouble with them.

Alan

---

