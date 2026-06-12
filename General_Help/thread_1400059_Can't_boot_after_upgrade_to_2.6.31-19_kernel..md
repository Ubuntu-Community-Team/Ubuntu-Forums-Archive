---
title: "Can't boot after upgrade to 2.6.31-19 kernel."
date: 2010-02-06
forum: General Help
---

### Post by kordenal on 2010-02-06
Hello.
Can't boot after upgrade to 2.6.31-19 kernel. Boot procedure stops on "Mounting root file system..." stage with message:
/init: line 218: syntax error: 0xhda1.

Can anybody help me? 
Thanx.

---

### Post by 23dornot23d on 2010-02-06
I have just upgraded too ..... will reboot and see if I get the same error .... watch this space .....

---

### Post by bowens44 on 2010-02-06
I can't boot into 2.6.31-19 either. Grub just hangs at the screen that allows me to select the kernel to boot into. I have let set for as long as 10 minutes. If I select the previous kernel it boots but it takes between 3 and 4 minutes to boot.

---

### Post by mushwars on 2010-02-06
it appears the new kernel has some problems. I did the upgrade on my brothers kubuntu. it seems to "hang"
**hit escape and post your error message**

I believe a bug report should be filed if [s]3[/s]4 of us have the same problem.

(ps. I have been answering posts all night and morning there have been a lot of complaints about the .19 kernel)

cheers.

---

### Post by 23dornot23d on 2010-02-06
Mine took slightly longer to go in ..... but is ok for me ...... faster into kde once the UBUNTU LOGO cleared ...... 

it went about 7 times back and forth across the HYPNO LOGO though ......

( I am not running gdm though (or pulseaudio) not that that pulsaudio should make any difference .....  )

I replaced it with kdm ...... and gnome runs ok from it too ..... no apparent problems ....

also using legacy grub .... as my install was an upgrade from 9.04

hope this helps in some small way .....

---

### Post by NFblaze on 2010-02-06
Damn I just upgraded...but I havent restarted yet, now Im scared to.


Edit: No worries, here restarted had no issues.

---

### Post by ddarsow on 2010-02-06
Hmm...
I upgraded all 5 of my machines yesterday. No troubles here. All different hardware as well, Even my 64bit machine and my laptop had no troubles.

---

### Post by kordenal on 2010-02-06
I try to boot for previously kernel (I have 5th old kernel in my GRUB menu) with same result.
/init : syntax error: 0xhda1
Kernel panic - not syncing: Attempted to kill init!
Pid:1, comm: init Not tainted

---

### Post by kordenal on 2010-02-06
> **ddarsow said:**
> Hmm...
I upgraded all 5 of my machines yesterday. No troubles here. All different hardware as well, Even my 64bit machine and my laptop had no troubles.

You are lucky bargee!
As I see - there are changes in GRUB config file. Before update all disks treats by UUID. But now as (hd0,0). 
My be it is root of problems?

---

### Post by bowens44 on 2010-02-06
> **mushwars said:**
> it appears the new kernel has some problems. I did the upgrade on my brothers kubuntu. it seems to "hang"
**hit escape and post your error message**
cheers.

Hitting escape does nothing. I don't see any error messages. It's just frozen.

---

### Post by lovinglinux on 2010-02-06
No problems here, although Grub still takes 23 seconds to load (the bug when grub is on a different drive than the mbr).

---

### Post by kordenal on 2010-02-06
I have found solution for me.
I have changed GRUB menu by hand like this:
root (hd0,0)
kernel /boot/vmlinuz-2.6.31-19-generic root=UUID=<long number> ro
initrd /boot/initrd.img-2.6.28-17

Some removal of tonsils through anal. But it help.

---

### Post by t4thfavor on 2010-04-15
has this been fixed? I just upgraded a webserver to the 31-19 kernel, and guess what... It hangs at boot, the old kernels wont boot anymore either :(

it appears to hangon "Could not access PID file for nmbd"

I will try booting with no quiet and no splash, and see what happens.

---

### Post by lovinglinux on 2010-04-16
Never mind, wrong subject.

---

