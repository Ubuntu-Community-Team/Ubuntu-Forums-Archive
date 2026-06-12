---
title: "error from a newbie - please help"
date: 2009-08-05
forum: General Help
---

### Post by uge on 2009-08-05
Hi guys,

I just installed Ubuntu 8.04 LTS 64 bit (desktop) on my computer.

I noticed the sound didn't work.

Since it's a built-on-board card, I went on ASUS website and looked for downloads, for Linux, in the downloads page for my model : P5GC/MX-1333

So I found a download called "linux drivers".
Downloaded it, extracted it and I found an Audio subfolder ! Too cool !
Even cooler, there was an install file so I ran
   sudo ./install
in the terminal

and now text was flying through like there was no tomorrow.

noticed a couple of error messages.... and sound didn't work still...

got to something else, logged out... everything's fine.

Now I tried to log in again and damn, it logs me out immediately.

I get this message that it logged me out 10 seconds after log in so it could be a problem, when I see the log, it's about a file called
   /usr/bin/seahorse-agent
and it says it can't open or find a share library (something about sound)

so now I can only log in using terminal, and can't use GNOME anymore - not even in failsafe mode !!

Please help !

Is there an easy way to undo what the ./install did ?


That's the primary issue.

Second issue : how can I make the damn sound work ;)


Anyone can help ??

---

### Post by uge on 2009-08-05
uh, just for the reccord, the RIGHT name of the board is an ASUS P5GC-MX/1333

---

### Post by nhanquy on 2009-08-05
[http://ubuntuforums.org/showthread.php?t=186298&page=2](http://ubuntuforums.org/showthread.php?t=186298&page=2)

Hopefully you can bring back gnome.

---

### Post by uge on 2009-08-05
> **nhanquy said:**
> [http://ubuntuforums.org/showthread.php?t=186298&page=2](http://ubuntuforums.org/showthread.php?t=186298&page=2)

Hopefully you can bring back gnome.


Thanks for the reply but... I'm not sure I understand...

the thread you posted the link for, is about installing GNOME on a server version of Ubuntu.

on my side, I installed Ubuntu 8.04 LTS 64 Desktop, so it came with GNOME pre-installed.


or.... are you suggesting that I completely uninstall GNOME and reinstall it ?

---

### Post by uge on 2009-08-05
Hey guys, I need help really ;)

Listen what I wanna know is

1) Does SEAHORSE is only used with GNOME or is it used by anything else
2) If SEAHOURSE is only used for GNOME, how can I just uninstall everything that has to do with GNOME, and reinstall it ?
I want to keep my settings for SSHD / SFTP (MySecureShell) / LVM config / RIBS.
I could back it up, back I'd rather just clear gnome, and reinstall it clean, while keeping all my other "server like" apps and configs intact.
Would you recommend to do so ?

3) If NOT, what do I do :(

4) Can you help me to make the freakin sound work ?


THANKS !

---

