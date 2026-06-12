---
title: "Firefox won't start"
date: 2011-03-22
forum: General Help
---

### Post by michiganitis on 2011-03-22
Ok...so here's what happened...

I wanted to restore firefox to is fresh install default settings. So I opened up a terminal and typed:

rm -Rf .mozilla/firefox/*.default

I accidentally somehow did it twice. I tried to start firefox back up. I get this message:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

Firefox was actually closed. But, I decided to restart my computer. Then I tried to start Firefox. Same message. I went to the Ubuntu software center...removed Firefox...re-installed firefox...restarted...same message.

What on earth did I do and how do I fix it?

---

### Post by Script Warlock on 2011-03-22
open terminal check if you have created profiles and remove them except the default.

firefox -profilemanager

---

### Post by Soul-Sing on 2011-03-22
> "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."


normally you could kill the firefox proces: ```
killall firefox
```
but now you had a reinstall/reboot/etc.
i really don't know how to solve this. maybe it is present as zombie proces now.
```
top
``` in the terminal shows running processes

---

### Post by michiganitis on 2011-03-22
> **Script Warlock said:**
> open terminal check if you have created profiles and remove them except the default.

firefox -profilemanager

yup, default is the only profile. and when i click the button that says 'start firefox', i get the following message:

"Firefox cannot use the profile "default" because it is in use.

To continue, close the running instance of Firefox or choose a different profile"

but firefox is not open. it does it even if computer is restarted.

---

### Post by lithopsian on 2011-03-22
Firefox profiles don't include files called *.default.  What else did you do?

That message is usually caused by the presence of a lockfile.  Since you want to revert to a clean profile anyway, I would suggest just deleting your entire .mozilla/firefox diretory.  Alternatively start with the -P option and create a brand new profile.

---

### Post by michiganitis on 2011-03-22
> **leoquant said:**
> normally you could kill the firefox proces: ```
killall firefox
```
but now you had a reinstall/reboot/etc.
i really don't know how to solve this. maybe it is present as zombie proces now.
```
top
``` in the terminal shows running processes

```

Swap:  4808700k total,        0k used,  4808700k free,   516744k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1205 root      20   0 83048  29m  12m S    3  0.8   0:37.70 Xorg               
 2692 juho      20   0 94172  13m  10m S    2  0.4   0:01.12 gnome-terminal     
   16 root      20   0     0    0    0 S    0  0.0   0:01.93 events/1           
  369 root      20   0     0    0    0 S    0  0.0   0:00.63 usb-storage        
 1776 juho      20   0 97.9m  10m 8408 S    0  0.3   0:00.85 gnome-settings-    
 2734 juho      20   0  2620 1148  840 R    0  0.0   0:00.19 top                
    1 root      20   0  2888 1708 1244 S    0  0.0   0:00.79 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.13 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.26 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2
```

and i just tried 'killall firefox'. still get the same error.

---

### Post by michiganitis on 2011-03-22
> **lithopsian said:**
> Firefox profiles don't include files called *.default.  What else did you do?

That message is usually caused by the presence of a lockfile.  Since you want to revert to a clean profile anyway, I would suggest just deleting your entire .mozilla/firefox diretory.  Alternatively start with the -P option and create a brand new profile.

that's the only command i ran...twice, by accident. before running it, firefox worked. after that, firefox is busted. even after removing and reinstalling via ubuntu software center. what do you think i should do?

just tried 'firefox -P'...same error.

---

### Post by michiganitis on 2011-03-22
Nevermind. I just deleted the default profile...created a new one called default. Fixed.

Odd. Whatev!

---

### Post by pqwoerituytrueiwoq on 2011-03-22
firefox's process is called firefox-bin
so to kill it it is 
killall firefox-bin

---

