---
title: "Strange 100% cpu spike about every 4 minutes"
date: 2010-12-23
forum: General Help
---

### Post by Lynx Phoenix on 2010-12-23
ok i'm worried about this a bit. occasionally, i get a strange cpu spike, going from ~50% for a second or two, then 1-2% then 100% for a bit less than it says on 50%. like, its going from 50, to 2 then jumps to 100 all within 2-3 seconds and using gkrellm i timed it (albeit crudely) to about 4 minutes between the spikes. there seems to be little noticable (if any) performance drop during the spikes (i havent noticed any that is) and otherwise the system runs quite perfectly.

i'm using maverick and neither gkrellm nor system monitor seemed to be able to catch the power hungry thread/process. so, using htop i got a couple of screenies and noticed that /usr/bin/perl pops up every time there is a spike. this started a couple of days ago and i didnt give it much attention but now its starting to worry me. in the meantime i havent done any hardware changes and the only things i've installed are some software on wine and a couple of random apps. ofcourse, any of these could be responsible but there was nothing perl related. also, ubuntu cant scale my cpu so its not the cores scaling down (and on my laptop there seems to be no overhead from the scaling anyway). i'm suspicous of some new firefox add-ons i've recently installed as well and i'm going to look into these as firefox-bin and the addon-container thing that firefox has are both regular turnups when i get 50% spikes. what worries me is the 100%, which is more like a deep system thing.

here are the screenies i got from htop (as links so as not to make the post huge):

[http://img220.imageshack.us/i/perl.png/](http://img220.imageshack.us/i/perl.png/)
[http://img708.imageshack.us/i/perl2.png/](http://img708.imageshack.us/i/perl2.png/)
[http://img535.imageshack.us/i/perl3.png/](http://img535.imageshack.us/i/perl3.png/)
[http://img812.imageshack.us/i/normalx.png/](http://img812.imageshack.us/i/normalx.png/)

the first 3 are my attemps to catch the process in the act, but due to refresh rates i guess, the cpu usage is shown properly but the process gets out of the way before its actual usage is apparent. i did catch (vgrepped not with a screenied unfortunately) perl on htop at 64% usage during a spike that reinforces my belief it is the culprit.

what worries me is the --cron thing at the end of one of these. my crontab is empty for both my user and root so who cron'd the process? judging from the munin-update thing, i'm guessing something is trying to update itself. is there any way i can keep a log of sorts that records only processes that go about 50%, how much exactly they're using and how long they're there?

btw, using ps -eLf | grep perl, gives me nothing but the instance of grep trying to find perl. using ps -eLf | grep /usr/bin gives me a lot of things but nothing perl related.

gonna check up on those new addons and post back - please post anything you know that might help

thanks :)

---

### Post by Lynx Phoenix on 2010-12-23
ok turns out i'm a complete ****ing idiot. the answer was right in front of my eyes

i installed munin some days ago and it was doing its graphing/noding thing. i tried to solve it surgically, stopping the services and all but it didnt work (strangely even the munin user cron was empty...) so i just removed munin altogether. guess its my fault for installing something i have no idea about #-o

sorry about the pointless thread guys

---

