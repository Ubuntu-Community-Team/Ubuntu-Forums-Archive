---
title: "Lots Memory"
date: 2009-08-23
forum: General Help
---

### Post by H4F on 2009-08-23
When I swich on ubuntu it uses around 350 MB out of 2 Gb Ram I have.
After working some time around 2 days I am noticing slowdown of the system.
Checking the system process gives me some info:
pingin uses around 15% of memory
firefox 12-35 % some time
other apps as rythmbox,transmission,skype etc does not use much
my 1170 out of 1977 mb are constantly used
500 mb swap out of 3 Gb is used.

thats fine firefox is known to memory leak.just to restart it once in a while

but common some simple IM as pidgin taking 12 % of memory . and constantly increasing.any way I can restart it too once in 2 days.

after closing everything possible I get
1300 mb out of 1997 MB ram
may be 2-300 mb out of 33Gb swap
 
Any way. Even If if close ALL my application I will not get used of 350 MB of Ram as in clean restart. So the question is who is stiling my RAM constantly ?

I am getting angry when I need to restart cause my systems becomes unresponsive cause of memory.

P.S no other processes are taking memory. and memory is still allocated to something.
Am I doing something wrong ?

---

### Post by blueridgedog on 2009-08-23
As has been said on this forum many times, empty memory is wasted memory.  Even if you close all applications, if there is room in memory, the system will leave many items cached.  The system wants to fill your memory with the things you are likely to run/open/view etc.

---

### Post by oldos2er on 2009-08-23
If you want to reduce swapping, you'll need to change your /etc/sysctl.conf file, and add a line
**vm.swappiness=5** for example. Values can be set from 0 (no swapping) to 100; I think the default is 60. Reboot after making any changes.

---

### Post by H4F on 2009-08-23
I have done that already . my vm.swappiness in /etc/sysctl is 10

---

