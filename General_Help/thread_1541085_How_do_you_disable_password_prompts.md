---
title: "How do you disable password prompts?"
date: 2010-07-28
forum: General Help
---

### Post by justinsn95 on 2010-07-28
I know, I know, its a security feature. That doesn't make it any less annoying. I find the constant asking for my password to be every bit as irritating as Windows's UAC. When I want to use the terminal, or when I want to download something, I don't want to have to enter my password every time. I don't care that someone could theoretically do something to my computer in some way. I managed to stay out of harms way in windows with UAC off, I'm sure I can do it in ubuntu without the constant nagging of the password prompts. Its annoying and I am tired of dealing with it. Anyone know how to turn it off? I am really not looking for reasons to leave it on. Its the same with UAC: Yeah, it can keep you out of trouble. No, I don't want it on.

---

### Post by dreamsR4living on 2010-07-28
As far as I know, this is the way security in Linux is arranged and there is no way to shut it off as a normal user. This is the difference between Windows and Linux. Linux has an extra security layer that Windows lacks, although they make it look like it has an extra layer.

I never tried if it is possible to log in as root from the start. You wouldn't need your password more than once in that case, but I would certainly recommend against doing that. Just because chances are 90% that not somebody else, but you yourself will harm your system, maybe lose stuff or render your entire system unusable.

---

### Post by ajgreeny on 2010-07-28
I don't think you have to actually log in as root to avoid the password prompt every time you try to do something that normally needs it, but as I have never had a reason to do so I can't remember exactly how it is done other than my memory suggesting that it will involve editing the sudoers file with ```
sudo visudo
``` and adding the line ```
%sudo ALL=NOPASSWD: ALL
``` at the end if it is not already there, and making sure you are a member of the sudo group, which you will not be normally by default.

However as everyone else will keep telling you this is [COLOR=Red]**most definitely not recommended**[/COLOR] and will leave you open to mistakes that may cause you great grief.  It is, however, your choice, even if a silly one, in my opinion.

---

### Post by sisco311 on 2010-07-28
You can configure both policykit and sudo to allow you to run _some_ applications as root without a password. 

Check out: 
[thread=1132821]HowTO: Sudoers Configuration[/thread]
and
[http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html](http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html)

NOTE: Disabling the password prompt for all applications is completely inappropriate and unnecessary.

---

### Post by mikewhatever on 2010-07-28
Constantly asking for password? What do you do with your computer? Edit system files all day long? I am dead serious, what do you do, that you get constant password prompts?

---

### Post by ajgreeny on 2010-07-28
> **mikewhatever said:**
> Constantly asking for password? What do you do with your computer? Edit system files all day long? I am dead serious, what do you do, that you get constant password prompts?
That's a very good point!

Why do you get the password prompt when you try to download something?  That has never happened to me as far as I can remember; when you try to install something downloaded, perhaps, but not just to download it, surely?

I see from another of your threads that you have had great problems with using grub2, and apparently did not even have grub installed after installing ubuntu.  This makes me wonder if the CD you used or the .iso file you burned to make the CD was at fault, and therefore you may be getting many unusual things happening in the system you have, with a great number of other anomalies in the way your system works, or more importantly doesn't work.

---

### Post by AlphaLexman on 2010-07-28
> **ajgreeny said:**
> Why do you get the password prompt when you try to download something?  That has never happened to me as far as I can remember; when you try to install something downloaded, perhaps, but not just to download it, surely?

Well, not trying to be a smart a*$, but:
```
sudo apt-get install application-name
```
qualifies as a download. Maybe they are trying to install the entire repository! ;)

---

### Post by mikewhatever on 2010-07-28
> **AlphaLexman said:**
> Maybe they are trying to install the entire repository! ;)

Several times a day, every day? I don't think so. In my experience, the password is needed several times after the installation, but afterwards, installing updates once a week is all I need it for.

---

### Post by AlphaLexman on 2010-07-28
Sorry, my previous post was laced with sarcasm. But the truth is this:
BEING PROMPTED FOR YOUR PASSWORD IS A WARNING TO BE CAREFUL!
It is a reminder for the user to go, "Whoa, am I ready to do this?"

---

### Post by 73ckn797 on 2010-07-28
> **AlphaLexman said:**
> Sorry, my previous post was laced with sarcasm. But the truth is this:
BEING PROMPTED FOR YOUR PASSWORD IS A WARNING TO BE CAREFUL!
It is a reminder for the user to go, "Whoa, am I ready to do this?"

This.

---

### Post by chopinhauer on 2010-07-28
> **AlphaLexman said:**
> 
Sorry, my previous post was laced with sarcasm. But the truth is this:
BEING PROMPTED FOR YOUR PASSWORD IS A WARNING TO BE CAREFUL!
It is a reminder for the user to go, "Whoa, am I ready to do this?"


No, being prompted for your password is a protection against priviledge escalation: if you don't check for them, everybody that has access to your account, has access to the root account.
```

sudo -s

```
is your friend.

---

### Post by sisco311 on 2010-07-28
> **chopinhauer said:**
> 
```

sudo **-i**

```
is your friend.

fixed :), see [this]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") post by [unutbu]("http://ubuntuforums.org/member.php?u=518895").

also to log out from the root shell, one could run:
```
exit
```
or press Ctrl+d

---

### Post by whizzlife on 2010-07-28
Run as a root!
SIMPLES!

---

### Post by ajgreeny on 2010-07-29
We seem to be going round in a circle with everyone except the OP arguing about how wise or unwise it is to run the system without password prompts.

Unfortunately the OP has still not said why he is getting so many demands for the password in ordinary everyday tasks; that is what makes me wonder if there is something seriously wrong with his system.

Any comment, justinsn95?  See my post #6 in this thread.

---

### Post by justinsn95 on 2010-07-29
> **mikewhatever said:**
> Several times a day, every day? I don't think so. In my experience, the password is needed several times after the installation, but afterwards, installing updates once a week is all I need it for.

> **73ckn797 said:**
> This.

> **AlphaLexman said:**
> Sorry, my previous post was laced with sarcasm. But the truth is this:
BEING PROMPTED FOR YOUR PASSWORD IS A WARNING TO BE CAREFUL!
It is a reminder for the user to go, "Whoa, am I ready to do this?"

I don't need "this". If I am doing it, then I have already decided that I am "ready" for it. *I'll* be the judge of that, without the pestering from my OS, thanks. As I said, I turned off UAC in windoze, for the same reason I'd like this to be off. I don't care what the differences are, its the same question: 

"Are you sure you want to do this? I mean, are you *really* sure? No, I mean are you *really* **really** sure??" -Windoze and Ubuntu

"Yes #$%@"!! -me 

"Well, cause I mean... there is all kinds of really bad stuff out there and there are some really mean people and I'd hate to see you get hurt, and the world might come to an end and the sky is falling..." -Windoze and Ubuntu

"... sigh" -me

That's an exaggeration lol. But you get the idea.

---

### Post by mikewhatever on 2010-07-30
That's rubbish, and it doesn't answer my question.
What do you do that you constantly get prompted for the password???

---

### Post by clhsharky on 2010-07-30
We all know that if you really knew what your were doing, you would have already learned how to do it.
Good luck justinsn95

Sharky

---

### Post by Zill on 2010-07-30
> **clhsharky said:**
> We all know that if you really knew what your were doing, you would have already learned how to do it...
Very wise words indeed!

---

### Post by justinsn95 on 2010-07-30
> **clhsharky said:**
> We all know that if you really knew what your were doing, you would have already learned how to do it.
Good luck justinsn95

Sharky

Well, yeah. Thats why I'm asking.

---

### Post by WorMzy on 2010-07-30
The original question was answered by posts #3 and #4, so I'll just chuck in my "Don't do it, it's not a good idea" and leave.


Don't do it, it's not a good idea.

*leaves*

---

### Post by Quackers on 2010-07-30
In all fairness to the op, try googling "turn off uac" and see how many hits you get. It strikes me as a similar thing in Ubuntu. Why should Ubuntu insist that I have a password in the first place? Nobody but me uses my laptop. A password is not needed at all in my circumstances, nevermind being prompted for it every time I want to install something or change a part of the system.
The silly part is that anyone can change the root password anyway! It's just pseudo security in the first place.
You may have guessed that this is one of my least favourite Ubuntu features :-)

---

### Post by WorMzy on 2010-07-30
You can't change the root password unless you can login as root, or have a sudoers account that allows you to.

Perhaps you're the only person who uses the laptop, but what if you left it unattended? What if someone ssh'd into your PC?

Your Ubuntu installation can be left unusable with a single sudo command.

[SIZE="3"]_[COLOR="Red"]DO NOT RUN ANY OF THE FOLLOWING COMMANDS[/COLOR]_[/SIZE]

```
sudo rm -fr /
```
```
sudo chmod -R 000 /
```
```
sudo apt-get remove ubuntu-*
```

[SIZE="3"]_[COLOR="Red"]DO NOT RUN ANY OF THE PREVIOUS COMMANDS[/COLOR]_[/SIZE]

All it'd take is one malicious user on an unprotected PC, and any one of the above commands would leave you with an unusable installation. I admit it's unlikely to happen, but why even take the risk? Entering your password takes all of half a second.

---

### Post by Quackers on 2010-07-30
Maybe that's my bad. I could have been thinking about Mac OS X - sorry.
On your other point I would say that it would be my misfortune for that to happen and I would have to re-install - but as I have done that many times already it would not be the end of the world.
The fact still remains that I believe the choice to have a password should be mine and mine alone. I don't appreciate being dictated to by the system. That's part of the reason I'm looking at Ubuntu in the first place!
Did you run Windows? Did you disable uac?

---

### Post by WorMzy on 2010-07-30
Yes, but I don't think of them as the same thing. UAC is just a "are you sure" annoyance, whereas the sudo password prompt is confirming that you have the rights to run certain things.

---

### Post by Quackers on 2010-07-30
I appreciate what you are saying WorMzy, but I just find it quite annoying at times (when I didn't want a password at all).
I am being asked for my password when not even using sudo, that's what irritates me.
Please don't get me wrong. Compared to previous installs with different hardware and different versions of Ubuntu, I am extremely impressed with Lucid. So much so, that I haven't even used Windows or Mac OS X for 3 days. I have everything I need in Lucid. My problems are mostly finding my way around the system and locating programs, files and things.

---

### Post by WorMzy on 2010-07-30
[QUOTE="Quackers"]I am being asked for my password when not even using sudo, that's what irritates me.[/QUOTE]

That is unusual, unless you mean graphic applications that you're running from shortcuts, in which case you probably are running them with gksu/gksudo/kdesudo, which are basically graphical frontends to sudo; some apps need to be run as root, like gparted. Some programs will run as a normal user, but then ask you for your sudo password before you can modify certain things; for example Users and Groups settings (users-admin), and Time and Date settings (time-admin).

Basically, anything that needs to create/modify/delete files outside of your home folder will need your sudo password.

As previously mentioned, you can disable the password prompt if you desire, the option is there, and nobody is going to stop you from disabling it if you want to; we just like to make sure that you know exactly why it's there in the first place, and what you're opening yourself up to by disabling it. At the end of the day, it's your PC, and you can do what you want with it. :)

---

### Post by hakermania on 2010-07-30
You dont get all time promts.... Only when you wanna install something (once a month) or/and modify something from the filesystem (once a week)

---

### Post by Quackers on 2010-07-30
There's more of that going on when the system is brand new to the user. Graphics driver installation (which has been needed more than once because there are 3 of them - some work partially only), new programs that you didn't even know you had that weren't installed automatically. There are plenty of times that I am asked for the password. And I have a long way to go yet :-)

---

### Post by justinsn95 on 2010-07-30
> **WorMzy said:**
> Yes, but I don't think of them as the same thing. UAC is just a "are you sure" annoyance, whereas the sudo password prompt is confirming that you have the rights to run certain things.

Windows has that too, also annoying. I have UAC disabled, and on more than one occasion, it has said "Administrator privileges are required for this task. Do you wish to proceede?" I was annoyed by that as well. Cause just like in Ubuntu, I *am* the administrator. As quacky said, its my PC and I don't need my OS bothering me with this stuff. But, I can see that we are in the vast minority here. You linux guys are darn protective of your OS, even when it is in the wrong. And that's not to say that its in the wrong for *you*. Its just in the wrong for *me*. Im a big boy, I can take care of myself. I don't need my OS saying "AreyousureAreyousureAreyousure??!!" Yes I'm sure, dang it. If I wasn't, you wouldn't be asking me this would you? lol

---

### Post by oldos2er on 2010-07-30
```
sudo -i
``` will give you a persistent root terminal. When you're done type **exit** to close it.

Linux was designed from the ground up to be a multi-user, networking OS; hence the usernames/passwords, file permissions, admin (root) elevated privileges, etc. Also, if your (anyone's) laptop or PC is connected to the internet in any way, it has far more than a single user.

"The fact still remains that I believe the choice to have a password should be mine and mine alone. I don't appreciate being dictated to by the system."

No choice is being withheld from you; it's your lack of knowledge that makes it seem as though you are in thrall to "the system". Give yourself some time to learn Linux, and I'm sure this will change.

---

### Post by Quackers on 2010-07-30
> **oldos2er said:**
> ```
sudo -i
``` will give you a persistent root terminal. When you're done type **exit** to close it.

Linux was designed from the ground up to be a multi-user, networking OS; hence the usernames/passwords, file permissions, admin (root) elevated privileges, etc. Also, if your (anyone's) laptop or PC is connected to the internet in any way, it has far more than a single user.

"The fact still remains that I believe the choice to have a password should be mine and mine alone. I don't appreciate being dictated to by the system."

No choice is being withheld from you; it's your lack of knowledge that makes it seem as though you are in thrall to "the system". Give yourself some time to learn Linux, and I'm sure this will change.

With all due respect, that's not true.
It is not possible to set up an account on Lucid (during installation) without putting in a password. Even Vista doesn't insist on that!

So, you are saying that either I put up with the prompts or sign in as root. And people here are warning me about security!!!  Not much of a choice in my humble opinion.

---

### Post by Quackers on 2010-07-30
WorMzy, am I reading this correctly?

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by The Cog on 2010-07-30
@justinsn95:
You have still not said what you doing that requires you to constantly keep putting a password. It's something I do around once a day, when I install updates. If you need to do it more often than that, constantly, I too wonder what's wrong - what is it that's broken. 

If you're doing system admin stuff, remember that **sudo -i** gives you a root prompt that lasts for as long as you leave the terminal open. Also consider that you don't drive round with the engine cover removed just because you tinker with the engine occasionally. You expect to have to remove the cover every time. 

If you're not doing admin stuff and you keep needing a password, something is amiss and if you would tell us what you are doing that requires a password, we may be able to help.

Finally, it is possible to configure Linux so that it doesn't require passwords before doing admin stuff. It is against the rules of this forum to tell you how, and I personally agree with those rules. By the time you know Linux well enough to know how to do that, hopefully you'll know Linux well enough to know you shouldn't do it. If not, then hopefully you'll at least know Linux well enough to avoid the more common mistakes that can trash the entire system, like putting a space where there shouldn't be one (yes, I've seen that).

---

### Post by WorMzy on 2010-07-30
> **Quackers said:**
> WorMzy, am I reading this correctly?

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

I don't know, how are you reading it? :P

Ubuntu doesn't set a password for root by default, so you shouldn't need to recover it. You can use ```
sudo passwd
``` to set a password for root, but that's unnecessary, and even less advisable than removing the sudo password prompt.

---

### Post by Quackers on 2010-07-30
Hi WorMzy, my point was that if you can boot up in superuser mode without using a password, then surely passwords become a tad pointless. You could do anything you want to anyone's system without even knowing a password.

---

### Post by sisco311 on 2010-07-30
> **Quackers said:**
> Hi WorMzy, my point was that if you can boot up in superuser mode without using a password, then surely passwords become a tad pointless. You could do anything you want to anyone's system without even knowing a password.

Most of us know that and still use a (strong) password. But you don't have to convince us, go ahead and disable the password prompt if you wish.

---

### Post by Quackers on 2010-07-30
In an earlier post I was told that it was only possible if you knew the password. Obviously this is not the case.
I can understand the use of passwords when somebody else can use the computer - it's just that this is not the case for me. I would just appreciate the option to not have one.

---

### Post by WorMzy on 2010-07-30
> **Quackers said:**
> Hi WorMzy, my point was that if you can boot up in superuser mode without using a password, then surely passwords become a tad pointless. You could do anything you want to anyone's system without even knowing a password.

You can lock grub with a password to prevent people entering runlevel 1 (Well, you can lock grub legacy, I assume there's an option for grub 2), and you can (probably*) lock your bios to prevent people booting from LiveCDs and circumventing security that way.

So yes, there are ways of breaking into a system and doing damage without knowing a sudoers/root password, but it's possible to block these methods too. You just need to be aware of them.



*Most bios' I've encountered have this option, but not all, which is a gaping security hole if you ask me.

---

### Post by oldos2er on 2010-07-30
> **Quackers said:**
> With all due respect, that's not true.
It is not possible to set up an account on Lucid (during installation) without putting in a password. 

The point I was trying to make was that once your account is set up, you can greatly minimize, or completely do away with the need to enter your password to do administrative tasks (although I don't recommend the latter at all).

> **Quackers said:**
> So, you are saying that either I put up with the prompts or sign in as root.

I never said sign in as root (the root account is disabled in Ubuntu, although it's very easy to enable if you wish to), I said to use **sudo -i**, for which you only need enter your password once. **sudo** itself can be tweaked in various ways. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by blur xc on 2010-07-30
> **WorMzy said:**
> You can lock grub with a password to prevent people entering runlevel 1 (Well, you can lock grub legacy, I assume there's an option for grub 2), and you can (probably*) lock your bios to prevent people booting from LiveCDs and circumventing security that way.

So yes, there are ways of breaking into a system and doing damage without knowing a sudoers/root password, but it's possible to block these methods too. You just need to be aware of them.



*Most bios' I've encountered have this option, but not all, which is a gaping security hole if you ask me.

but even a password protected bios isn't that secure.  All you need is a paper clip or small screwdriver to jump the reset bios jumper, and BAM no more bios password...

But, a lot of cases have accommodations for a lock, or padlock, but locks can be picked, and keys can get stolen or left in an insecure location.  So you have to lock your case key in a lock box- and then secure the location of the lock box key...  etc... etc...

BM

---

### Post by WorMzy on 2010-07-30
> **blur xc said:**
> but even a password protected bios isn't that secure.  All you need is a paper clip or small screwdriver to jump the reset bios jumper, and BAM no more bios password...

But, a lot of cases have accommodations for a lock, or padlock, but locks can be picked, and keys can get stolen or left in an insecure location.  So you have to lock your case key in a lock box- and then secure the location of the lock box key...  etc... etc...

BM


Haha, too true. There is no such thing as a completely secure system.

---

### Post by theozzlives on 2010-07-30
Without reading the rest of this thread, logging on as root, and bypassing the password are forbidden subjects. **MODS please close this before anyone is tempted to divulge more info, thanks.**

---

### Post by Quackers on 2010-07-30
Oldos2er, I take your points.
Wouldn't it be easier to give me the option to not have a password though?
Anyway, I've learned a lot today :-)

---

### Post by Quackers on 2010-07-30
I'm sorry if I have broken the rules. Even though it only took me 20 seconds to find the info. Please Mr. Moderator feel free to delete my earlier link if it is a problem.

---

### Post by clhsharky on 2010-07-30
(sudo) is a part of Ubuntu security model to help protect millions, with ease to elevate admin to root.
All your annoyance, inconvenience are easy to changed, but are there for a reason(protect millions).

Learning is up to yourself, we'll help if we want to.
There is a lot of Documentation - Ubuntu Documentation, Community Documentation, man pages, Search Ubuntu Forums, many many sites devoted to Ubuntu, find even more on Google.

If Ubuntu's model is wrong in your opinion or you dont like it, there are hundreds of distro's to choose from. Not good enough for you, spin your own perfect distro.

We're free to use FOSS or not, and free to learn or not, and so on. You choose.
Laziness is NOT our concern. 

Sharky

---

### Post by oldos2er on 2010-07-30
> **Quackers said:**
> Oldos2er, I take your points.
Wouldn't it be easier to give me the option to not have a password though?


As long as Linux remains multi-user and networked, I don't think it will. But I'm not a developer, so I don't really know.

---

### Post by dreamsR4living on 2010-07-31
> Without reading the rest of this thread, logging on as root, and bypassing the password are forbidden subjects. MODS please close this before anyone is tempted to divulge more info, thanks.

How can logging on as root be a forbidden subject? 

First of all, I used to run Debian and whenever I want to install a package or modify system files like Xorg.conf I have to do it as root, because Debian doesn't have sudo. 

Second of all, it is up to every user individually how they use their system. If they want to run as root constantly (which I highly recommend against), it is their own choice and responsibility. A topic like this can be helpful in making that choice. Deleting this topic will only add to people being ignorant about the risks.

For a list of forbidden subjects see this; [http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)

---

### Post by Bachstelze on 2010-07-31
> **dreamsR4living said:**
> How can logging on as root be a forbidden subject? 


[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by DrMelon on 2010-07-31
> **justinsn95 said:**
> I don't need "this". If I am doing it, then I have already decided that I am "ready" for it. *I'll* be the judge of that, without the pestering from my OS, thanks. As I said, I turned off UAC in windoze, for the same reason I'd like this to be off. I don't care what the differences are, its the same question: 

"Are you sure you want to do this? I mean, are you *really* sure? No, I mean are you *really* **really** sure??" -Windoze and Ubuntu

"Yes #$%@"!! -me 

"Well, cause I mean... there is all kinds of really bad stuff out there and there are some really mean people and I'd hate to see you get hurt, and the world might come to an end and the sky is falling..." -Windoze and Ubuntu

"... sigh" -me

That's an exaggeration lol. But you get the idea.

And if the command happened to be "rm -rf /" in a malicious script (or even entered by hand, should you be that stupid) you would lose everything. Completely irreversible. 
Note that commands like that can very easily be disguised or obfuscated to hide their true function. Be careful.

---

### Post by dreamsR4living on 2010-07-31
An interesting blog post from TuxTeam.com about running as root to add to the conversation.

[http://tuxteam.com/2010/07/30/why-the-risk-of-running-as-root-is-overblown/](http://tuxteam.com/2010/07/30/why-the-risk-of-running-as-root-is-overblown/)

---

### Post by dreamsR4living on 2010-07-31
> Re: How do you disable password prompts?
Quote:
Originally Posted by dreamsR4living View Post
How can logging on as root be a forbidden subject?
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Alright, thanks, I wasn't aware of this post.

---

### Post by justinsn95 on 2010-08-01
> **oldos2er said:**
> Give yourself some time to learn Linux, and I'm sure this will change.

I am. And, I am not logging in as root because I simply don't know enough to make the decision in good conscience. I won't be doing that, because I don't feel that I know near enough to understand the true risks of all that could go wrong. Perhaps one day, that'll change. But for now, I aint gonna do it. I just wanted the irritating password prompts off. Big difference between that, and logging in as root. And I really don't see why they HAVE to be related. I mean they are, but there should just be a little option in the setup where you turn them off, and yet somehow you are not logged in as root. I don't see why they have to go hand in hand. 

> **The Cog said:**
> @justinsn95:
You have still not said what you doing that requires you to constantly keep putting a password. It's something I do around once a day, when I install updates. If you need to do it more often than that, constantly, I too wonder what's wrong - what is it that's broken. 


Guys... its probly cause you haven't been noobs for a long time. But no exaggeration.. I probly got asked for my password 15 times today. 5 times were when I actually knew what I was doing. (i was installing games) the other 10 times was me setting things up how I like it, or how I want to try stuff out, in "Ubuntu Tweak". I don't know fully what I am doing yet, so of course I just muddle around looking at stuff. And I keep messing with updates and manually updating things and trying out new little programs and stuff to see if I like them. Ubuntu Tweak asks you for your password a lot, and IIRC the software center and package manager asks for it from time to time as well. 

Not trying to be rude or anything, but I really don't understand how you guys could wonder why a noob wouldn't be asked for his password a lot. You'd think it'd be obvious.. cause I don't know what I'm doing and I'm messing with all kinds of $h1#.

> **WorMzy said:**
> Haha, too true. There is no such thing as a completely secure system.

Now on to my next point. What good at all does asking for my password do, before I install something? It happens every time, right? If so, then I am going to be used to seeing it, right? Then how on earth am I to recognize something malicious, if I am the one choosing to install it and saying "Yes, do this"? Which makes the whole thing completely pointless. Which only adds to how annoying it is. If I install a virus, then I install a virus. Same as in windows. If I download something and say "Install this now please" then does the OS magically know that I shouldn't? So what, may I ask, is the point? 


> **clhsharky said:**
> 

We're free to use FOSS or not, and free to learn or not, and so on. You choose.
Laziness is NOT our concern. 

Sharky


Don't really know where you are getting this from, but I'll just say ok.

---

### Post by Elfy on 2010-08-01
This is just going in circles with no new information - read this [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

You can use sudo -i and have it open while you are playing. 

I understand that you might be installing and removing things at the moment - I did the same, but I never really worried too much about having to type a few characters. 

Closing this now.

---

