---
title: "Conky frequency scaling bar, how?"
date: 2011-03-21
forum: General Help
---

### Post by bazcor on 2011-03-21
Hello and thanks for reading this. No biggie but how can I show a bar with a cpu frequency scale. My CPU varies its freq between 0.8 and 3.3 GHZ and I would like a bar to show this, is it possible?

I have been trying the 'execbar' command with freq_g but I don't really know what I'm doing and have had no luck at all.

Thanks again ... Barry

---

### Post by Paulgirardin on 2011-03-21
CPU Frequency Scaling Monitor in the panel.
Right click on the panel,select "add to panel",add freq monitor.
Multiple instances can be added for individual cores - right click on the cpu monitor and select preferences to allocate each monitor to a different core.

---

### Post by Lianli on 2011-03-21
Also the cores are numbered starting from 0. I have 8 cores and like to see them as 1-8. So i label them starting with core1, but the fist freq monitor would be set as core0, so i see cores 1 thru 8 but like under the hood it's cores 0 thru 7 if that makes sense

---

### Post by bazcor on 2011-03-23
Thanks for the replies, I have settled (for the moment) with having the frequency scaling widget in the top bar. If I knew more about conky though I'm sure that it would be possible to have a scaling bar in the conky display. 

Guess I'll go on looking ... Thanks again .. Barry

---

