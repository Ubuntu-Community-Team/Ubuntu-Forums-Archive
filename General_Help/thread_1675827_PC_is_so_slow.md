---
title: "PC is so slow"
date: 2011-01-26
forum: General Help
---

### Post by Gary777 on 2011-01-26
Hi, I wonder if anyone can help me, I run linux 10.04 (I think)
but just lately it has went so slow, perhaps 5 minutes to open a file, 10 mins to play a movie (VLC) and sometimes it pause's while watching, and builds up buffering to 100% then begins again.

Is it my motherboard, I read online something to do with >>>>

[COLOR="DarkOrange"]Whenever your system has a really big bug, a file with the name "core" is created. The content of this file is an image of what happened at the time of the really big bug. Therefore, this "core" file is very large. If you have one or more of these files on your system, it might saturate because there is not enough memory anymore.[/COLOR]<<<<<

So I opened terminal and pasted (locate core)
and got lot's of stuff, but how do I know if there is a problem

Load Averages for the last 1, 5, 15 mins I have seen 2.70 ish for all of them, but looking at them now 0.08, 0,61, 1.13
but thats not normal, there way higher than that, also it took around 15 minutes to boot up.
Motherboard (shot) has been suggested
any pointers ?

Thank You.
Gary

---

### Post by dandnsmith on 2011-01-26
> **Gary777 said:**
> Hi, I wonder if anyone can help me, I run linux 10.04 (I think)
but just lately it has went so slow, perhaps 5 minutes to open a file, 10 mins to play a movie (VLC) and sometimes it pause's while watching, and builds up buffering to 100% then begins again.

Is it my motherboard, I read online something to do with >>>>

[COLOR="DarkOrange"]Whenever your system has a really big bug, a file with the name "core" is created. The content of this file is an image of what happened at the time of the really big bug. Therefore, this "core" file is very large. If you have one or more of these files on your system, it might saturate because there is not enough memory anymore.[/COLOR]<<<<<

So I opened terminal and pasted (locate core)
and got lot's of stuff, but how do I know if there is a problem

Load Averages for the last 1, 5, 15 mins I have seen 2.70 ish for all of them, but looking at them now 0.08, 0,61, 1.13
but thats not normal, there way higher than that, also it took around 15 minutes to boot up.

*locate core* doesn't give you the locations of any core files - look at the man pages for *locate*
I'd try under /var or /tmp. Anyway they only occupy HDD storage, not RAM, so won't affect normal running, unless you're severely short of filespace.

Might be a mobo problem, but I think more likely it's HDD access time which is slowing it.

VLC is a heavy usage thing - but you can often see the resultant stuttering of picture/sound if it is overloaded - as you have - but this could be a graphic speed problem.

---

### Post by Gary777 on 2011-01-26
> **dandnsmith said:**
> *locate core* doesn't give you the locations of any core files - look at the man pages for *locate*
I'd try under /var or /tmp. Anyway they only occupy HDD storage, not RAM, so won't affect normal running, unless you're severely short of filespace.

Might be a mobo problem, but I think more likely it's HDD access time which is slowing it.

VLC is a heavy usage thing - but you can often see the resultant stuttering of picture/sound if it is overloaded - as you have - but this could be a graphic speed problem.

Thanx Derek, but very new to Linux, can you suggest what to look for, more importantly how 
Kind Regards
Gary

---

### Post by Gary777 on 2011-01-26
Thanx Derek, but very new to Linux, can you suggest what to look for, more importantly how
Kind Regards
Gary

I cant find quick reply button, I did but not the one I am meant to find

---

### Post by IWantFroyo on 2011-01-26
Updating your drivers might help (additional drivers). If nothing works, you might want to backup your files and livecd upgrade to 10.10.

---

### Post by dandnsmith on 2011-01-27
You can get the Ubuntu version by using the System menu (on Preferences list *About Ubuntu*)

A list of the actual PC parameters might help - someone could say whether the hardware is really capable (I don't know the stuff very well, but have had one configuration fail to work, and several others OK). In a terminal window, issue the *sudo lshw* command (lowercase ell again) - this will get a lot of output, so arrange to capture it for reading/posting.

I would do:
lshw >lshw_output.txt
with the output.txt as the output.

---

### Post by Gary777 on 2011-01-27
> **dandnsmith said:**
> You can get the Ubuntu version by using the System menu (on Preferences list *About Ubuntu*)

A list of the actual PC parameters might help - someone could say whether the hardware is really capable (I don't know the stuff very well, but have had one configuration fail to work, and several others OK). In a terminal window, issue the *sudo lshw* command (lowercase ell again) - this will get a lot of output, so arrange to capture it for reading/posting.

I would do:
lshw >lshw_output.txt
with the output.txt as the output.

Hi Derek thanx for your time, it's apreciated.
Re: the data, there's allot, trying to do anything with the PC takes a  great deal of time, yet I watched a movie last night and it paused only once for a couple of seconds, today it's like treacle, but allot worse.
There is so much data, I can snip it, but it will mean at least 6 or so pictures, perhaps if possible we can narrow it down a little,

Regards
Gary

---

### Post by dandnsmith on 2011-01-27
I wasn't really thinking you'd post the lot (there always is a large amount) - merely extract the vital details about cpu, RAM, graphics etc. I think (but not entirely sure) that if you post it as 'code' (see # at the top of the post window) that it will add scroll bars if too long or too wide.

Did you use the same film each time? There is a possibility that the details of the coding may be enough different to affect it (for example, I found on my 'bad' configuration I could play a black and white film, but not one in colour).

---

### Post by Gary777 on 2011-01-27
> **dandnsmith said:**
> I wasn't really thinking you'd post the lot (there always is a large amount) - merely extract the vital details about cpu, RAM, graphics etc. I think (but not entirely sure) that if you post it as 'code' (see # at the top of the post window) that it will add scroll bars if too long or too wide.

Did you use the same film each time? There is a possibility that the details of the coding may be enough different to affect it (for example, I found on my 'bad' configuration I could play a black and white film, but not one in colour).

Derek, I am usless when it come to the PC, however 2gb ram duel core 4800, Lucid lynix, n-videa 8400, 
Re: the movie, nope this was just an other movie, hadn't watched this before,
Tonight it has taken around 15mins to open and play VLC, what made it worse I think was it was extracting and repairing some download.....

---

### Post by dandnsmith on 2011-01-28
That extract+repair could account for a lot - the VLC is highly intensive and can take a fair bit of RAM as well.
I'd suggest trying to get a feel when there isn't anything else going on - not that that is always easy.
Do you have the cpu type and speed?

---

### Post by Gary777 on 2011-01-28
> **dandnsmith said:**
> That extract+repair could account for a lot - the VLC is highly intensive and can take a fair bit of RAM as well.
I'd suggest trying to get a feel when there isn't anything else going on - not that that is always easy.
Do you have the cpu type and speed?
Hi Derek
CPU I think is AMD Athlon duel core 4800 does that make sense ?
The PC takes about 10 t0 15 mins to boot up, just to open a folder is a couple of mins, no vlc running.
I've been told it might be the motherboard.

---

### Post by dandnsmith on 2011-01-28
That spec is as fast as the one of mine which runs such stuff as videos without trouble.
The bootup time seems excessive - I'd be looking for a bit more evidence to pin it down
- how much time before the outline desktop appears?
- is it long then before the menus bars and any applications have got going?
- just how many applications do you start automatically?
- could you clear it so these are not started automatically?

for example a Ubuntu10.04 of mine on an AMD XP 1800+ with 1GB RAM
- takes 45 secs to boot  as far as desktop complete with 4 small apps running

---

