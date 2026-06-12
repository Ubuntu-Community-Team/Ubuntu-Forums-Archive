---
title: "start a realtime kernel without realtime features enabled"
date: 2011-02-23
forum: General Help
---

### Post by gnumark on 2011-02-23
Hi all,

there is a way to start a realtime kernel (in my case 2.6.31-10-rt for 10.04) without the realtime feature enabled?

it exist something like -nort as a boot parameter?

i searched into the rt kernel patch and i can't find anything, neither googling it.

The best i could do is to get all the process with SCHED_FIFO and set it to SCHED_OTHER

for in in `ps ax |awk '{print $1}'`; do chrt -p $in >>fifo_sched; done

for i in  `grep SCHED_FIFO fifo_sched |awk '{print $2}' |awk -F "'" '{print
$1}' |sort -g -r`; do chrt -o -p 0 $i; done

but that's not the perfect solution cause i keep all the threaded kernel process in the ps and that doesn't really delete the realtime feature, but is only a stupid workaround.

I need that for testing purpose.

Thanks in advance

---

