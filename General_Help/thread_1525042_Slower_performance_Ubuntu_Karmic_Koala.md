---
title: "Slower performance Ubuntu Karmic Koala"
date: 2010-07-06
forum: General Help
---

### Post by acrocephalus on 2010-07-06
Hello!
Lately I have noted a decrease on the performance of my Ubuntu Karmic Koala 64 bits installation. It takes longer times to open applications and documents and sometimes the windows fade to grey and I have to wait. Can anyone give me some hint on where to start looking for a solution?
Cheers!

Dani

---

### Post by nacho32 on 2010-07-06
you could try going in system pref start up and turning a few thing off you don't need running, and look at system monitor and see whats running, look at the ram usage. I think a average would be a round 200 megs running on normal Idle

---

### Post by prshah on 2010-07-06
> **acrocephalus said:**
> give me some hint on where to start looking for a solution?

Step 1) If you have 1GB or over of RAM, the "swappiness" setting can be adjusted for more suitable performance. Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo sysctl -w vm.swappiness=20
``` Then use the machine for a while and see if it's OK. If you feel it's OK, then post back for how to make the change permanent. 

Step 2) HDD problems (logical, not physical) can cause a slowdown. Give the command```
sudo touch /forcefsck
```, then reboot to trigger a diskcheck. While doing this should cause no problem, you do this at your own risk. You may want to wait for someone else on the forums to agree that this command is not malicious.

Step 3) Check if any programs are (over)using the CPU; the simplest way is to run the "top" command from a terminal, and then study the first few programs for a few mins. Look at the "CPU(s)" line and the "%CPU" column for CPU usage details. If you find programs that are using 100% (or 50% if you are using Dual Core CPUs) consistently, kill them, and see if your computer is more responsive.

You can do the above steps in any order you like.


Please post back with results and details for more possible troubleshooting steps.

---

### Post by philinux on 2010-07-06
> **acrocephalus said:**
> Hello!
Lately I have noted a decrease on the performance of my Ubuntu Karmic Koala 64 bits installation. It takes longer times to open applications and documents and sometimes the windows fade to grey and I have to wait. Can anyone give me some hint on where to start looking for a solution?
Cheers!

Dani

Computer specs?

---

### Post by acrocephalus on 2010-07-06
Hello!
I have tried the first option suggested by prshah, and it seems that the computer works better. How can I make it permanent? The, I have run the "top" command and I have seen that google chrome is eating almost 50% of my RAM memory (1GB out of 2GB). Is there anything I can do?
Cheers!

Dani

---

### Post by nacho32 on 2010-07-06
use Fire Fox or Opera

---

### Post by philinux on 2010-07-06
> **acrocephalus said:**
> Hello!
I have tried the first option suggested by prshah, and it seems that the computer works better. How can I make it permanent? The, I have run the "top" command and I have seen that google chrome is eating almost 50% of my RAM memory (1GB out of 2GB). Is there anything I can do?
Cheers!

Dani

[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by warfacegod on 2010-07-06
I just used Bootup Manager on an old AMD 1.1 GHz with 768 MB RAM running Karmic with LXDE. It actually turns things off, unlike Startup Apps. I was able to cut the boot time by 2/3. Needless to say, if things aren't starting on boot, they won't be running in session either unless you turn them on.

```
sudo apt-get install bum
```

---

### Post by prshah on 2010-07-06
> **acrocephalus said:**
> I have tried the first option and it seems that the computer works better. How can I make it permanent?

Edit the file /etc/sysctl.conf ```
gksudo gedit /etc/sysctl.conf
``` and add a single line to the end of the file (don't change any other contents)```
vm.swappiness=20
``` Then save and exit. Now, the setting will persist across reboots.

---

