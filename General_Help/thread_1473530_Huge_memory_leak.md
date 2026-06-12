---
title: "Huge memory leak"
date: 2010-05-05
forum: General Help
---

### Post by HolidayQueen on 2010-05-05
Normally my computers bootup with an initial ram usage of 112~mb. Though, every second or third boot, it will boot up with approximately 400mb of ram...This seems to happen across all my computers (though ive since changed my tower to another dist since it really can't afford the waste). When i open up system monitor i find no indications of where the extra 300mb of ram is going.?

Running 10.04.

---

### Post by StuartN on 2010-05-05
> **HolidayQueen said:**
> When i open up system monitor i find no indications of where the extra 300mb of ram is going.?

**ps -vax** will show memory usage (%) for every running process.

---

### Post by HolidayQueen on 2010-05-05
tried that. I still get no clear indication of where the extra 300mb of ram is going.

I just ran update manager, and when the computer rebooted, it was at 394 ram at startup.

Like i said, i can reproduce this exact behaviour on my tower, the only diference is, my tower only has 512ram to begin with, so it took nearly 5 whole minutes for the DE to load up.

---

### Post by StuartN on 2010-05-05
> **HolidayQueen said:**
> Like i said, i can reproduce this exact behaviour on my tower, the only diference is, my tower only has 512ram to begin with, so it took nearly 5 whole minutes for the DE to load up.

512 MB is a very small amount of ram for a GUI desktop.

You should be able to track down the usage if it changes between boots, and is repeated.

The commands free, ps aux and lspci -v should reveal the use. For instance some graphics cards use ram and lspci -v will list the usage. lspci -v | grep -i memory will list all hardware ram use.

---

### Post by jocko on 2010-05-05
It's probably not a memory leak. It's ureadahead that reprofiles the boot process everytime you have installed an update that affects the boot process.

---

### Post by Grenage on 2010-05-05
Are you sure it's actually being used, and not just being 'looked after'?

---

### Post by iponeverything on 2010-05-05
Can you post a "free" for both the states.

---

### Post by HolidayQueen on 2010-05-05
booted at 112mb ram :
             total       used       free     shared    buffers     cached
Mem:       1018092     387664     630428          0      48012     201456
-/+ buffers/cache:     138196     879896
Swap:      1429776          0    1429776



will now attempt to reboot at 300+ ram

---

### Post by HolidayQueen on 2010-05-05
Odd i suddenly can't seem to reproduce the behaviour (after a dozen reboots). I did remove xubuntu desktop though, do you think that might have been causing this?

ill keep trying to make sure this doesnt happen again, if it does, ill post the results of free on here.

---

### Post by HolidayQueen on 2010-05-05
tower @ boot:
freddy@Jerry:~$ free
             total       used       free     shared    buffers     cached
Mem:        442408     436624       5784          0       5608      34424
-/+ buffers/cache:     396592      45816
Swap:      2152700      17816    2134884

---

### Post by Kenda on 2010-05-06
Sometimes when I boot up memory usage is about 1.5Gib with no explanation.If I restart the memory usage is about 500mib - the same programs are running, so why is the memory usage so dramatically different. Is this the Ureadahead issue?

---

