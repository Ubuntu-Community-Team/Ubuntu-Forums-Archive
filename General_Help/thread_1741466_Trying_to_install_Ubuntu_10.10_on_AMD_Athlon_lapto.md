---
title: "Trying to install Ubuntu 10.10 on AMD Athlon laptop"
date: 2011-04-28
forum: General Help
---

### Post by newbun on 2011-04-28
A few days back, I burned a CD with Ubuntu 10.10 (maverick?).  Have since installed 10.10 on an old desktop (pentium ii, 1.15 ghz) and it boots up ok - (apart from a 'freeze' issue which varies from 10 mins to 2 1/2 hours)

Anyway, my immediate problem is I'm using the SAME CD to install 10.10 on a AMD Athlon laptop (which previously ran Windows XP).
The installation process starts with the usual: TRY/INSTALL screen - I select INSTALL.  The whole process runs for about 40 mins, using the entire 60gb drive (I've got rid of XP).  The final few messages are: 'installing system', 'copying installation logs' 'installation complete' - 'restart now'.
So, the CD is ejected after which I get a string of '2380 nnnnnn i/o error device sector 533280'messages.  Then, 'will now restart'

At the restart, up comes the UBUNTU screen and the intro clip...and there it stays.

My question, does anybody know what could be happening - if anything??  Remembering that this CD was installed on the desktop.

I've tried three times :-(

---

### Post by newbun on 2011-04-28
It appears I've been loaded into Command Line Interface mode.  But why?   I would like to boot straight in GUI.

When I type: CTRL/ALT/F5 I'm sent to: **Ubuntu 10.10 'my id' TTY5**

The lspci command displays: 

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

Can any forum members help please?

---

### Post by mörgæs on 2011-04-28
How much memory is in the machine?

---

### Post by KegHead on 2011-04-28
Hi!

Have you tried;

"try"

You may have a bad disk?
You'll be able to determine any problems.
Do you have at least 256 ram?

KegHead

---

### Post by newbun on 2011-04-28
> **KegHead said:**
> Hi!

Have you tried;

"try"

You may have a bad disk?
You'll be able to determine any problems.
Do you have at least 256 ram?

KegHead



Hi

I'm guessing you mean 'tty'?  Gives: /dev/tty4

I have 1gb RAM.  Previously this machine was running Windows XP without any problems.

Thanks

---

### Post by mörgæs on 2011-04-28
You might need boot options. There are a couple of links here:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

