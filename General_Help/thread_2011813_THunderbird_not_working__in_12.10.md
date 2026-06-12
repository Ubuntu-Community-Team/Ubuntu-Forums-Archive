---
title: "THunderbird not working  in 12.10"
date: 2012-06-27
forum: General Help
---

### Post by Peter J Cooke on 2012-06-27
Thunderbird crashes at start up or freezes and cannot get to read my mail,Everything else works ok so far in 12.04
I get the following error message.


Add-ons: [email]edsintegration@mozilla.com:0.3.9,messagingmenu@mozilla.com:0.9.3,globalmenu@ubuntu.com[/email]:3.2.3,{972ce4c6-7e08-4474-a285-3208198ce6fd}:13.0.1
BuildID: 20120615093033
CrashTime: 1340844975
EMCheckCompatibility: true
Email: <snip>
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1340440540
Notes: OpenGL: nouveau -- Gallium 0.4 on NVC1 -- 3.0 Mesa 8.0.2 -- texture_from_pixmap

ProductID: {3550f703-e582-4d05-9a08-453d09bdfdc6}
ProductName: Thunderbird
ReleaseChannel: release
SecondsSinceLastCrash: 649
StartupTime: 1340844968
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 13.0.1

This report also contains technical information about the state of the application when it crashed.


Urgent help is needed as I use the e mail for my medical updates and appointments

thank you

peter

---

### Post by zombifier25 on 2012-06-27
What Ubuntu are you using? The title says 12.10 but your post says 12.04.
Anyway, you can try launching it in safe mode and see if problem persists.
```
thunderbird -safe-mode
```

Another tip: NEVER post your email address online like that. Spambots lurk everywhere.

---

### Post by infinitezero on 2012-11-08
I had the same issue. After disabling Firetray it works just fine.

iz

---

