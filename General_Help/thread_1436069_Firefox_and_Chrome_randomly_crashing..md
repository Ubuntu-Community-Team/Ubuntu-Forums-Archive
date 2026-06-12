---
title: "Firefox and Chrome randomly crashing."
date: 2010-03-22
forum: General Help
---

### Post by xeemo on 2010-03-22
I'm having a problem where both firefox and chrome are randomly crashing on me.  I'm using Ubuntu 9.10 and everything is updated.  Firefox is the latest version as is chrome.  So far when I've loaded them in the terminal Firefox has just said Segmentation Fault.  Google Chrome has said Segmentation fault Trace/breakpoint trap, and Illegal instruction.  Everything else seems to be running pretty stable.

I've had this problem before, and I've reinstalled ubuntu since then.  It was just firefox at first, but google chrome started doing it too.  I don't have libflashsupport installed.

I'm using a firewall, and I have even gone as far as to run a nessus scan on my system.

Anyone have any idea what could be wrong?

---

### Post by Hikayu on 2010-03-22
Uh oh. Hardware error or corrupted software.

Try reinstalling Chrome or Firefox and see if it helps.

Also, tell us WHAT you did BEFORE this happened.

---

### Post by sakusa on 2010-03-22
Same here with Firefox random crashes. Had hoped the recent  upgrade to FF v3.5.x would solve the problem that was bugging me earlier. No such luck.

Am on Ubuntu 9.10 ever since its release.

---

### Post by xeemo on 2010-03-22
> **Hikayu said:**
> Uh oh. Hardware error or corrupted software.

Try reinstalling Chrome or Firefox and see if it helps.

Also, tell us WHAT you did BEFORE this happened.

I'm guessing Hardware too, but I have no idea what it could be.  I don't think it's corrupted software because I've reinstalled the browsers, and I even went as far as to get the latest version of Firefox which isn't in the repositories yet.  This same thing was happening with Firefox on a previous install.  It's also seemingly random.  It'll not happen for a day or so, and then it will happen once every few minutes.

---

### Post by Hikayu on 2010-03-22
> **xeemo said:**
> I'm guessing Hardware too, but I have no idea what it could be.  I don't think it's corrupted software because I've reinstalled the browsers, and I even went as far as to get the latest version of Firefox which isn't in the repositories yet.  This same thing was happening with Firefox on a previous install.  It's also seemingly random.  It'll not happen for a day or so, and then it will happen once every few minutes.

Hmm, any other software you think? Maybe conflicts?

I doubt this is a hardware error. To confirm, grab the latest LiveCD and see if the same problems occur on it. Use Firefox on it for an hour everyday for a week and see if any problems occur. If this "Segmentation fault" appears while on LiveCD, I can assure you that it's a hardware problem.

Otherwise, it's software
And Conflicts in particular, since you say it was random.

Can you do a detail documentation of what you have running when the crash happens? Or maybe WHAT you were doing?

---

### Post by xeemo on 2010-03-22
It's happened to me about 10 times since I've started this thread and I'm running pidgin, firestarter, wicid, and gedit.  Don't think there's a conflict.

I'll see if I can try the live CD tonight, but it'll depend on if the drivers for my wifi card require a reboot.

---

### Post by fragos on 2010-03-22
In the case of Chrome there are stable and unstable testing versions. Unstable has a few more features and at this time does have some random crashes which I'm sure will be resolved as Chrome updates. I stick with Chrome as my default browser but have a copy of Epiphany available in the off chance it's needed. It seems odd that both Firefox and Chrome are sharing a problem unless of course the issue is in flash player.

---

### Post by xeemo on 2010-03-23
I went all morning without any crashes, but firefox just started crashing on me again.  I ran it with strace and got the following output:

Segmentation fault
[{WIFEXITED(s) && WEXITSTATUS(s) == 139}], 0, NULL) = 8230
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(139)   

not sure if that will be of any help.  I was watching a flash video at the time, but it has crashed without any scripts running as well.

---

### Post by jaoc223 on 2010-03-23
I'm running 10.04 beta1, chromium browser 5.0.307.11 (39572), I experience
periodic crashes.

---

### Post by TBABill on 2010-03-23
+1 on the 10.04 beta and Chromium in Lubuntu crashing. My experience with it is usually flash related. Pages such as those where you can select options seem worst for it. I do not get it often, but it has happened when on sites looking at vehicles and customizing it with the options I would want included. It's not as simple as checking a block and hitting update...the sites auto update with each selection. Ford and Mazda are sites I can think of that crashed during this process, but never consistently enough to say it was any specific step in the process. I just got the "aw snap" error and reloaded and everything was fine then.
 
I am running the daily updated Chromium so I expect it to happen frequently. When I want it more stable I jump on Firefox and it's only dumped 1 or 2 times on me so I am content going that route. Just hoping it does not progress into Firefox 3.6 on me.

---

### Post by dosox on 2010-03-23
Don't know but my firefox went okay after various ubuntu updates..

---

### Post by fragos on 2010-03-23
I'm running Chrome 5.0.356.2 which rarely crashes. Rather than the tab I'm on going "AwSnap" all the tabs seem to fail. When I tell tabs to refresh they frequently come up OK. I might be mistaken but Flash doesn't seem to be the cause of my occasional "AwSnap".

---

### Post by frogzombie on 2010-04-05
I'm running 10.04 beta x86 with chrome and firefox from the Software center just to be extra cautious. Flash is crashing my browsers. They will go to the initial site, but crash shortly after.

I did an apt-get update/upgrade today. It was the first since I installed ubuntu 10.04 2 weeks ago. 

I've tried reinstalling everything, apt-get remove --purge.

Any suggestions?

EDIT: I have fixed it by apt-get remove -- purge firefox, chrome, and flash. then apt-get install firefox, then adobe-flashplugin, then chrome.

---

### Post by Jose Consuervo on 2010-04-28
Okay, I have been making posts, and reading various threads, and haven't found a solution. I am running 10.04, 64 bit Kubuntu. I seem to be getting the crashes, and they always seem to be related to flash. Until just now the crashes seemed to be only happening on gmail, and even then they were unpredictable. But I ran firefox in gdb, and here are some of the outputs I was getting. 

> (firefox-bin:5512): Gdk-WARNING **: XID collision, trouble ahead


This is one of them, it comes up about 15 million times, no matter what I am doing. I haven't been able to find the reason for this warning, but it seems unrelated to the crashing.

> /home/jose/.esd_auth: File exists


This is another that I believe is unrelated, as it comes up constantly, no matter what I do. I have read and found that it has something to do with esd, which is some sort of sound server? I can't really remember.

> Program received signal SIGSEGV, Segmentation fault.
0x00007fffd5f4aa42 in ?? () from /usr/lib/mozilla/plugins/libflashplayer.so


These are the final two lines from my debug. This made me think it was the plugin, so I have done several things, including reinstalls of firefox, and redownloads of the 64 bit plugin, and deleting it, and trying the 32 bit plugin, all of which have no apparent effect on the crash.

I hope this helps,
Jose Consuervo

---

