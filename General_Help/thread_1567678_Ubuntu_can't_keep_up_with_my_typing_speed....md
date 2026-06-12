---
title: "Ubuntu can't keep up with my typing speed..."
date: 2010-09-04
forum: General Help
---

### Post by James M Weir III on 2010-09-04
So lately I've been having some issues with certain programs (namely Empathy) being unable to keep up with my typing speed.  The problem is I'm not sure where to look for the cause of the issue.

It's not simply a delay; it just stumbles all over what I'm trying to type.  For example, if I were to type the word "not" it would only pickup the 't'.  Then when I try to backspace and correct it might only pickup some of the backspaces (which means my corrections need corrections, exacerbating the problem).

Needless to say it's incredibly frustrating.  It feels like video lag (even though that doesn't really make any sense).  On that note, my video drivers are up to date.  I haven't tried Pidgin yet because other than this one issue I like Empathy.  I'll probably try that test next, but I was wondering if anyone had heard of a similar type of problem.

I suppose it could have something to do with Compiz or perhaps Flash open on Firefox in the background somewhere.  I'm running 10.04 and don't usually have too much running, though.

Hardware specs:  [http://computershopper.com/laptops/reviews/asus-g50vt-x1](http://computershopper.com/laptops/reviews/asus-g50vt-x1)

---

### Post by mikewhatever on 2010-09-04
Can you name ALL of the programs affected, perhaps there is something in common. Don't be vague. Obviously, Ubuntu, the operating system can't be affected, as it isn't a typing application.:p

---

### Post by James M Weir III on 2010-09-04
Empathy is the main culprit where the problem is consistent.  I *think* it has happened in Firefox, but it is not very common there.  If the problem has something to do with receiving input from the keyboard then obviously it would not be the fault of Empathy (but the OS instead).  Like I said, I need to do more testing, but I was hoping the problem would ring a few bells and save me hours of random shots in the dark.

---

### Post by mikewhatever on 2010-09-04
Just guessing, but it seems, if Empathy is the only program affected, the problem is specific to Empathy. Had there been a problem of receiving input from the keyboard in general, don't you think all other programs would have been displaying the same behavior?

---

### Post by no2498 on 2010-09-05
just a guess but some thing is hitting the cpu hard
have a look in htop
do that in a terminal

---

### Post by RedRat on 2010-09-05
I can't speak for Empathy but I do note that some web sites, typing can be slow, perhaps it is Java (just a wild guess). I do a lot of responses on Huffington Post and If find that typing in the comment box there to be atrociously slow on some days, and OK on others--but then it is keeping tabs on word count. Find the same thing on the Washington Post comments. What I do when the web site is particularly slow and unresponsive is to type my comments in gEdit and then copy/paste them into the comment boxes. If gEdit is not giving you problems then I don't think the OS is the problem. I suspect it might be Firefox, Java, or some other factor.

---

### Post by James M Weir III on 2010-09-13
Well seeing as how I've dumped my Windows partition finally (go big or go home), I've been forced to really "live" in Linux.  Unfortunately this problem has not gone away.

Upon further testing, this problem is not always present.  It seems to come and go, and it almost seems to get worse the more I backspace (as weird as that sounds).  It's actually happening right now as I type this in.

Programs that have issues now include Empathy, Terminal, and Firefox (equally bad in all of them).  I haven't had any problems in gedit yet.

I tried using htop but nothing shocking was revealed.  Most of the time it was htop itself at the top of the CPU usage, and occasionally firefox would pop up there.  Usage was usually 3% or less, with firefox spiking at about 15% every 20 seconds or so.  Far too infrequent to be causing the constant sluggish behavior.

It feels very similar to the kind of lag you get when you're using generic video drivers (ie, after a fresh install of windows).  Like a keyboard equivalent of mouse lag when you're not using a hardware cursor in games.

I'll keep researching this.

---

### Post by mastablasta on 2010-09-13
have you tried replacing the keyboard?

---

### Post by James M Weir III on 2010-09-15
> **mastablasta said:**
> have you tried replacing the keyboard?

Well, from the link I posted above it's a laptop.  I suppose it would be possible to replace it but I'm fairly certain it isn't the culprit.  Never had issues like this in Windows.

Mostly its the repeating that drives me nuts.  Even if I hunt and peck it will randomly decide to repeat a keystroke 3-6 times (and often when I'm trying to backspace, making the problem worse as I'm trying to correct a previous repeat).

---

### Post by coffeecat on 2010-09-15
> **James M Weir III said:**
> Well, from the link I posted above it's a laptop.  I suppose it would be possible to replace it but I'm fairly certain it isn't the culprit.  Never had issues like this in Windows.

Well - even though it's a long shot, it's worth excluding a hardware problem in the laptop. You could plug a USB keyboard in and see how that behaves.

---

