---
title: "Typing speed in Firefox"
date: 2011-01-23
forum: General Help
---

### Post by Robbyx on 2011-01-23
I am seeing a unreasonable delay between typing and it appearing on the screen.

I have noticed a lot of entries for firefox-bin and thunderbird-bin in htop and wonder if this is part of the problem.

**Does any one know of solutions to unreasonable typing delays in FF?**

Robin

---

### Post by lithopsian on 2011-01-23
Which version of Firefox?  Is this something that just started happening?  Or after an update?  There is a bug raised on very slow typing response against FF4beta, combined with maximised the CPU.

If you have several processes using up 100% of the CPU then slow typing isn't such a surprise.  If you have loads of processes but not using much CPU then typing should respond normally.

---

### Post by Robbyx on 2011-01-23
Currently my CPU% is highish. The main one is /usr/bin/X :0 -nr -verbose -auth- /var/run/gdmn/auth-for-gdm-gl7vyh/database -nolisten tcp vt7. That is taking up 29% of cpu.

As for memory usage: Firefox 3.6.13 has a lot of entries in Htop all taking about 6% of memory each.

HTop is showing core 1 at 66% and core 2 at 64%. 

I wonder if Recoll is eating up memory, although it is not obvious which programs are causing the high cpu usage. .

---

### Post by uRock on 2011-01-23
I have this problem on one of my machines as well. The problem is only with Firefox. Chrome works fine. Firefox has been causing this problem ever since 10.04 was installed on the machine.

I have not taken the time to trouble shoot the issue, but I am thinking that it will go away after backing up the .mozilla folder and letting FF create a new one.

---

