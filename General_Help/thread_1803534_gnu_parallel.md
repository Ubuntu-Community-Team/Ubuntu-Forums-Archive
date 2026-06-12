---
title: "gnu parallel"
date: 2011-07-13
forum: General Help
---

### Post by sidman on 2011-07-13
Hi, 
   I have quite a specific problem actually, I'm new to Ubuntu forums and didn't know where to post this.
   I just installed GNU parallel on my Lenovo ThinkPad T420i laptop (Intel i3 quad-core) running 64-bit Lucid. I'm trying to run an executable called 'P2PMisorientation' on multiple files. Halfway through the run I get a broadcast message from root saying that "the system is going to halt NOW!". I tried running it in run level 3 (non-graphical login) but I have the same problem. My code is: 

[FONT="Courier New"]ls shifted_*.mic | /usr/bin/time parallel ./P2PMisorientation z1_mis.mic {} {}.MIS
[/FONT]

Here the files 'shifted*.mic' are the input files. Can anyone tell me why I'm getting that broadcast message? Any help at all would be appreciated.
   Thanks!

---

### Post by Ole Tange on 2011-07-14
> **sidman said:**
> Hi, 
   I just installed GNU parallel on my Lenovo ThinkPad T420i laptop (Intel i3 quad-core) running 64-bit Lucid. I'm trying to run an executable called 'P2PMisorientation' on multiple files. Halfway through the run I get a broadcast message from root saying that "the system is going to halt NOW!".

You code is fine. My guess is that your laptop has poor cooling and that it is shutting down because it is too hot.

Try running 8 burnP6 (8 = 4 cores + hyperthreading): 
```

aptitude install cpuburn;
nice burnP6 & nice burnP6 & nice burnP6 & nice burnP6 & nice burnP6 & nice burnP6 & nice burnP6 & nice burnP6 &
```and leave that running for a whole day. If you laptop does not shutdown by this, then it is probably not cooling that is the issue.

---

