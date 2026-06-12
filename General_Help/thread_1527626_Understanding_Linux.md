---
title: "Understanding Linux"
date: 2010-07-09
forum: General Help
---

### Post by bigseb on 2010-07-09
I've gotten to a point where I want to learn more about Linux. For example: so many times of gotten help by people telling me to type something in the terminal and it works but absolutely no sense to me. How/where do I learn what all this means and more importantly how do I learn to it myself?

What brought this on is I have this brilliant OS (Karmic UE) with a ton of stuff yet I find I still use it like a windows user. I want to expand my knowledge in this area. I know this probably sounds vague but any ideas would be welcome.

---

### Post by nothingspecial on 2010-07-09
I started with this site

[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

---

### Post by Turtle.net on 2010-07-09
If you really want to understand what's under the hood you should install Gentoo (I recommand to do this on another computer ... i took me quite some time to have Gentoo running :))

---

### Post by Rubi1200 on 2010-07-09
I have found these links to be useful:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by bigseb on 2010-07-09
Excellent stuff. Thanks a million. I bookmarked those links and will get reading once the baby's asleep.


@ [Turtle.net]("http://ubuntuforums.org/member.php?u=15664"): I have been recommended this (and similar) by many people. Pity I have no spare pc at the moment...

---

### Post by patchwork on 2010-07-09
If you have questions about commands (or you have an idea of what command you'd like to use, but need help with the syntax and options) check the manual pages.

i.e.```
man ls
```
will return the manual page for the ls command, ```
man bash
``` will return the BASH (default terminal shell) manual page, and so on.

---

### Post by QIII on 2010-07-09
> **Turtle.net said:**
> If you really want to understand what's under the hood you should install Gentoo (I recommand to do this on another computer ... i took me quite some time to have Gentoo running :))

Why?

I hear this all the time.  It seems so many have "discovered" something  that we who have been using Linux since the days of compiling our own  kernels knew long ago.

Does Gentoo do something he can't do in Ubuntu?

Just because you "have to" in Gentoo doesn't mean you "can't" in Ubuntu.

A mechanic does not need to build a car from individual parts delivered on a flat bed truck to get an ASE Certification.

I taught my son to repair cars by tearing up one that was assembled when we got it.

---

### Post by mcduck on 2010-07-09
When somebody gives you instructions or commands, just ask what they do. :)

It's actually recommended that when giving instructions on these forums you should also explain what they actually so. Of course that can be quite a lot of work to do, and in case of people like me who aren't native English speakers it's even harder to explain everything properly, but if you just show that you are interested in what's happening instead of just getting a quick solution to fix the problem most people will be happy to give more detailed explanations.

Of course the best way of learning is trying to do things yourself, think of something you'd like to do and then try to find out how to do it. Of course it's harder than just asking for instructions, but you'll also learn lot more, and remember what you learned better because of all the work you put into it.

When I started using Ubuntu I also found being active on these forums is quite a good learning experience. Even if you don't know much, there's always somebody in the Beginner section with a simple problem you can help with. Even if you can't give answer that solves the problem you'll learn from trying to figure it out, and of course from everybody else. :)

---

### Post by nothingspecial on 2010-07-09
> **QIII said:**
> Why?

I hear this all the time.  It seems so many have "discovered" something  that we who have been using Linux since the days of compiling our own  kernels knew long ago.

Does Gentoo do something he can't do in Ubuntu?

Just because you "have to" in Gentoo doesn't mean you "can't" in Ubuntu.

A mechanic does not need to build a car from individual parts delivered on a flat bed truck to get an ASE Certification.

I taught my son to repair cars by tearing up one that was assembled when we got it.

yep

---

### Post by mcduck on 2010-07-09
> **Turtle.net said:**
> If you really want to understand what's under the hood you should install Gentoo (I recommand to do this on another computer ... i took me quite some time to have Gentoo running :))

If you *really* want to understand what's going on under the hood you forget about Gentoo and start using LFS instead. :D

Gentoo is just halfway there.

(Or you can get yourself a normal distro and have yourself a system that actually works while you learn about what's going on under the hood...)

---

### Post by QIII on 2010-07-09
> **mcduck said:**
> If you *really* want to understand what's going on under the hood you forget about Gentoo and start using LFS instead. :D

Gentoo is just halfway there.

(Or you can get yourself a normal distro and have yourself a system that actually works while you learn about what's going on under the hood...)

It is instructive to see and remember how the parts are assembled in the end state, tear things down to the frame, and then work at getting them put back together with the understanding of how they are supposed to go together.

And then your son sells the stupid car.

Fifteen years ago, we were getting the Linux parts delivered by UPS a few at a time and assembling them on a coffee table.  Nobody really knew how they were supposed to fit together.  We tried different variations until we got one that seemed to work.  When UPS delivered the next package, we put that bit together and tried to bolt it on only to find out that we had aligned the bolt holes wrong on the first piece.

Why not see how the bolt holes are supposed to align first?

***THEN  ***buy the kit car and impress your neighbors when you finally back it out of the garage.

---

### Post by bigseb on 2010-07-09
Yeah I suppose I should have asked back when I was just starting out... didn't think to then.

---

### Post by Turtle.net on 2010-07-09
@QIII
I agree with your point. You don't have to go that way, but i am sure you can undertand that building your own car is clearly a good way to learn mechanics (hard and painful but a good way).
I like Gentoo because it forces you to build the system from the ground up, you have no other choice.
@mcduck
LFS ? Never heard of that. I just checked the Wikipedia entry. That sounds really interesting. A little be too hard core for me though.
I should try it one day :)

---

### Post by Turtle.net on 2010-07-09
I really like the idea, nut I still think that building a car from parts and engineering drawing is a better way. If you don't have the drawing ... then your method is clearly better then ...
Gosh I confuse myself with my own arguments ...
In the end i guess that both methods are good.

---

### Post by QIII on 2010-07-09
So, turtle, let me get this straight -- and I intend this to be a discussion, not a flame war.  Advice from an old fart, maybe.

If I had wanted to learn how my Harley works, I should have ordered the parts directly from Milwaukee, opened all the drawers on my big red toolbox, laid out the assembly manual on the floor and started putting it together?

Or should I ride for fun on Saturday and turn wrenches for fun on Sunday?

To an old fart like me, those who now crow about "learning things the hard way" like I had to back in the day remind me of the adage "Work smarter, not harder."

My recommendation to the OP would be this:  Use an OS that you can drive off the lot Friday afternoon and go cruising the drag that evening.  On the weekends, turn a few nuts and tighten them back up.   Get a feel for the girl.  Don't go pulling off the rocker covers and trying to install new camshafts that weekend.  As you get more and more confident, move on to more complex things.  Before long, you'll be able to replace those camshafts over a weekend and be pretty sure you can do it without riding the bus next week.  And you'll have the car to drive while you learn.

Let your next door neighbor learn about his car by getting it delivered in parts.  By the time he gets his assembled, you'll have been driving for a year and you'll know as much as he does.

Then, if you want, you can buy one in pieces.  I agree that there is substantial satisfaction in doing something with your own hands.

---

### Post by bodhi.zazen on 2010-07-09
In my experience, if you install Gentoo you learn Gentoo.

The biggest problem with that, IMO, it that there are too many things in the Gentoo way that do not generalize.

I think you are far better off learning :

1. Bash (see linux command links).

2. Learn to read the man pages.

3. Learn to compile from source code.

4. Learn to compile a kernel. 

Can do that with any distro.

If you go LFS you will learn ./configure && make && make install

---

### Post by bigseb on 2010-07-10
> **bodhi.zazen said:**
> In my experience, if you install Gentoo you learn Gentoo.

The biggest problem with that, IMO, it that there are too many things in the Gentoo way that do not generalize.

I think you are far better off learning :

1. Bash (see linux command links).

2. Learn to read the man pages.

3. Learn to compile from source code.

4. Learn to compile a kernel. 

Can do that with any distro.

If you go LFS you will learn ./configure && make && make install
Sounds good to me. Any starting points?

---

### Post by d3v1150m471c on 2010-07-10
Think of tasks you do on your pc that would be much easier if you had some simple code you could automate or just click on your desktop and it happen. Then, write bash scripts to actually perform these tasks. It might take you a while but little bash hobbies go a long way to learning the *nix shell.

---

