---
title: "All Kinds Of OS Problems"
date: 2010-06-02
forum: General Help
---

### Post by w0Rm210 on 2010-06-02
Ok before i go NUTS! I need to know if it's just my computer being fried or all these OS's are suddenly going nuts. Well ok i'm on a compaq presario with a AMD sempron 2100 mhz processor and i had windows 7 on it for a few months until something went wrong on it so i said screw it and picked up ubuntu 10.04 to try it out i ended up installing it and enjoying it until i decided i wanted something with KDE interface i tried openSUSE and it'd freeze halfway booting up so i got fedora KDE spin and it woulden't work either something about an error 13 mx80 or something this was just before it locked up so i coulden't use it at all then i tried to install ubuntu 10.04 once again but anytime i would take it off AC power it'd freeze up to the point i would have to remove the battery to turn it off then i got Kubuntu 10.04 once again it fully installed but now it just boots and then goes to a black screen is their something wrong with my computer? I'm getting the 64-bit version of every OS so far..... I'm gonna keep trying at kubuntu because i really do love kde interface but i'll live with ANYTHING at this moment....
 
 
Any suggestions?

---

### Post by lisati on 2010-06-02
The "[kubuntu]("http://www.kubuntu.org/")" flavour of Ubuntu comes with KDE. Have you tried that?

---

### Post by w0Rm210 on 2010-06-02
> **lisati said:**
> The "[kubuntu]("http://www.kubuntu.org/")" flavour of Ubuntu comes with KDE. Have you tried that?
 
 
I have it installed right now it just boots up shows the Kubuntu screen for a brief second then goes to a dead black screen in which i once again have to remove the battery to turn it off.

---

### Post by inameiname on 2010-06-02
Wow. you are really having some bad luck. Seeing as all the problems are occurring with a variety of a operating systems and environments, and all the problems seem to be different in nature, hardware might be a reason. I guess there is one way to know for sure.

Personally, to rule that out for me, I'd erase the hard drive entirely, and then run and install a live cd and then see if you have any woes. For me, that just ensures that the hardware is, software-wise, completely factory clean and like new, and then you'd know it's not because of all the layers of software and operating systems that were installed. Just my thinking on where to start. Perhaps boot into the live cd, and if it's Ubuntu, use this command or something similar:

sudo shred --force --iterations=0 --verbose --zero /dev/sdX


I'm sorry as this really doesn't help much, but maybe as a way to deduce potential causes, it might.

I've ran across this sort of trouble when I was trying to install Ubuntu on an older laptop I had. It would freeze during random times, have really unusual and odd problems, and always seem to occur no matter if it was Ubuntu, Fedora, OpenSuse, Windows, whatever. And for it, it turned out to be a hardware thing.

---

### Post by w0Rm210 on 2010-06-02
Thanks i'll defiantly try that and if it is a hardware problem do you have any clue as to what it might pertain to?

---

### Post by inameiname on 2010-06-02
More times than not it's a hard drive issue. Though, from my experience with some friends and family I have, and their constant need to hit a computer when they are frustrated, it could be a number of things. ;) hehe. Anyway, I would say hard drive, which you can get relatively cheap. One way to check this out is if you have a spare one laying around, or can borrow one or something, then you can test that theory. Sometimes it can be the result of overheating, or of low ram, among other things.

---

### Post by w0Rm210 on 2010-06-02
Yeah it could very well be RAM i ment to add some but we ended ourselves up in a motel and i haven't had the time... I'm wiping the hardrive now and installing ubuntu fully to the hard drive as i (now) have no reason to dual boot lol but thank you very much i thought i was gonna lose my frickin' mind

---

### Post by inameiname on 2010-06-02
Alrighty. Well just remember when I mean erase, I mean actually erase, not just installing Ubuntu or Kubuntu or whatever you want.

And as I said, how I'd go about this is to boot into the Live Cd, as you probably would anyway, and just before you install it, you enter that command that I gave you, to fully overwrite the whole thing, making it like factory new. Depending on the size of your hard drive, and amount of ram, it might take an hour, or more. However, that command is the fastest, as it just overwrites it all in '0's, and only once, so it'll be the quickest.

sudo shred --force --iterations=0 --verbose --zero /dev/sdX


And also, I can't remember if shred is already installed on the Ubuntu ISO from their site. If not, just type this first:

sudo apt-get install shred

And then once that is finished, just install normally and go from there. It's an extra step, but to appease your mind in wondering if it might be all the past things underneath.

---

### Post by w0Rm210 on 2010-06-02
Alright it's shredding things up now man i hoped it woulden't have to go this far..... Man thank you sooo much i never woulda thought about something like that i haven't used linux very long... Only used Ubuntu on and off since 7.10 release lol but thanks :D

---

### Post by inameiname on 2010-06-02
No prob. Hope that at least helps to narrow things down for ya.

---

### Post by w0Rm210 on 2010-06-02
alright i got a new error trying to shred it said shred: /dev/sdX: failed to open for writing: No such file or directory... Any clue?

---

### Post by inameiname on 2010-06-02
Oh, you have to figure out what your hard drive is. sdX is just a generic term. It could be sda, sdb, sdc, etc. 

It's probably /dev/sda

---

### Post by w0Rm210 on 2010-06-02
Wow i'm tired lol i just went with the quickest looking thing (no not a complete noob) lol just confused and it's been a while... Thanks xD

---

### Post by inameiname on 2010-06-02
Quickest shredding is my choice too. It'll do exactly the same as the really slow ones, minus the potential of the government or a good hacker to read what was erased. hehe. Not a huge issue for me.

---

### Post by w0Rm210 on 2010-06-02
Scratch that.... Same problem on battery power plays the startup sound a few hundred times skipping and skipping then flies into a black screen >_< ERK man man man i'm going nuts.

---

### Post by inameiname on 2010-06-02
Well then...I'm more inclined to call it a hardware issue then. Of course, to be really sure of that, install Windows and see if you get funky errors. That would tell you that it's gotta be the hardware if it gets screwy, especially regarding things like battery troubles (hardware stuff), with both fresh installs of Linux and Windows.

---

### Post by w0Rm210 on 2010-06-02
Eh that's the thing is i'd rather die than put windows back on this machine i would consider hackintosh but to get windows i would have to pirate it or somethin illegal considering i never backed up my old system or bought windows =/ kinda a drop lol But i can always just use my lappy with ubuntu on charge it's just i'm at a hick motel where i gotta walk to get wifi and no place to plugin but i don't get how the hardware could all of a suddon get funky when it was fine up until two nights ago.....

---

### Post by inameiname on 2010-06-02
Yeah, that's too bad. I just meant to install Windows for a moment only, so as to see if any potential hardware issues occur, that's all. Of course, as you said, you need a Windows installation disc to do even that. Though, you really don't need a license for it, as you aren't planning on using it for more than a short moment, and I think you normally have 30 days with it. Regardless, this doesn't seem like an easy thing for you to do where you are at the moment, so guess that option is out.

Let's see, how about try another Linux distribution? About all I can tell you.

Oh, how about running it entirely in the Live cd, and see if you get any hardware trouble in there. If you aren't in regards to say the battery, as you are with the actual installation, then that'll help narrow things down for ya. And also, if it is a hard drive problem, you'd have no issues with a Live CD since you aren't using the hard drive. IDK. Something I guess.

---

### Post by w0Rm210 on 2010-06-02
Actually during the ubuntu install i took it off ac power as a test and it worked fine but once the OS loaded it just froze i'm beggining to think it's a power supply thing battery meter is lying to me..... Never know but i will because the ubuntu default is to hibernate when the battery gets low so when i boot it's just saying BATTERY LOW and shutting off so i'm thinking supply problems as a new possibility.

---

### Post by inameiname on 2010-06-02
It could be. Good job with deduction. How old is your battery? Have you ever installed hardinfo? 

sudo apt-get install hardinfo

It's like System Information for Windows, and under the battery section it'll tell you how much of a charge your battery sustains and all that. Pretty simple tool, but maybe it'll show something different than what the battery meter tells you.

Another interesting application is battery-status, found here:

[http://www.webupd8.org/2010/05/battery-status-011-fixes-lots-of-issues.html](http://www.webupd8.org/2010/05/battery-status-011-fixes-lots-of-issues.html)

It'll give you tons of info about your battery. I've tried it a couple of times, but it seemed to give too much info, most I really don't care about. :P

---

### Post by w0Rm210 on 2010-06-03
Wow in battery it actually gave me 90.6% capacity but the monitor was at 96.0% thanks for the nifty tool i usually just use ubuntu for basic stuff gaming and youtube but i've always used windows for some reason even though i hate it... But i'm just gonna take this drone apart i gotta add RAM a new wifi card and other stuff but hey bro thank you for your effort and stuff i know you probably googled the hell out of everything lol thanks man and did i mention this forum is great? Lol well i'm gonna get to fixing this problem.

---

### Post by inameiname on 2010-06-04
Sure, no prob. Yeah, this is one great forum. Has definitely helped me out a few times when I've been in a bind. Good luck!

---

### Post by w0Rm210 on 2010-06-06
Oh yeah one more question, is it possible it's a screen problem? Because now i can't boot into it at all on charger or off is it just crappy hardware? Should i call compaq? I got a 1 year warenty on it but with everything i've done on it they might not trade it in. Any suggestion? Because it's getting on my last nerv it was working fine until my mom spilled some jager on it then it was screwy but it worked up until i closed the screen and when i opened it it never worked since... I should call compaq eh?

---

### Post by coldraven on 2010-06-06
I think your problem might be doing installs on battery power.
Could be that the computer is going to sleep before the install is complete.
Run the Live CD and make sure that you disable the sleep/suspend in the power management window.(System/Preferences/Power management)

Also disable the screensaver, my installs of Ubuntu freak me out when the screen goes black after ten minutes! If it does don't press the spacebar or Enter to wake it up or you may stop the install doing something. I always press the right arrow key, it's safer!

Good luck :)

---

### Post by inameiname on 2010-06-07
Good suggestion 'coldraven'. You never know. :)

And as far as your theory, I really don't know w0Rm. Jager on it ehy? ;) Interesting trouble. That stuff does mess you up, in more ways than one. Uhm, if it got into things, who knows could be the issue. Spills are so unpredictable, and the problems that come with such regarding electronics are hard to figure out for certain. Thus, could also be something got wet inside and was fried, who knows. Again, this is way beyond my expertise. Best not to give you too many possibilities from something who isn't an expert either. :P

---

