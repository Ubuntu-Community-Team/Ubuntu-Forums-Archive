---
title: "Recovery Mode vs. Normal Mode"
date: 2006-01-30
forum: General Help
---

### Post by Stereotypical Rage on 2006-01-30
What exactly is run during Recovery mode and a regular boot up? I can't remember the last time I actually booted Ubuntu normally. I've used every single Ubuntu release. (Warty, Hoary, Breezy and Dapper.) all versions freeze at the gdm login screen. If I am lucky to get to the desktop, it freezes within moments of loading.

If I boot into recovery mode, then type "gdm" at the prompt, everything runs fine...From what I can tell. Am I doing something wrong?

Is there something bypassed when booting Recovery Mode? As far as I know. Normal mode is run level 4 or 5 (I forget which) and Recovery Mode is 1. Is there a way to know what exactly is booting at each of the specific run levels or modes?

Please Note: I have not customized the bootup functions, but I am wondering if I should do that to see what's playing around. My main problem is I'm not home enough to play around with it all that well. Also, this problem happens in 32bit as well as 64bit.

If a moderator deems this thread to be placed somewhere else, please do so. I wasn't sure on where I should put it.


I do thank anyone in advance who bothers to read this.

---

### Post by hegenious on 2006-01-30
Is there a way to know what exactly is booting at each of the specific run levels or modes?

Yes. Open a console and type **man init**. That'll show you what the different run-levels represent.

To find out at which run-level you are currently operating,  type **who -r** in a console window.

---

### Post by Stereotypical Rage on 2006-01-30
I know what run-level I am in now. (Recovery Mode) aka run level 1. **who -r** didn't work, however **who -a** did work.

I'm just looking for what exactly is loaded during runlevel 1 vs. runlevel 5. I'm betting something in runlevel 5 is borking my system.

---

### Post by hegenious on 2006-01-30
ok, you want to know what gets started at every runlevel. Check the **/etc/rcX.d** directories, where the 'X' represents a run-level., e.g. you should see an /etc/rc5.d directory with links in it pointing to the programs that should startup in that run-level.

if for some reason you want to disable the startup of a program, just rename the link to something else. on the other hand these directories are handy as you can place a link to any program in any of those 'run-level directories' and it will be started by switching to that runlevel.
switching run-levels goes like this: **sudo init <run-level>**.

strange thing though that who -r doesn't work, it always worked on every *nix box I ever logged in to. perhaps it's because you booted recovery mode.

---

### Post by dcstar on 2006-01-30
[QUOTE=Stereotypical Rage]I know what run-level I am in now. (Recovery Mode) aka run level 1. **who -r** didn't work, however **who -a** did work.

I'm just looking for what exactly is loaded during runlevel 1 vs. runlevel 5. I'm betting something in runlevel 5 is borking my system.[/QUOTE]
Install sysv-rc-conf or bum

---

### Post by Stereotypical Rage on 2006-01-30
Thank you. I'm looking at BUM now.

---

