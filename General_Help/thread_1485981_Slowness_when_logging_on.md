---
title: "Slowness when logging on"
date: 2010-05-17
forum: General Help
---

### Post by ipefix on 2010-05-17
Hello,

I own a laptop Acer Aspire 5633 WLMi on which I installed Ubuntu 10.04 in order to get familiar with a Linux environment. The problem is that it gets slow during startup, more specifically just before choosing my username. I mean it starts well till Grub is displayed and then, between Grub screen and log on screen with the default wallpaper, I have to wait about 20 to 30 seconds before I can choose my session and enter my password:???: I already had this problem with Ubuntu 9.10 and didn't find a solution, so I waited for Lucid to be released in the hope that it would get solved by itself but... it didn't! The thing is that I also ran previous version of Ubuntu earlier (7.10 and 8.04 if I remember well, it was a couple years ago) without any problem.

Btw, I already tried a clean (re)install of the OS :p

Does anyone have an idea ? I already asked the french community but I didn't get an answer :-\"

Anyway, thanks in advance for your answers :)

---

### Post by _0R10N on 2010-05-17
You should take a look at the startup applications list and the services starting up, also. There's a lot of apps that can help you out configuring your system's boot process, like Bootup-Manager
```
aptitude install bum
```
or rcconf
```
aptitude install rcconf
```

---

### Post by ipefix on 2010-05-19
I installed bum but I'm not sure of what could be removed there (if that's what I'm supposed to do to see if logging on still freezes :p ). Anyway, I deleted the things I suspected to not be needed and made a reboot but the logon screen with usernames still takes about half a minute to appear :(

If it helps : it also takes 20 to 30 seconds between me hitting Enter after entering my password and all the bars (top and bottom) appearing.

---

