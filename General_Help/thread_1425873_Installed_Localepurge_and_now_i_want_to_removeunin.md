---
title: "Installed Localepurge and now i want to remove/uninstall/disable the program"
date: 2010-03-09
forum: General Help
---

### Post by Nicksin on 2010-03-09
as much as i am one for saving space and throwing out the trash. i myself am new to the linux community but prefer it over anything out to this date. now my problem is the fact that I DO NOT WANT THIS program (localepurge) running on my system. i look and did everything i could. note : i am a noobie. when i config the program from the start i told it NO don't delete anything. and now that i have done some reading i do not want it working period. i could not find a way to disable or uninstall localepurge. if anyone is willing to help me solve my problem i'd appreciate it. :D

---

### Post by sparky-steve on 2010-03-09
2 choices

1, at the command line, type
```
sudo apt-get remove localepurge
```

2, open Synaptic Package Manager, search for localepurge and select complete removal.

Synaptic Package Manager is found in System, Administration.

Hope that helps

SS

---

### Post by Nicksin on 2010-03-09
thank you, helps alot.

with that said. i did what you mentioned. seems to be uninstalled but this error came up

[IMG]http://img717.imageshack.us/img717/2339/26498999.png[/IMG]

shall i just ignore this?

---

### Post by sparky-steve on 2010-03-09
That error is quite common, according to google.

You could spend time chasing it, but if I were you, I'd make sure that the end result is good (ie, it's no longer installed/working) and if so, leave it be.

You could try

```
sudo dpkg -P localepurge
```

in a terminal and see if that gives away any clues.

Also, just to be safe, check there are no problems in general by doing this in a terminal:

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

With the latter, if there are packages to be upgraded, for now, select no - just check for any obvious errors related to localepurge.

I'm grasping a little at straws here, as I've not come across that problem in a long time.  But I do believe that you should be OK now.

Cheers

SS

---

### Post by mkvnmtr on 2010-03-09
When I uninstalled localpurge by the command line it offered me the chance to reinstall everything it had uninstalled. I said yes and I have had no further trouble. They warned me that the package was kind of buggy and indeed it was. The reinstallation of the language packs it removed seems to be critical.

---

