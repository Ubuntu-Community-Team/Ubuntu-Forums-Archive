---
title: "Why CONFIG_HZ=100 ? (Empiric study)"
date: 2010-11-12
forum: General Help
---

### Post by a-user on 2010-11-12
Well, i am not sure if this is the right forum for this, but i do not know where to discuss this else.

Now, the stuff was already many many many times discussed. Ubuntu had in previous version config_hz set to 250. beginning with lucid it was reduced to 100. the reason for this - as far as i discovered - is that due to usage of high resolution timers it is not needed for the kernel to periodically poll more often than this... at least theoretically.

old suggestions for setting this to 1000hz have several drawbacks, at least that's what i read. thus drawbacks are e.g. higher power consumption, slower loop throughoutput.

now, i made some test on my amd machine with the current kernel set to 100hz, set to 300hz and the current git kernel 2.6.37 with the same two hz settings.

the brief results are that cpu usage has  been reduced dramatically. idle load was reduced by 30-50%. firefox and its npviewer plugin process got also reduced heavy. the most reduction is seen for npviewer with over 60%.

the xorg process basically got cut by half too, sometimes even more.

and finally i mesured my power consumption over a day. for both kernel versions set to 300hz the power consumptions was mesureable lower than with 100hz.

oh and finally, as this is my htpc i observed that some kind of periodically video playback stuttering every .5 or 1sec that i used to have from time to time in xbmc and other players seems to have disapeared. could be related to the fact, that 300hz is a multiple of my 60hz vfreq.

now i am very curoius why not to increase the config_hz value again. it makes such a big difference. it seems that my results are not uncommon, as far as i discovered during my internet research.

so here is my suggestion: increase it to 300 for best balance in the default ubuntu desktop kernel.

p.s. for the interested ones: i tried the newest git kernel cause i was curious about the impact of removing the big kernel log. and it has quite a big positive influence. sadly, my dvb-s2 card (hauppaugue nova S2) needs big kernel log. without it i even don't get the modules. but the porting of all the code to not need BKL is early work still in progress. so patience ;)

---

### Post by a-user on 2010-11-13
i really would like to hear some input to this issue.

---

### Post by a-user on 2010-11-15
i additionally made some test with the full preemtion setting. but this didn't gave any noticeable improvement, instead throughput dropped a bit (as expected).

i still recommend the 300hz setting for any desktop, especially if used for multimedia playback. the impact of the 100hz setting is visible and mesureable.

---

