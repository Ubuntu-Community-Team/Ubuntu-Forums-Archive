---
title: "WINE wont run a ICMP win app-socket error?"
date: 2011-10-03
forum: General Help
---

### Post by cabsandy on 2011-10-03
Hi all,
I have a weird problem, and I can only solve it by going over to root user. I'm not a Linux expert , by any means so bear with me. I'm trying to set up some test machines, quite old (Optiplex GX280's with 1Gb RAM). I can install the iso (Ubuntu 10.10), get my updates etc etc-no problems.I'm trying to run a specific program that is Windows called fping ( [http://www.kwakkelflap.com/fping.html](http://www.kwakkelflap.com/fping.html) ). It has some great leaps over the normal Windows ping (if there is a sutiable Linux version that does what it does, please shout). My problem is when I go to use it (fping.exe) under a "normal" login, WINE will let me run it (I need to use the cmd.exe file in the WINE windows folder, it wont run of its own accord) but it then comes back with a WPA error-the web says this is related to a windows socket error?
However, I jump into root and taa-daa, it works.Thing is, I dont want to be in root (for obvious reasons), and root also doesn't play with other apps I use , like Teamviewer (I know, I could use VNC but I like Teamviewer) and Chrome. Has anybody any idea how to fix this, when logged in as something else than root? I've been trying to fix it for the past few days and I think there must be some workaround/way to get WINE to play ball.

thanks

cabs

---

### Post by cptrohn on 2011-10-03
I am not familiar with that program, what does it do that a normal ping command from terminal followed by the appropriate switch doesn't do?

---

### Post by cptrohn on 2011-10-03
[http://linux.about.com/od/commands/l/blcmdl8_ping.htm](http://linux.about.com/od/commands/l/blcmdl8_ping.htm)

Here is a list of linux ping switches if that helps any....
[http://linux.about.com/od/commands/l/blcmdl8_ping.htm](http://linux.about.com/od/commands/l/blcmdl8_ping.htm)

---

### Post by cabsandy on 2011-10-03
> **cptrohn said:**
> I am not familiar with that program, what does it do that a normal ping command from terminal followed by the appropriate switch doesn't do?

Thanks for the reply,
I dont think it can timestamp each individual ping and it cant do the jitter measurement either?

It's what I've been using for my testing for a while,so I'd like to keep the familarity.

thanks cabs

---

