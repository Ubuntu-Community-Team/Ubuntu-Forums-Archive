---
title: "System sound Not working"
date: 2010-05-24
forum: General Help
---

### Post by pr0t3g3 on 2010-05-24
I don't know how it happened but I can't seem to adjust or even hear sound on my laptop anymore.  When I try to click on the sound icon at the top right it merely says:
Waiting for sound system to respond; but it never does.  I restarted my pc and even tried manually shutting it down, but nothing seems to work.  Any way I can MAKE it work?

Edit:  it still plays sound at the same sound level as before I couldn't adjust it, however even though I have sound I cannot adjust it.

---

### Post by dino99 on 2010-05-24
which distro are you talking about ? i've not magic power :(

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by pr0t3g3 on 2010-05-24
> **dino99 said:**
> which distro are you talking about ? i've not magic power :(

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
I'm using 10.04 lucid

Your link didn't help me.  It seems I do have sound at a low volume.  However it refuses to let me open the menu to adjust it, claiming, that it's waiting for the sound system to respond... ooookaaay... but when the flip is it going to respond?

Note:  aside from selecting the system sound icon, I have 2 other ways to adjust the volume on my dell inspiron 8600 laptop; one with the fn button and another with the plain old up/down and mute buttons.. neither ways work.  It was a bit slow to respond in the past but no more than 3 seconds... whats going on?

---

### Post by pr0t3g3 on 2010-05-24
>.>
 

<.< 



BUMP!!



:evil:

---

### Post by razorboy5 on 2010-05-24
has it worked b4 in the older ubuntu versions?

what sound care are u using?

what happens when u run alsa mixer in terminal?

i've had similar problem back in the day with 9.04 and 9.10
switching to OSS4 fixed the problem for me

---

### Post by pr0t3g3 on 2010-05-24
> **razorboy5 said:**
> has it worked b4 in the older ubuntu versions?

what sound care are u using?

what happens when u run alsa mixer in terminal?

i've had similar problem back in the day with 9.04 and 9.10
switching to OSS4 fixed the problem for me
This is my first time using ubuntu; I started a week or so ago.  I learn fast though..... alsa mixer?  isn't that a sound device used in kubuntu?  I'm using ubuntu 10.04 lucid and no to my knowledge (my friend gave this to me... it's old but new enough to get the job done.. nothing that great either.)  I don't think there have been any sound problems, I'll ask him.  

However I noted that there was a second or two of lag when adjusting the volume with the buttons on the keyboard.. nothing serious... I've noticed that this pc is glitchy.. so the thing is I coulda modified something without knowing >.<

never mind that now. I have the normal setup for sound no mods or anything.  I don't think I made any serious modifications I probably glitched the sound.. how do I edit it so that it will start fresh?

---

### Post by razorboy5 on 2010-05-24
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
i had the problem too when sound was very faint and i couldn't adjust and when i tried to open pulseaudio it gave me an error message (can't remember what it was) but switching to OSS4 fixed that problem. OSS4 has it's separate forum as well (although i dont think alot of ppl use it anymore except a few members dedicated to OSS4 and to help ppl moving to it)

also it seems like ur friend knows alot more about ubuntu and maybe he can further diagnose the problem. 

and i believe alsamixer is used to control the volume in ubuntu as well. i have alsamixer v1.0.22 installed from fresh lucid install

in terminal just run 
```
alsamixer
```

maybe it'll let u change the volume that way

---

### Post by pr0t3g3 on 2010-05-24
> **razorboy5 said:**
> [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
i had the problem too when sound was very faint and i couldn't adjust and when i tried to open pulseaudio it gave me an error message (can't remember what it was) but switching to OSS4 fixed that problem. OSS4 has it's separate forum as well (although i dont think alot of ppl use it anymore except a few members dedicated to OSS4 and to help ppl moving to it)

also it seems like ur friend knows alot more about ubuntu and maybe he can further diagnose the problem. 

and i believe alsamixer is used to control the volume in ubuntu as well. i have alsamixer v1.0.22 installed from fresh lucid install

in terminal just run 
```
alsamixer
```maybe it'll let u change the volume that wayactually he knew about previous version's of ubuntu.. 8. something?  Now I don't know what he's doing.... anyways...  I'm not interested in changing everything around (switching os's) just because the sound is 'faint'  ... is there anyway to reset the volume?  or is there no way to do such a thing.... I tried restarting in fact I've done it a few times already... please I love ubuntu tell me what I can do to fix this!

---

### Post by razorboy5 on 2010-05-24
actually OSS4 is not an operating system (it stands for open sound system) it's a sound driver for when pulseaudio is not compatible with ur sound card (it explains in the documentation i posted above) 

but sry i do not have the expertise to figure out the problem and fix this for u, hopefully some1 more experienced may see this thread :S

---

### Post by pr0t3g3 on 2010-05-24
> **razorboy5 said:**
> actually OSS4 is not an operating system (it stands for open sound system) it's a sound driver for when pulseaudio is not compatible with ur sound card (it explains in the documentation i posted above) 

but sry i do not have the expertise to figure out the problem and fix this for u, hopefully some1 more experienced may see this thread :Slmao... I'll bet at least 10 have, they just have way more important problems to take care of such as failed internet connections and other bad stuff. T_T oh well.  honestly though I can go without sound It's not a major hindering factor.. unless I do something where sound is required...>.< sorry I'm a bit tired atm... I've acutally heard of that oss4 in passing when I used to use windows and so I should have known that's what you were talking about... it's an audio device

---

### Post by beefone on 2010-05-24
Hi,

Open up a terminal and try 
```

sudo pulseaudio --kill
cd ~/
rm -rf .pulse*
sudo pulseaudio --start -D

```
That seemed to fix the issue on my laptop after the upgrade.

---

### Post by pr0t3g3 on 2010-05-24
> **beefone said:**
> Hi,

Open up a terminal and try 
```

sudo pulseaudio --kill
cd ~/
rm -rf .pulse*
sudo pulseaudio --start -D

```That seemed to fix the issue on my laptop after the upgrade.
E: core-util.c:[COLOR=Red] Home directory /home/anthony not ours.[/COLOR]
E: main.c: [COLOR=Red]Failed to kill daemon: Permission denied[/COLOR]

what the flip is daemon?

edit:  The program 'daemon' is currently not installed.  You can install it by typing:
sudo apt-get install daemon
o.O  if it's not installed then wth?

---

### Post by pr0t3g3 on 2010-05-25
[COLOR=Red][SIZE=6][U][I][B]BUMP!!!!


[/B][/I][/U][/SIZE][/COLOR][COLOR=Red][SIZE=6]_***:evil:***_[/SIZE][/COLOR]

[COLOR=Red][SIZE=6][/SIZE][/COLOR]

---

### Post by pr0t3g3 on 2010-05-25
sudo pulseaudio --start -D
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: core-util.c: Home directory /home/anthony not ours.
W: lock-autospawn.c: Cannot access autospawn lock.
E: main.c: Failed to acquire autospawn lock

  ARGH! this doesn't seem to have a simple fix!! somebody *please *help me with this!

---

### Post by benplanet on 2010-05-30
getting same error: E: core-util.c: Home directory /home/anthony not ours.
E: main.c: Failed to kill daemon: Permission denied


my pulse audio won't start... (even tho it's added to the startup apps) 



Anyone??:(

---

### Post by pr0t3g3 on 2010-05-30
> **benplanet said:**
> getting same error: E: core-util.c: Home directory /home/anthony not ours.
E: main.c: Failed to kill daemon: Permission denied


my pulse audio won't start... (even tho it's added to the startup apps) 



Anyone??:(why did you same home/anthony?  Anthony is my username... if yours isnt the same as mine then that's a little silly to add that part... are you really having the same problem as me?

---

### Post by Ozymandias_117 on 2010-05-31
Try:
```
pulseaudio --kill
cd ~
rm -rf .pulse*
pulseaudio --start -D
``` (Same command as previously posted, but without sudo)

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> Try:
```
pulseaudio --kill
cd ~
rm -rf .pulse*
pulseaudio --start -D
``` (Same command as previously posted, but without sudo) pulseaudio --kill
E: main.c: Failed to kill daemon: No such process
anthony@anthony-laptop:~$ cd ~
anthony@anthony-laptop:~$ rm -rf .pulse*
anthony@anthony-laptop:~$ pulseaudio --start -D

 The way I see it, my pc is *confused.* I was trying to end pulse-audio .. where is it getting daemon from? Is daemon a template or... ah geez..

---

### Post by Ozymandias_117 on 2010-05-31
> **pr0t3g3 said:**
> pulseaudio --kill
E: main.c: Failed to kill daemon: No such process
anthony@anthony-laptop:~$ cd ~
anthony@anthony-laptop:~$ rm -rf .pulse*
anthony@anthony-laptop:~$ pulseaudio --start -D

 The way I see it, my pc is *confused.* I was trying to end pulse-audio .. where is it getting daemon from? Is daemon a template or... ah geez..

A daemon is simply a program that runs in the background on your system. The commands did what they were supposed to.

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> A daemon is simply a program that runs in the background on your system. The commands did what they were supposed to.


nah... they don't work... I copied and pasted the whole thing at once. . . the piece of crap just  put an error after the*** first *** line and then placed the next parts of the  series of commands you gave me afterwards :popcorn:
I got this message still ;D
Waiting for sound system to respond

Edit: I didn't copy and paste one line at a time.. like I said I took the whole box and pasted it into terminal and the above happened ^

---

### Post by Ozymandias_117 on 2010-05-31
> **pr0t3g3 said:**
> nah... they don't work... I copied and pasted the whole thing at once. . . the piece of crap just  put an error after the second line and then placed the next parts of the  series of commands afterwards :popcorn:
I got this message still ;D
Waiting for sound system to respond

The error after the second line was saying that it couldn't run it, because it was already true. So, that means there was no reason to run the first command.

I'm not sure what to do for your problem, I just saw the error messages given off from beefone's commands and thought I would tell you how to get the commands to run.

Edit: Try running them one line at a time then - That first error wouldn't have screwed up the results, but I don't know if they would have all run properly being pasted in like that... I've never tried it.

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> The error after the second line was saying that it couldn't run it, because it was already true. So, that means there was no reason to run the first command.

I'm not sure what to do for your problem, I just saw the error messages given off from beefone's commands and thought I would tell you how to get the commands to run.

Edit: Try running them one line at a time then.
but it still didn't work!  it said it didn't even recognize the first command.. the one that seemed to be vital!  There must be something else you can try.. please don't give up on me..

---

### Post by Ozymandias_117 on 2010-05-31
> **pr0t3g3 said:**
> but it still didn't work!  it said it didn't even recognize the first command.. the one that seemed to be vital! 

No, it said that it couldn't stop the process because the process wasn't running, not that it couldn't recognize the command.

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> No, it said that it couldn't stop the process because the process wasn't running, not that it couldn't recognize the command.
So is it vital that I ***make ***it run?

---

### Post by Ozymandias_117 on 2010-05-31
> **pr0t3g3 said:**
> So is it vital that I ***make ***it run?

Just run the four commands in the terminal, one at a time. If the first one gives off that same error message, ignore it.

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> Just run the four commands in the terminal, one at a time. If the first one gives off that same error message, ignore it.
Mirror image from before... nothing different.. its all the same. Anything else I can try? Trust me I've searched everywhere. I've checked out my sound card and all my other drivers and stuff (took it to someone who took it apart and checked to see if the hardware is good)  and so I know it's not a hardware problem.. nothing in the forums or on google helps me with this problem... I need a solution to this.. Come on there has to be one!

---

### Post by Ozymandias_117 on 2010-05-31
```
sudo pulseaudio --start --system -D
```

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> ```
sudo pulseaudio --start --system -D
```
sudo pulseaudio --start --system -D
[sudo] password for anthony: 
E: main.c: --start not supported for system instances.
anthony@anthony-laptop:~$ 



Next command please?

---

### Post by Ozymandias_117 on 2010-05-31
Oops
```
sudo pulseaudio --system -D
```

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> Oops
```
sudo pulseaudio --system -D
```
uhm?  
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!



Alright .. so I can enter the menu now and adjust sound from my keyboard.. but can you explain to me why those intimidating commands were needed and what they did?

---

### Post by Ozymandias_117 on 2010-05-31
Looks like it still loaded, it's just upset some values weren't set. Did it effect your sound settings at all?

---

### Post by pr0t3g3 on 2010-05-31
> **Ozymandias_117 said:**
> Looks like it still loaded, it's just upset some values weren't set. Did it effect your sound settings at all?
View page 3 and answer my question at the end of my post, please.  ^_^!!!

---

### Post by Ozymandias_117 on 2010-05-31
> **pr0t3g3 said:**
> uhm?  
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!



Alright .. so I can enter the menu now and adjust sound from my keyboard.. but can you explain to me why those intimidating commands were needed and what they did?

The whole problem is that pulseaudio didn't want to load. We've been trying to get it to load both just for you (The way it's supposed to work now - All the times we did it without sudo). Since, for whatever reason, it wouldn't start that way, that last command got it to load across the entire system. Apparently, it did finally load this way.

---

### Post by Ozymandias_117 on 2010-05-31
To make sure it doesn't break when you reboot your computer, type ```
gksudo gedit /etc/rc.local
``` and add ```
pulseaudio --system -D
``` right before the line "exit 0"

---

### Post by benplanet on 2010-05-31
I'm giving up, tried everything in this thread, and ever purrged and reinstalled pulseaudio...nothing worked. Whatever I do, I get the "waiting for system sound" prompt. I have a a hunch this might have been caused by incorrect permissions or me login in to root (which i only did once! ive now disabled it)

I should mention that sound works, it's just that i cannot adjust it or do anything with it. 


any other commands I could try before reinstalling ubuntu? :(

---

### Post by pr0t3g3 on 2010-05-31
> **benplanet said:**
> I'm giving up, tried everything in this thread, and ever purrged and reinstalled pulseaudio...nothing worked. Whatever I do, I get the "waiting for system sound" prompt. I have a a hunch this might have been caused by incorrect permissions or me login in to root (which i only did once! ive now disabled it)

I should mention that sound works, it's just that i cannot adjust it or do anything with it. 


any other commands I could try before reinstalling ubuntu? :(

Yeah I think your right.. ubuntu's sound thing on my laptop is a glitchy piece of crap...As for 'more commands'  I had to literally pull the answer out of  ozy in pms till he just posted some stuff here.. the admins and mods/staff know.. their either up to their necks in other forums/threads or they think mine is a waste of their time.  Somehow I think reinstalling will be less agonizing then pulling answers from them!

---

### Post by benplanet on 2010-05-31
> **pr0t3g3 said:**
> Yeah I think your right.. ubuntu's sound thing on my laptop is a glitchy piece of crap...As for 'more commands'  I had to literally pull the answer out of  ozy in pms till he just posted some stuff here.. the admins and mods/staff know.. their either up to their necks in other forums/threads or they think mine is a waste of their time.  Somehow I think reinstalling will be less agonizing then pulling answers from them!

well, they do their best, don't want to take anything away from valiant efforts of this community. But If it's pulseaudio specifically that you're talking about, I agree, it has giving me (and countless others) nothing but headaches since the earliest version of ubuntu. cannocial oughtta do something about it soon.

---

### Post by pr0t3g3 on 2010-05-31
> **benplanet said:**
> well, they do their best, don't want to take anything away from valiant efforts of this community. But If it's pulseaudio specifically that you're talking about, I agree, it has giving me (and countless others) nothing but headaches since the earliest version of ubuntu. cannocial oughtta do something about it soon.
ah man... I thought it was just my pc and it's setup... so many others too?  No wonder this post has been by-passed... it's common problem, not worth answering T_T

What really get's me is I didn't have a problem with it earlier on... and I did nothing that would glitch it so badly ( that I know of)  No programs were installed newly when I started having problems.. so .. that's out...no conflicts there.

---

### Post by benplanet on 2010-05-31
> **pr0t3g3 said:**
> ..
What really get's me is I didn't have a problem with it earlier on... and I did nothing that would glitch it so badly ( that I know of)  No programs were installed newly when I started having problems.. so .. that's out...no conflicts there.


Same. I'll go as far as saying this was one of my all time best ubuntu setups. everything was on point and perfect! In fact, I was just about to create an image of my perfect OS, and then bam! pulseaudio jinxed it all :)

---

### Post by pr0t3g3 on 2010-06-07
> **benplanet said:**
> Same. I'll go as far as saying this was one of my all time best ubuntu setups. everything was on point and perfect! In fact, I was just about to create an image of my perfect OS, and then bam! pulseaudio jinxed it all :)
Hopefully this 'long term support' for lucid lynx will include sound perfection >.>... It really is strange how something like sound can be an extremely important factor in computing and other daily tasks...My default sound scheme is on the fritz again.  Yesterday (before I shut down and restarted my computer) my sound was adjustable again, and I did nothing to troubleshoot.. in fact I did nothing that would even go with sound at all insofar as configuring options ( I did download a massive update)  but it worked.. then I restarted my pc and BAM! Since I muted it before I did it I now have NO sound whatsoever.  This is a major inconvenience, and until it's fixed I think it's time for alternative operating systems.  I refuse to give up ubuntu.. I can't believe using this operating system has done so much for me.. Thanks to ubuntu I had to learn about the command line (whether I wanted to or not)and I've learned loads; what's more is I've had a better experience. I have nothing but praise.  My hope in the future is that with the following updates, Ubuntu will be a fully functioning os; I'm sad (or happy) to say that I'll probably be able to set up an os by scratch by then, as I'm learning all about computer languages and builds at college. It's going to be my future ^_^.... so I guess for the most part I'm going to be using different operating systems.. which annoys me as ubuntu is all I need.. darn pulseaudio...

---

### Post by Subito Piano on 2012-07-18
To anyone following this thread (maybe history buffs?) -- for me, i could play music - it was the system sounds that didn't work (Thunderbird "new mail" sound, screenshot "shutter" sound, etc.).  

I yanked pulseaudio.  All is well again.

(Note for newbies: anytime you uninstall anything -- be sure to check what else it will uninstall with it.  You DON'T want to lose any of your favorite apps.)

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

