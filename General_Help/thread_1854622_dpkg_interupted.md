---
title: "dpkg interupted"
date: 2011-10-04
forum: General Help
---

### Post by stillcen on 2011-10-04
Greetings;

i was using the sypaptic package manager to install a typing game for my daughter when she stepped on the power strip, specifically the off  switch.

i  go back to the synaptic package manager and get




E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




i went to terminal and attempted to comply.  i failed, not suprizingly since i only have the vaguest idea as to what i am actully doing.

thanks

stillcen

---

### Post by wildmanne39 on 2011-10-04
Hi, run these commands one at a time and if you get errors post all of them here.
```
sudo dpkg --configure -a 
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by drs305 on 2011-10-04
So you opened a terminal and ran the following?

```
sudo dpkg --configure -a
```

You should have been asked for your password, which you type without getting any feedback, then press ENTER.

What happened next? If it failed, you should have received additional error messages.

---

### Post by stillcen on 2011-10-04
Great; Thanks folks; 


All FIXED,

so... now how do i mark this thread as FIXED as to not use anybody elses time?


stillcen

---

### Post by wildmanne39 on 2011-10-04
Hi, I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by garvinrick4 on 2011-10-04
> **stillcen said:**
> Great; Thanks folks; 


All FIXED,

so... now how do i mark this thread as FIXED as to not use anybody elses time?


stillcen Upper right in Thread tools and you are not wasting anyones time. When you got
a problem you just ask away. That is what these Forums are all about.
 EDIT: Opps Wildemanne39 has already answered, he is quick, quick on the draw.

---

### Post by stillcen on 2011-10-04
every time i ask a question  here,  i just laugh. 

i post an issue and in less time than i would spend on hold to a corporation, i have three responces all which helped out perfectly.


thanks much

stillcen

---

### Post by wildmanne39 on 2011-10-04
Hi, your welcome!

---

