---
title: "my internet provider hates ubuntu????"
date: 2006-03-08
forum: General Help
---

### Post by drop_d33 on 2006-03-08
okay.. i dont know for sure about the title. so obiously i have an internet connection. my problem is the speed of my connection. i used to have an average of 1.3mbps but just recently( 2 weeks ago), the speed went drastically low. at one point it even went as low as 40kbps!! now it is at average of 350kbps. and i rarely reach 700kbps. much more i never reach 1mbps anymore. i am on dual boot by the way, so at a couple of times i use XP. but when i tested the connection speed thru the meter my internet provider provides, it amazingly says 3mbps!! it averages at around 1.5mbps. it hasnt happened just once. i was on XP earlier and tested the speed, again was, 1.5mbps. so when i went back to ubuntu and tested the speed, it said i had 350kbps. i never seem to reach 1.5mbps on ubuntu no more. i didnt change nothing on my internet/router settings. i dont even dare to touch it! and i dont even want to bother calling up my internet provider. lets just say that if u call them, it is like ur just talking to a Microsoft staff, wherein u will just receive nonsense answers, and dont even expect good service. what is this?! is my provider biased on windows?!! wtf?! this makes me hate microsoft even more!!! grrrr.... any comment guys? i have a dsl connection by the way

---

### Post by MacV on 2006-03-08
Turn off the IP version 6 support on your network card.
[http://www.ubuntuforums.org/showthread.php?t=126221&highlight=slow+internet+speed](http://www.ubuntuforums.org/showthread.php?t=126221&highlight=slow+internet+speed)

---

### Post by Brynster on 2006-03-08
Also be very warey of speed measuring software and internet connections. 

I have never seen one that actually measure connection speed acurately.

---

### Post by Mustard on 2006-03-08
How are you testing the speed in Ubuntu?

---

### Post by drop_d33 on 2006-03-08
i test it thru the website of my internet provider. they have a meter there to test their subscribers speeds.. my friend who is also on ubuntu and on the same provider advised me to just monitor the speed for half a year. still, im really annoyed by the fact that XP is getting a faster connection. i hate MS even more

---

### Post by stoeptegel on 2006-03-08
I think it's best to test internetspeed with a 100mb.bin file; just search with google for "100mb.bin" or "50mb.bin" and wget the download to see the avarage speed when wget finishes.

PS. Most providers can't help you when you tell them you're using linux. There are only two ISP's here in the Netherlands with decent linux support: xs4all.nl and kovoks.nl

---

### Post by drop_d33 on 2006-03-09
guys help me!! my speed is now at an amazingly low speed!! 14.3kbps!! absolutely horrible!! we arent paying for speeds like these.. XP still gets top speeds.. and i didnt tinker with any of my router settings. it just went this low two weeks ago!! unbelievable!!! i hate MS

---

### Post by ESM on 2006-03-09
But XP gets top speeds :)

I don't have this by the way. With Versatel the speed in Linux are even better than on XP.

---

### Post by drop_d33 on 2006-03-09
i have no idea why XP gets top speeds.. and i dont like using XP. i want to get top speeds on ubuntu again!!
:cry:

---

### Post by dpaint4 on 2006-03-09
[QUOTE=drop_d33]i have no idea why XP gets top speeds.. and i dont like using XP. i want to get top speeds on ubuntu again!!
:cry:[/QUOTE]

Welp. Time to change ISP's. Sheesh. Glad I never experienced that. I'd be so mad. I bet they can somehow tell that you're browsing with an 'unsupported platform' or some shit like that, and are limiting your speed as a 'security precaution'.

That's my conspiracy bet.

My normal everyday bet is that something is configured incorrectly. Have you tried another connection? A freind's connection who dosen't use this ISP? How about the connection of another friend using Linux? 

I'd do that and if you can prove it's due to your OS, switch providers, not OS's.

---

### Post by stoeptegel on 2006-03-09
What i would do i trying a live-cd, and when the outcome is the same thinking about disabling my account there.

---

### Post by Hitchhiker427 on 2006-03-09
Well, I'm not sure what's causing it.. may be your ISP, may be an improper linux configuration.  However, I don't understand how every one of your posts contains "I hate MS!".  I mean, just because XP performs better in this area for you, is no reason to hate it.  In fact, one would think that this incident would make you like Windows more, but hey, what do I know?  Nevertheless, don't blame Microsoft for some other screw-up they have no control over, and don't insult them for making an OS that is working BETTER for you here.

---

### Post by pbaehr on 2006-03-09
You should just end all the speculation and experimentation and just call your ISP and ask them plain and simple if the way their service operates could interfere with your net speed based on your OS. Don't accuse them of anything, just ask them if that could possibly be your problem.

If they say no something in Ubuntu may be set up wrong. I'd make the call and put the speculation to rest so that everyone helping can try and track down the real culprit in the event there is no massive ISP conspiracy. ;) 

Good luck!

---

