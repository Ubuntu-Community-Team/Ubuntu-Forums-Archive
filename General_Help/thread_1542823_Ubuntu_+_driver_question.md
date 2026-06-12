---
title: "Ubuntu + driver question"
date: 2010-07-31
forum: General Help
---

### Post by artisan on 2010-07-31
Goes like this.

Drivers did work.
Ubuntnu "upgraded" to 10.4 drivers no longer work.

So it is not the drivers.
Drivers did work and now do not. The only thing that changed in between was Ubuntu.

Why fix something that ain't broke?
And then  say it's the "propriety"  drivers fault?

OK some people will say that because they are proprietary then the people who code for Ubuntu do not have (full?) access to the drivers?
I am NOT a programmer just a user.
But how come things have moved backwards?

Or how come that the drivers (nvidia in particular) are crap?
Is it the drivers? Or Ubuntu?
This is not a troll question I would honestly like to know.

How come it is taking this long after the release of 10.04 LTS that there are still some video driver issues?

I am not a rocket scientist but, a computer needs a monitor. Without that it is pretty much useless.

So the question is.
Can higher ups please give some reason why the Nvidai drivers are still borked?

Thank you.

---

### Post by NightwishFan on 2010-07-31
Perhaps you could be more specific to the driver version and your card etc. I am sure someone would be glad to help you get your computer working and answer those questions. :)

---

### Post by DrMelon on 2010-07-31
> **artisan said:**
> 
I am not a rocket scientist but, a computer needs a monitor. 


Only for home use. Ever wondered what goes on behind the scenes of the internet?

Besides, you chose to upgrade to 10.04: nobody forced you to do it. You didn't have to do it, especially if you knew beforehand that people were having problems with drivers.

It is very difficult to explain why we have these problems to a user - Linux is a highly technical operating system of many parts. You have to accept that things can and will break, and a simple solution isn't always available. You will have to get your hands dirty with various terminal commands, perhaps even recompiling drivers separately. It depends on the situation.

Happily, it's just about the best way to become a computer guru in the shortest time possible. You'll learn a hell of a lot. :D

---

### Post by 3rdalbum on 2010-07-31
More information required. What exactly is the problem, and did you install the Nvidia driver through the Hardware Drivers program?

Asking questions like "Why don't the drivers work" and "Why haven't the issues been fixed" is a bit naff when most people haven't seen any issues.

---

### Post by artisan on 2010-07-31
> **DrMelon said:**
> Only for home use. Ever wondered what goes on behind the scenes of the internet?



Oh.
How do people program computers without a monitor?
Or am I being obtuse?
There would need to be a monitor attached.... No?
Or is it like that Who song "deaf, dumb and blind kid, sure plays a mean pinball"


NightwishFan
Thank you for the kind offer.
This is not about Ubuntu and especially not about the people like yourself, who are so helpful in the forums.
BUT.
There is obviously still an issue with Nvidia card and drivers.


I had it sorted once. But then there was an "update" that screwed things.
It is probable that I can spend my weekend trawling the forums and trying 
different solutions.

3rdalbum
A bit naff the questions may be.
But...
NOTE:
I am not asking for help!
Did I say I want help?
Would I have posted in the Cafe?

Where else I am supposed to ask why the video drivers are still screwed?
In the forums?

As far as I am aware I am asking why?
What is the issue here?
A monitor is integral. I can handle that 3D graphics for games does not work. What is so wrong with the whole thing that basic graphics drivers without Compiz do not "STILL" work out of the box?


I do know it is the Nvidia drivers. I have "cleared" this problem once before.
I am just trying to ask where the problem lies.
I am not the only person with this issue.
There are probably people working on this issue and who are still having sleepless nights.

There is no attack intended. 
Just asking that's all.

---

### Post by keithpeter on 2010-07-31
Hello

As others have said, if you can give more specific information about the driver and the video card your computer uses, people might be able to help.

Suggestion: boot from the live CD of the Ubuntu version that worked ok. Then type the following into a terminal prompt

```
lspci
```

You will see a line in the output something like the one below but with the name of the video card that your computer uses

```
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
```

Copy that line here and someone who has had similar issues with 10.04 will probably know what to do.

---

### Post by philinux on 2010-07-31
Moved to General Help Forum.

---

### Post by artisan on 2010-07-31
OK I give in!

I have no choice right now.
Nvidia driver are giving an intermittent fault.

Some times the computer is OK. Most often though when the computer is switched on (the first time in the day) after approx. 5 minutes the computer shuts down.
Sometimes.

Sometimes it does this only once. Yesterday it did it 3 times in a row.

Sometimes it reboots. Sometimes it switches off completely.
Sometimes. I does not.

It IS the video drivers. I have solved this before but the Nvidia threads have disolved in to 800 page threads.
Right am using Nvidia driver version 173.14.22

No Compiz.
Just on basic settings.
Have, Nvidia accelerated graphics driver (version 173) running
Tried the Nvidia accelerated graphics driver(version current [recommended]
Just as bad as each other.

---

### Post by artisan on 2010-07-31
> **philinux said:**
> Moved to General Help Forum.

No answers.
Great now can you please move this back to the Cafe where it was originally posted?

---

### Post by artisan on 2010-08-01
It just keeps getting better.

Just found out that I did not grab a copy of all the site info from Filezilla when I had to reinstall 10.04 because of a crappy Cups update.
:(:(:(:(:(:(:(

Now I have hours of extra work.
Yes my own fault.

BUT!!!!!!!!!!!!!!!
Comments such as
> you chose to upgrade to 10.04: nobody forced you to do it
do not go down too well.

---

### Post by artisan on 2010-08-01
> **artisan said:**
> It just keeps getting better.

Just found out that I did not grab a copy of all the site info from Filezilla when I had to reinstall 10.04 because of a crappy Cups update.
:(:(:(:(:(:(:(

Now I have hours of extra work.
Yes my own fault.

BUT!!!!!!!!!!!!!!!
Comments such as

do not go down too well.

Add to that... 

All emails have been lost. 
Evolution did not import properly.

This is going to be a LOOOONG day.


Now looking for recommendations for a stable Linux system to use.
Am more than seriously considering moving away from 10.04 LTS.
Can honestly say.

"I do not have time for this!"

---

