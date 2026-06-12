---
title: "How do I find what's causing a system crash?"
date: 2012-07-12
forum: General Help
---

### Post by savvasandreas on 2012-07-12
Hello,

I have upgraded to Ubuntu 12.04 and although I like it a lot  ever since the upgrade my system has been sporadically (but consistently) crashing. 
And the way it crashes is by completely and without any prior warning switching off as if I suddenly unplugged from the wall..

I read somewhere this might be caused by faulty hardware (memory, motherboard) so I ran MemTest86+ for several hours (~7) but it didn't report any errors.

Any ideas as to how I could investigate what is causing this issue which has made my system very unstable and unpredictable?

Thanks,
Savvas

---

### Post by Habitual on 2012-07-12
What do the logs say?

---

### Post by savvasandreas on 2012-07-12
Hello,

Thanks for your reply. 

Which logs would log this type of failure?

Thanks,
Savvas

---

### Post by Habitual on 2012-07-12
terminal > 
```
grep [COLOR=Red][COLOR=Black]-i[/COLOR] keyword[/COLOR] /var/log/* -R | less
``` where [COLOR=Red]keyword[COLOR=Black] would be whatever you suspect is causing the issue, [/COLOR][/COLOR]
or 
```
dmesg
``` may yield clues

---

### Post by savvasandreas on 2012-07-12
Great, thanks very much!

I'll go through all logs which seem like they would have error details but do you think the os would have the chance to log anything if it s being shut-down in such a brutal way?

Thanks,
Savvas

---

### Post by dino99 on 2012-07-12
if its a real crash, then it is logged into /var/crash/
then you can right click on it and select "report this issue" to file a bug on launchpad

---

### Post by teward on 2012-07-12
If the crash isnt caused software side, but say a thermal overheat and a thermal-shutdown, that'll be in the BIOS, the OS will show that it just received a shutdown command from the BIOS/hardware.  (A "crash" is not necessarily a true crash)

---

### Post by savvasandreas on 2012-07-12
Thanks very much all for your replies.

/var/crash has a couple of files but they are related to some program which keeps crashing but don't think it's taking the whole os down with it..

Thomas, it looks like it's a thermal issue like you suggest. Is there a log file which would record such an instruction (BIOS --> OS)? 

Thanks,
Savvas

---

### Post by dino99 on 2012-07-12
> **savvasandreas said:**
> Thanks very much all for your replies.

/var/crash has a couple of files but they are related to some program which keeps crashing but don't think it's taking the whole os down with it..

Thomas, it looks like it's a thermal issue like you suggest. Is there a log file which would record such an instruction (BIOS --> OS)? 

Thanks,
Savvas

possible logged errors inside .xsession-errors (/home, ctrl+h to unhide it)

about thermal issue: is this system overclocked ? or dusty ? is the fan blowing ?

---

### Post by savvasandreas on 2012-07-12
> **dino99 said:**
> possible logged errors inside .xsession-errors (/home, ctrl+h to unhide it)

about thermal issue: is this system overclocked ? or dusty ? is the fan blowing ?

.xsession-errors has logged a number of errors mostly related to missing css files and incomplete HTTP requests but none related to a shutdown..

About overheating, the fan seems to be working but I have noticed it is spinning a bit faster after upgrading to 12.04. 
Are you aware of any workarounds (e.g make the fan spin faster)?

Thanks very much.

---

### Post by charlyoleg on 2012-07-14
I have also random and consistent crashes on my new laptop. They append during large quantity of file copy or transfer. For example crashes occur when I'm using rsync, cp, mv or diff -rq. If I copy more than 20G, I have more than 90% chance that the crash occures. Crash can have different looking: Part of the graphic interface is not responding, screen freeze, dmesg display, black screen or shutdown. I have tried several hard disk configuration: mechanical hdd + ssd (wished configuration), only ssd, only mechanical hdd. The crashes occur for all those configurations.
In the bios, I had: sata mode: AHCI mode. I switched to sata mode: IDE mode. I still have the crashes.
How can I check if it is a hardware or software issue?

---

