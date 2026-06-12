---
title: "Sound problem with Ekiga"
date: 2006-06-07
forum: General Help
---

### Post by grenier on 2006-06-07
Hello all.
Having just installed dapper, I find myself with a problem I don't know how to correct. 

In trying to use ekiga, I find there is a problem with transmission of the sound input. I've configured it with no problem (both the test with the druid and a test in Audacity went well). But, when it comes to calling, no luck. I tried the test call (500@ekiga.net), and I can hear just fine, but as soon as it comes to my input, I can only hear weird noises like somekind of electronic bird.

Now I know the problem is somehow with the sound transmission as the "ebird" sound stops as soon as I kill the mike. Furthermore, in testing another SIP softphone (wengophone), I got exactly the same result.

So I'm guessing there's some kind of problem in what my computer sends, maybe with the protocol used, but I've no idea what to do about it :-k 

Any suggestion?


I doubt it's really useful, as it otherwise works, but for the record I use an external USB SB MP3+ soundcard - and no other apps use it, so no esd or some such problem.

---

### Post by rag on 2006-06-07
I had this problem. If you have a router use a static IP for your box and forward the ports 5000 to 5100 to it instead of using the STUN server. Also had to kill esd with:
 killall -9 esd 
on my box. The CVS version of Ekiga seems to get around the esd problem though.
You could add either of these repositories for a later version:
deb [http://snapshots.gnomemeeting.net/ubuntu/](http://snapshots.gnomemeeting.net/ubuntu/) dapper main
deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) dapper main

With Wengophone I had to forward ports 10600 and 10601

---

### Post by encompass on 2006-12-25
did it work? I have a similar problem....

---

### Post by encompass on 2006-12-25
[http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F](http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F)
Try this... it worked for me... :P

---

