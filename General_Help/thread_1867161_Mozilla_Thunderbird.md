---
title: "Mozilla Thunderbird"
date: 2011-10-22
forum: General Help
---

### Post by apexRaiden on 2011-10-22
Hey everyone.
First off, glad to have Linux on my IdeaPad and not Windows. Yet i am a windows man, I've always been interested in trying out Linux.


Here is my problem.
I have a Lenovo s10-3t IdeaPad.
I just recently had MeeGo on here and decided to go with Ubuntu. The new one was released not too long ago either, 10.11.

My problem is when i try to start Mozilla Thunderbird, it crashes. I got it to start once and i uploaded all of my mail from my current e-mail account. And it worked fine. But then i chose to select a bunch of old mail and delete it all, then after that, it crashed. So when i tried to restart it, it turns on, runs for 5 seconds, looks for new mail and crashes. Ive tried restarting the computer as well. 

Like i said, im not familiar with the Linux process of anything. But i do know of the whole terminal thing.

So if anyone has a solution, if you could tell me the steps on how to take care of it, that would be awesome.
Thanks again!

---

### Post by pqwoerituytrueiwoq on 2011-10-22
open a terminal
```
thunderbird -safe-mode
```if it does not crash there is a addon you should remove

if it crashes this will completely reset Thunderbird (all settings/configurations will be lost)
```
rm -rf ~/.thunderbird/
```
alternatively you can move it so thunderbird will not see it
```
mv ~/.thunderbird ~/.thunderbird-borked
```
to restore it
```
rm -rf ~/.thunderbird/;mv ~/.thunderbird-borked ~/.thunderbird
```

---

### Post by apexRaiden on 2011-10-22
Ah awesome! It crashed in safe mode, so i just reset all the settings and such. 
Guess i should just go on the actual mail site and delete my mail that way instead.


Thanks for your help!

---

