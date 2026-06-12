---
title: "ureadahead"
date: 2010-06-21
forum: General Help
---

### Post by whalogreg on 2010-06-21
I just have a general question about ureadahead. I understand that it is used to read files ahead during boot to speed up the process. I just recently installed bootchart and saw (if I'm reading the chart correctly) that ureadahead is running by itself for about fifteen seconds, and the rest of the processes take up about eight seconds after that. Is ureadahead supposed to run  by itself for so long? Is it using that time to speed up everything else? Fifteen seconds seems like a long time for something to run alongside nothing else at the time if it is supposed to speed up boot times.. My concern is that 10.04 is supposed to have improved boot times over 9.10, but in my case seems that it takes about five seconds longer than karmic did for me. I'll show my boot chart..

---

### Post by whalogreg on 2010-06-22
Better view of the bootchart..

---

### Post by whalogreg on 2010-06-24
::bump::

---

### Post by psusi on 2010-06-24
Yes, that is supposed to happen.  Laptops have very slow hard drives, hence, why it takes 15 seconds.

---

### Post by whalogreg on 2010-06-25
> **psusi said:**
> Yes, that is supposed to happen.  Laptops have very slow hard drives, hence, why it takes 15 seconds.

Just seems odd to me that karmic was consistently 5-7 seconds faster to boot when lucid is supposed to be quicker..

---

### Post by bwana on 2010-07-28
possibly discussed here? :
[http://ubuntuforums.org/showthread.php?t=1507610](http://ubuntuforums.org/showthread.php?t=1507610)

---

