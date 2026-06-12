---
title: "virus and shut down"
date: 2011-02-28
forum: General Help
---

### Post by rahulbest on 2011-02-28
1>i m having duel boot win xp and ubuntu...most of internet downloading i do from ubuntu....
i know windows virus dont run on ubuntu even they come but what about my windows partition.....is that gets affected????

2>how to shut down computer from terminal???i want to specify time also.means at 12pm it should get shutdown something like that....but before getting shut down it should close all application if possible....is there anything to do all that??

---

### Post by zenwalker on 2011-02-28
1. When a virus can run (gets executable) then only any thing in the system gets affected. So yourself claimed that virus doesnt affect ubuntu, so relax your true. It can go worse, unless you voluntary executes unknown programs on your system or use system as root account.

2. Shutdown -t command helps you. But i dont know if you can close all apps successfully. May be you need to send a DBUS message for that.

---

### Post by nomko on 2011-03-01
[QUOTE=rahulbest;10507339]1>i m having duel boot win xp and ubuntu...most of internet downloading i do from ubuntu....
i know windows virus dont run on ubuntu even they come but what about my windows partition.....is that gets affected????
[QUOTE]
 
Any virusses, spyware, malware ment for Windows systems doesn't have any effect on Linux systems. Main reason for this is the difference in architecture between the 2 operating systems. And 99.9% of all virusses/malware/spyware are mainly build for Windows systems due to the fact that most computers run on Windows. And that Windows isn't half as secure as Linux is. If you get a virus on your system, don't panic, it won't harm your Linux system. The only problem you get with Windows virusses is when you have a Windows formatted drive mounted **AND** placed the infected file on that drive! As long the virus is still on your Linux system, it won't harm your Windows formatted drives since a Windows program and/or Windows virus/malware/spyware cannot run on a Linux system. If you have a dualboot system between Ubuntu and Windows there's nothing to worry about as long as the Windows partition is not mounted and the file containing the virus/malware/spyware isn't moved or copied to that Windows partition. Again, as long as it stays on your Linux system/partition, it can't do anything because stuff programmed for Windows and Windows architecture cannot run on Linux systems/architecture. But if you mount your Windows drive and/or partition and move/copy the file to that drive/partition then you will get serious problems.

---

### Post by rahulbest on 2011-03-01
en 1 can tell me this in detail????
2>how to shut down computer from terminal???i want to specify time  also.means at 12pm it should get shutdown something like that....but  before getting shut down it should close all application if  possible....is there anything to do all that??

---

### Post by donkyhotay on 2011-03-01
I think there are other ways of shutting down a computer from CLI but this is what I use

for shutdown
```
sudo telinit 0
```
for restart
```
sudo telinit 6
```

---

### Post by soullessgod on 2011-03-01
Gshutdown
 [http://gshutdown.tuxfamily.org/en/download.php](http://gshutdown.tuxfamily.org/en/download.php)

---

### Post by oldos2er on 2011-03-01
> **rahulbest said:**
> en 1 can tell me this in detail????
2>how to shut down computer from terminal?

```
man shutdown
```

---

### Post by rahulbest on 2011-03-02
sudo shutdown +1

i used it for shutdown.....desktop screen shut down but next ubuntu screen remained for long time and pc would not get shut down completely......
i think complete shutdown from terminal is not possible....no1 gave me exact command.....
if anyone knows plz let me know...
thanks in advance....

---

### Post by robro on 2011-03-02
sudo poweroff
thats what i use when something goes wrong :)
although idk how to run it at a specific time....

---

