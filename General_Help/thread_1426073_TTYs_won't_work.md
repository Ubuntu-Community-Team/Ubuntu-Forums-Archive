---
title: "TTYs won't work"
date: 2010-03-09
forum: General Help
---

### Post by VinisLentoje on 2010-03-09
Hello,

I have searched the web, tried getting support on IRC, and even tried some drastic measures that I came up with on-the-fly, but could not get satisfactory results.

After installing the 2.6.31-20 kernel, I have noticed, that virtual terminals ( or whatever should I call those. The ones that are accessed by ctrl+alt+[function_key]) stopped loading. When I open any of them I only see a cursor and nothing else. I can take almost no actions: the only two things that actually work are changing between terminals and ctrl+alt+delete.
Eventually, I gave figured out, that this happens because getty is not launched automatically. After running appropriate command, each terminal can be recreated for the current session. Tried fixing this by creating a script that would run that command on each startup, but could not actually make the script to be executed (I tried making rc to run it, as I need these terminals to be present when GUI is not yet activated).

Right now, I see two possible solutions: either make them autoload like they are supposed to, or work out a way for that script to be ran on startup. So, any ideas?

Ah, yes. Also, the GDM now loads on tty2. Will it give me problems if it continues like that?

Thank You in advance!

[offtopic]
It is 4 AM and I am working on this problem for at least 11 hours straight... Pretty tired...
[/offtopic]

---

### Post by VinisLentoje on 2010-03-10
**B**.ring
**U**.p
**M**.y
**P**.ost

---

### Post by VinisLentoje on 2010-03-12
**B**.ring
**U**.p
**M**.y
**P**.ost

Again

---

### Post by VinisLentoje on 2010-03-15
Bump

---

### Post by VinisLentoje on 2010-03-26
Please, someone!

---

### Post by prodigy_ on 2010-03-26
> **VinisLentoje said:**
> After installing the 2.6.31-20 kernel
I'd suggest you to revert back to 2.6.31-19. For me, the newest 9.10 kernel was nothing but a problem.

---

### Post by scratchr on 2010-05-01
Same. I was ok, then it happened.

:confused:

---

### Post by VinisLentoje on 2010-05-02
> **prodigy_ said:**
> I'd suggest you to revert back to 2.6.31-19. For me, the newest 9.10 kernel was nothing but a problem.

Loading the 2.6.31-19 kernel did not solve the problem, as it seems that after the 2.6.31-20 got installed to my computer, i started to having the same problem with earlier kernels.
But, not long (~a week) ago, when I had finally decided reboot for a specific reason, I had noticed, that it started to work again. It seems, that was because of a *newer* kernel that got loaded. No problems as of now, I think.
Did not mark the thread as solved back then, because even though I tried to find a way to mark it as solved on many occasions, I only found it 10 minutes ago.

> **scratchr said:**
> Same. I was ok, then it happened.

Could You provide more information? Like: what distro and kernel You are using? when did You noticed the problem for the first time? Et cetera, et cetera... That would make it way easier for us to help You.

---

### Post by scratchr on 2010-05-03
It was doing what you described, loading gui in f2, no tty.
When using Ctrl+Alt+F[1,3-6] I get a blinking cursor and no login prompt. 
I am running Ubuntu 10.04. 

who turn out:
```
tty2         2010-05-03 22:08 (:1)
pts/0        2010-05-03 22:11 (:1.0)
```This command will temporarily fix tty1, but tty2 still has gui. Also exit will undo this command instead of returning to login.
```
sudo getty -8 38400 tty1
```Also Ubuntu is running after no kernel updates.

I found this error in ctrl-alt-f7
```
init: Failed to spawn rc-sysinit main process: unable to open console: Input/Output error
```
More about this is here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2228050.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2228050.html)

---

### Post by scratchr on 2010-05-06
Help?

---

