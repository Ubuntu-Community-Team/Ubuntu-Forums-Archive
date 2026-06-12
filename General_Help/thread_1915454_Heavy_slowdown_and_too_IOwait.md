---
title: "Heavy slowdown and too IOwait"
date: 2012-01-26
forum: General Help
---

### Post by ginlemon on 2012-01-26
Hi guys,
I'm having a lot of problem with my new notebook, acer timelineX 4820tg with i5 processor and 4gb ram ddr3. Ubuntu run worst than my older pc 1,6ghz core duo with 3gb ram ddr2. There's a general problem of latency, when i click gedit or terminal icon it requires some second to open the window, the system freeze often even if i just open nautilus and some google-chrome tab the ram usage grown easly to 93%! (only nautilus get from 500 to 1,5gb ram!!!) It's an unbearable situation...

Now i just try to merge some jpg in a pdf with "convert" from terminal and it completely freeze the system! (only 3 tabs chrome on background)
Here a photo (i couldn't take a screenshot obviously...)
[IMG]http://www.ginlemonblog.com/carica/uploads/C360_2012-01-26-10-49-30.jpg[/IMG]
Ok, maybe "convert" required too many resources but it's unbelievable that Ubuntu gets KO for such so little...i think it may depend from my configuration, but i can't understand where the problem is...

I'm using Ubuntu 11.10 64bit, with Unity.

---

### Post by ginlemon on 2012-01-28
bump!

---

### Post by parsim on 2012-05-08
Sorry for the gravedig, but...

First of all, you have a RAM problem. In my experience, almost all disk problems are really RAM problems: you see huge disk activity, but it's happening because the machine can't fit enough data in RAM and needs to keep temporarily shoving it to disk and reading it back again. Your 'top' output shows all memory being used, with basically nothing in either 'free', 'cached', or 'buffers', and 500MB or so of swap employed. This is a really bad situation; no machine will run well in those circumstances. If you ran 'vmstat 5', you would no doubt see big numbers in the 'si' and 'so' columns, showing data being swapped in and out.

A healthy system won't touch swap at all. To fix this, you either need more RAM or to stop running so many processes at once that use lots of RAM. 'convert' is using 2GB, according to your 'top' output, which is an enormous amount and half your system total. In fact, it's so much I wonder if it's a bug in 'convert.' But anyway, that's why things bog down when you run that.

Now, if you didn't have a RAM problem, here's how you would diagnose that 'iotop' output. It shows 15M/s being read, which is an awful lot, and 10.57M/s of that is because of chrome. (Most of the rest is probably swap activity.) You would find it useful to enter iotop and use the left-arrow key to highlight the 'DISK READ' column, which will sort processes by the how much they're reading.

Your pic also shows writes of 5M/s, which is a lot, so maybe it's that (or a combination of the two). It's impossible to see which process is generating writes, though, because you haven't sorted by that, and all processes on screen are showing 0B/s.

It's also a little hard to know for sure what's going on, because your pic is just one moment in time. Maybe it's not representative of your general lag situation.

But anyway, when you have a disk lag, run iotop (perhaps with '-d 3' so the numbers aren't flashing past your eyes, and/or '-a' to show accumulated totals), look up the top to see if you have high numbers for reads or writes or both, and use the arrow keys to sort by the appropriate column to figure out which process is causing that.

The 'IO' column can be misleading because it shows which processes are WAITING on the disk. This might be because they're doing something very disk intensive, or might be because something ELSE is doing something disk intensive, and they're in the queue.

Now I have a question for you: how on Earth did you get numbers in the SWAPIN and IO columns? This requires a particular kernel option be enabled which is [not on by default in Ubuntu](https://bugs.launchpad.net/ubuntu/+source/iotop/+bug/513127).

---

