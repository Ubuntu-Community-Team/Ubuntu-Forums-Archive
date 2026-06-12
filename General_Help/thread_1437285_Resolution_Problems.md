---
title: "Resolution Problems"
date: 2010-03-23
forum: General Help
---

### Post by hugoread on 2010-03-23
Hello all,

I'm new to Ubuntu and really like it so far, having come from a PC background up to now.  I've installed it on my Acer laptop and all is well there.  However, on my desktop, the screen resolution doesn't match the Ubuntu desktop and fonts and graphics are very blurry.  The hardware I have is:

HP Compaq dx2450 micro-tower FE281EA
Samsung 23" widescreen monitor, native resolution 1680x1050

When I check the resolution using System > Preferences > Display it says that indeed I'm using 1680x1050, which should be correct.  However, the bottom of the Ubuntu desktop is cut-off, below the bottom of the screen, so I can only see the very top edge of the bottom panel.  The top panel is also slightly cut off, missing about the top 20% of the panel. Left and right seem to be in line OK.  The resulting blurriness of fonts makes it fairly unusable until I get it fixed.

I've searched fairly extensively and I realise there are other threads on this so sorry for posting again, but they all seem to be slightly different problems and all the responses are fairly or very technical.  Maybe I can't avoid a technical solution and getting my hands dirty with a terminal prompt, but I'm hoping I can fix this without resorting to stuff I don't understand and might get wrong.  I'm a technically minded end-user but not a unix guy.

Any help much appreciated,
Hugo Read.

---

### Post by cogier on 2010-03-23
Sounds like a driver issue. To find which card you have without using the command line....From the Ubuntu Software Centre type "hardinfo" in the search box and install the "System Profiler....." that appears. 

Once installed run the program Appliactions>System Tools>System Profiler and Benchmark.

Select the Display option on the left and scroll to the bottom of the right pane. Your card will be listed there.

You should then look around for a suitable driver or solution to your problem.

---

