---
title: "Wrong File Transfer Time"
date: 2011-08-09
forum: General Help
---

### Post by snarlster on 2011-08-09
This seems like such a fundamental issue, but the countdown timer for file transfer is wrong by 1 minute exactly. This can be seen by copying for example 20GB of files between partitions/drives and watching the timer, it will count down from lets say 5 minutes and say "5 minutes left". Exactly when there is 2 minutes left, it will say "1 minute left" for 1 minute and then when there "really" is only 1 minute left it will say "60 seconds left" and then the seconds counter starts going.

I think this is pretty straight forward and shouldnt need very much explanation, but for example in Window$ they skip the whole "1 minute" part and go straight from "2 minutes" to seconds, which is more correct. When in a rush and you are waiting impationately for a transfer and seeing "1 minute left" for a "whole" minute and then all of a sudden its 60 seconds left... it can be a bummer :)

Hope this helps,

---

### Post by snarlster on 2011-08-09
Perhaps "General Help" isn't the best place for this, but I couldn't find any better... There must be a "bugs" category, but I couldn't find any way to navigate to it...

---

### Post by dFlyer on 2011-08-09
First time I've seen this. What version are you using?

---

### Post by jwbrase on 2011-08-09
It's not wrong, Windows simply counts partial minutes as full minutes and Ubuntu doesn't count partial minutes at all. They are both perfectly valid ways of rounding a non-whole-number of minutes. I personally would prefer rounding to the nearest minute (so that it goes from "3 minutes" to "2 minutes" when it flips over from 2:30 to 2:29, and from "2 minutes" to "1 minute" when it flips over to 1:29), but really, it's not that big a deal.

---

### Post by snarlster on 2011-08-10
> **dFlyer said:**
> First time I've seen this. What version are you using?
I got 11.04 classic running, you telling me you don't see the same issue?

---

### Post by snarlster on 2011-08-10
> **jwbrase said:**
> It's not wrong, Windows simply counts partial minutes as full minutes and Ubuntu doesn't count partial minutes at all. They are both perfectly valid ways of rounding a non-whole-number of minutes. I personally would prefer rounding to the nearest minute (so that it goes from "3 minutes" to "2 minutes" when it flips over from 2:30 to 2:29, and from "2 minutes" to "1 minute" when it flips over to 1:29), but really, it's not that big a deal.
How can it be correct to say:

"1 minute left" when there is exactly 2 minutes left... leaving the user waiting for 1 minute to be disappoint by 60 seconds left 1 minute later.

I would say that the timer should trip to say "5 minutes left" when there is exactly 5 minutes left and then 4 when there is 4, anything less is ok but more is disappointing.

---

### Post by snarlster on 2011-08-10
> **jwbrase said:**
> It's not wrong, Windows simply counts partial minutes as full minutes and Ubuntu doesn't count partial minutes at all. They are both perfectly valid ways of rounding a non-whole-number of minutes. I personally would prefer rounding to the nearest minute (so that it goes from "3 minutes" to "2 minutes" when it flips over from 2:30 to 2:29, and from "2 minutes" to "1 minute" when it flips over to 1:29), but really, it's not that big a deal.
I dont think rounding the time to the half minute would solve this simple issue, a simpler way is to say "Less than X minutes left" but the way Ubuntu does it now, they would have to say "More than X minutes left".

Also, I know this is not a "Big Deal" and im not going to stop using Ubuntu because of it ;) But... never the less I am of the opinion that it should be Less than, not More than and there is no need to disappoint people when they are in a rush, perhaps telling their friend to wait 2 minutes when it really is 3.

---

### Post by pommie on 2011-08-10
This is in "*Is the glass half full or half empty*" area, who cares, if all you have to worry about is a minute here and there you have it easy, I didn't even know that it counted like that, I just shove the transfer notification window to one side and do something else until it disappears, now that you know it counts this way what is the problem ??

Cheers David

---

### Post by snarlster on 2011-08-10
> **pommie said:**
> This is in "*Is the glass half full or half empty*" area, who cares, if all you have to worry about is a minute here and there you have it easy, I didn't even know that it counted like that, I just shove the transfer notification window to one side and do something else until it disappears, now that you know it counts this way what is the problem ??

Cheers David
Really?? I wonder if thats really the popular opinion here... please people, tell me what you think about this! 

Now that "I know", lets just keep it this way and let all future users of Ubuntu have to "find out"... You didnt know, but perhaps you dont work in a high speed workplace and perhaps you are NEVER in a rush while copying files. If Im copying a a few gigs and tell someone to wait, which is better to make him wait 1 minute less or 1 minute more?

I would love to hear if everyone here is of the same opinion here... seems like it so far, but it seems very wrong to me to have such a fundamental issue like this so wrong. 

Please people, post here if you think the timer should be "less than X minutes left" or "more than X minutes left"

---

### Post by snarlster on 2011-08-10
> **pommie said:**
> This is in "*Is the glass half full or half empty*" area, who cares, if all you have to worry about is a minute here and there you have it easy, I didn't even know that it counted like that, I just shove the transfer notification window to one side and do something else until it disappears, now that you know it counts this way what is the problem ??

Cheers David
Its Pretty basic, You shouldnt make promises you cant keep, if I say Im going to be somewhere in an Hour, I wont round up to 2 hours... I'll be there within the hour. If the computer flips from "5 minutes left" to "4 minutes left", I should not have to tell my colleague "no, see... its actually 5 minutes now... its just the way ubuntu does it"

---

### Post by pommie on 2011-08-10
> **snarlster said:**
> 
Now that "I know", lets just keep it this way and let all future users of Ubuntu have to "find out"... You didnt know, but perhaps you dont work in a high speed workplace and perhaps you are NEVER in a rush while copying files. If Im copying a a few gigs and tell someone to wait, which is better to make him wait 1 minute less or 1 minute more?



You will be making him wait exactly how long it takes, its finished when its finished, not one minute earlier or later, no matter what you tell him or what the _*estimated*_ transfer time says.
If you are working in such a high pressure time intensive environment, how come you have the spare time to stare at a timer counting down, you should be working, or were you just being facetious.

Cheers David, who regularly transfers 10~15gig files, they finish when they finish !!!

---

### Post by Wim Sturkenboom on 2011-08-10
You can file a bug report on launchpad (or mention it there as the question first).

The actual time left at 'exactly' 2 minutes is 1 minute, 59 seconds, 999 milliseconds and a bit ;) It just gets rounded down 'by stripping the part after the minutes'

Incorrect: yes
A problem: not for me
Easily solvable: yes

---

### Post by snarlster on 2011-08-10
Interesting arguments you got here Pommie, 

"It finishes when it finishes" and 
"I just shove the transfer notification window to one side and do something else until it disappears".

These are the reasons why you dont see the argument that this 1 minute delay is incorrect, because YOU just do this and that and dont care about time... I am here trying to point out a bug in an effort to improve Ubuntu, but because of your personal habits and general "dont care" attitude about transfer times, you do nothing to help point me to the correct place for this conversation, but rather shoot down the idea that it would be better to estimate down rather than up.  Thank you very much!

---

### Post by snarlster on 2011-08-10
Thank you for pointing me to the place for bugs Wim, I'll make a post there.

I agree with your diagnoses 100%, its not a "problem" for me also, but now that I know about it its rather an annoyance and I think that any "Estimate" of a workload should at least attempt to finish on a correct time rather than be built to be always late.

While looking at the time, it says "4 minute left"... 10 seconds go by, any user would think, now its less than 4 minutes left. Its just plain logical to have the time flip to say "4 minutes left" when there is exactly 4 minutes left rather than when there is 4 minutes and 59 seconds left.

---

### Post by pommie on 2011-08-11
> **snarlster said:**
> 
While looking at the time, it says "4 minute left"... 10 seconds go by, any user would think, now its less than 4 minutes left. Its just plain logical to have the time flip to say "4 minutes left" when there is exactly 4 minutes left rather than when there is 4 minutes and 59 seconds left.

So telling you that there is 4 min left when there is actually 3min 5sec left is more accurate than telling you there is 3 min left when there is 3min 55sec, either way is just as wrong as the other, the only solution is to have it display the actual minutes *and seconds* left to go.

Now see if you can reply without sending snide immature remarks my way, you know nothing about me just as I know nothing about you, other than what we post here, and lots of luck with the Developers if you show the same attitude towards them.

Cheers David, who is now outahere

---

