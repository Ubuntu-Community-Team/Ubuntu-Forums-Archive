---
title: "System lagging on battery, help"
date: 2012-06-30
forum: General Help
---

### Post by michalt on 2012-06-30
Hello, 

before submitting bug I would like to make sure it's not in my head. :)

Since upgrade to Oneiric I have problem with serious system slowdown when on battery power or when battery starts to charging. I tried a lot of the settings with laptop-mode with no success (though disabling power saving for MC and SMT scheduler seemed to help a bit).

The usually problem arises like that - I unplug cable and work with computer. After some time, system starts lagging, switching between windows is slow and everything takes longer. System is gradually less responsive while top doesn't sow any considerable load. Sometimes this slow down and lagging will not start before I plug power again - especially when battery is low already. After that the system is lagging and unresponsive until battery get to some 20-30 percent, then the system start working normally again.

Any idea? I tried everything I can image before posting this. I suspect now it can be some battery polling deamon though have no idea how to test the hypothesis.

My config is HP ProBook 4320s with i3 running Precise.

Will appreciate any hints.

---

### Post by dino99 on 2012-06-30
you should watch htop to see which process is too highly using either cpu or ram or both

have you refreshed your battery recently, if not do it via the bios

---

### Post by michalt on 2012-06-30
> **dino99 said:**
> you should watch htop to see which process is too highly using either cpu or ram or both

have you refreshed your battery recently, if not do it via the bios

No option to refrewsh battery in bios.

Tried htop and fount that any running application uses much more CPU than normally. If for example firefox or X uses some 20% normally, it will occuppy 80% percent during the time I experience lagging.

---

### Post by Redblade20XX on 2012-06-30
Did you do a fresh install  or an upgrade? Usually this stuff happens with upgrades because of carried over configuration files.

-Red

---

### Post by michalt on 2012-06-30
> **Redblade20XX said:**
> Did you do a fresh install  or an upgrade? Usually this stuff happens with upgrades because of carried over configuration files.

-Red

It's upgrade though I tried to run a system from the Live CD and even that very clean Live CD instance exhibited same behaviour.

---

### Post by michalt on 2012-07-01
Actually I strongly suspect these are two separate problems. One is the slowdown when running on battery and the second is slowdown when again on AC power.

While the slowdown on battery seems to be helped by deactivating SMT and MC scheduler and NMI watchdog powermanagement in laptop mode for temporal slowdown when attaching AC power again I have no solution.

From log I only notice that anacron tasks are launched every time power is connected. Can't be slowdown related to that?

---

### Post by michalt on 2012-08-26
So after some time I decided to follow advice and do a fresh install. It did help to some degree - now the problem is more reproducible and specific:

After about 3 minutes on battery power system becomes unresponsive. It's especially laggy during music and video playback (which get broken quickly). Htop shows more then 10 running processes in que and all core threads are running 100%. Though no extraordinary processes shows, just all the normal known processes eats much more resources then usually. Clicking icon, moving windows, everything is very slow and it gets just worse and worse. When AC power is connected back the system becomes normal in matter of seconds or sometimes a minute.

I tried a lot of the settings with laptop mode. Sometimes it seemed that I found the culprit but the second testing proved negative.

Only thing which did really help was acpi=off kernel option. With acpi=ht the problem got back. So I suspect multithreading kernel support, but I have no idea what to do about it. 

Any idea or recommendation, please?

---

### Post by michalt on 2012-08-27
Bumb bumb, at least some ideas for debugging?

---

