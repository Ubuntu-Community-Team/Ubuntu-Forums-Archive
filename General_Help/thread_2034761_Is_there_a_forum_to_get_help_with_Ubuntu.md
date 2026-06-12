---
title: "Is there a forum to get help with Ubuntu?"
date: 2012-07-28
forum: General Help
---

### Post by AbeFM on 2012-07-28
Folks, I get it  no amount of describing my problems will generate ANY advice. Can you tell me where to go?

I went from a functioning machine to something which loses the bass channel every half hour, gets the sound card output bit shifted into sci-fi movie static effects a few times a day, and now gets stuttering in the sound a few times an hour.

The computer used to reboot when you select "reboot", and now it just goes to the log in screen.

The DVD Rom closes on discs before you can even remove them from the tray.

All I've done since a clean re-install is allow automatic updates.

I've offered to log anything, look up anything, to help in ANY way to help solve these problems for the community. Well, I don't care about the community any more - they don't care for me. I don't want to be in a thread of 30 people saying they have the same unanswered questions any more.

So please, tell me if there's a place where I can find a way to make my computer run as well as it did when I was using 10.04. If it's another forum where people will help, I'm all ears. I've posted to death problems no one will listen to.

---

### Post by vasa1 on 2012-07-28
Oops! Actually, this is the first time I've seen a post by you. Maybe it's a matter of time zones and the 250 newest posts limitation (which I really wish wasn't there).
In any case, I'm just making excuses for why others may have missed your post. I don't know much about your present question.

---

### Post by AbeFM on 2012-07-29
[http://ubuntuforums.org/showthread.php?t=1885240&highlight=audio+troubleshooting&page=9](http://ubuntuforums.org/showthread.php?t=1885240&highlight=audio+troubleshooting&page=9)
Post 89

[http://ubuntuforums.org/showthread.php?t=1986816](http://ubuntuforums.org/showthread.php?t=1986816)

[http://ubuntuforums.org/showthread.php?t=1981975](http://ubuntuforums.org/showthread.php?t=1981975)

The not rebooting thing is new, as are the bouts of skipping. I thought it was network issues at first, but now I get it even when playing local media.

Read the audio tutorial thread. It's pages of people saying "yeah, me too" or "is there a single person who has any idea of what's going on here in this thread".....


I've worked on some open source projects before - they live and breath on the support of the people who know what's going on, and on keeping the users in the fold. While I'm encouraged by a small amount of flexibility coming back in recent months, overall, my computer _fails to do basic things like play sounds_. How can you tout the benefits of an operating system which makes it hard to do anything your average phone can do for $90 without a hitch?

It's not rocket science, it's something free or paid OS's have been doing for 15 years. You don't see the new Volvos coming off the lot with wheels falling off - so how is a broken OS an upgrade?

Anyway - I'm not here to insult anyone - I just want to know if there's a place where I might actually get some help.

---

### Post by dcstar on 2012-07-29
> **AbeFM said:**
> 
...........
Anyway - I'm not here to insult anyone - I just want to know if there's a place where I might actually get some help.

What is the Launchpad Bug report number that **you** have lodged?

---

### Post by AbeFM on 2012-07-29
> **dcstar said:**
> What is the Launchpad Bug report number that **you** have lodged?

[https://bugs.launchpad.net/bugs/1004593](https://bugs.launchpad.net/bugs/1004593)


Again, <irony> thanks for being super helpful </irony>. It's not my fault if I'm willing to learn and give detailed information. This forum makes people with questions feel like the enemy.

In other news, AskUbuntu, while even more cumbersome, has already solved two issues for me tonight. Very, very impressed.

LFE channel disappearing:
[http://askubuntu.com/questions/53802/subwoofer-sound-preferences-problem](http://askubuntu.com/questions/53802/subwoofer-sound-preferences-problem)

Computer logging out instead of shutting down:
[http://askubuntu.com/questions/122304/shutdown-or-restart-logs-out?rq=1](http://askubuntu.com/questions/122304/shutdown-or-restart-logs-out?rq=1)

---

### Post by mastablasta on 2012-07-29
that's not a propper bug report. note how it was marked as opinion in launchpad.
so you followed this: 
[https://help.ubuntu.com/community/SoundTroubleshooting/](https://help.ubuntu.com/community/SoundTroubleshooting/)
And this to find the right package: [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)
so you can make the bug report propperly.

the operating system can do the asounds as long as hardware is compatible with it. and if you have propper drivers installe. i dare you to try and stick windows 7 on those phones and see if everything works.it won't because that hardware is not supported by windows 7. neither did the manufacturers provide any drivers on their own.

another option is to use cannonical payed support. or you can always use another OS on that maschine (MacOS, Windows7, Vista, Solaris.Free BSD, another linux distribution...)

if it worked in 10.04 and doens't work now it could be either kernel bug or bug within alsa. if it's like that it would be best to stick with 10.04 (supported until 2013, some packages a bit longer...) and feed the developers all information possible so they can fix it.

edit:

also no need to write novels on bug report.
this should be enough with a good title and necessary logs and informaitons posted along with it. wll maybe you can add a bit but just informaiton you think it would help resolving the issue.
> I went from a functioning machine to something which loses the bass  channel every half hour, gets the sound card output bit shifted into  sci-fi movie static effects a few times a day, and now gets stuttering  in the sound a few times an hour.

---

### Post by Jimmyfj on 2012-07-29
> **AbeFM said:**
> So please, tell me if there's a place where I can find a way to make my computer run as well as it did when I was using 10.04. If it's another forum where people will help, I'm all ears. I've posted to death problems no one will listen to.

I'm not claiming to have knowledge about the problems you encounter. But since your problems just started after 10.04 my suggestion is that you add those repos from 10.04 that holds your sound drivers as I think that your new version of Ubuntu simply have dropped those drivers for what ever reason. So add the repos to your /etc/apt/sources.list and hunt the right driver down.

As for your problem on restart. It seems that you for whatever reason no longer have the privileges needed to reboot the system. Check your rights and allow yourself to administer the computer (almost root privilege). I had the the same issue some versions ago but this tip made it go away.

Come to think about it, but not at all sure: Maybe these other problems are influenced by the lack of  rights too.

---

### Post by AbeFM on 2012-07-29
Again, I'm not looking to get in a pissing match here. You've got someone who can and will get any logs, run any command, put in some hours.... But can't get anywhere without a helping hand. The purpose of reporting a bug is to improve the system for everybody, and when I see other folks coming back with the same issues, it's not selfish.

> **mastablasta said:**
> that's not a propper bug report. note how it was marked as opinion in launchpad.
so you followed this: 
[https://help.ubuntu.com/community/SoundTroubleshooting/](https://help.ubuntu.com/community/SoundTroubleshooting/)
And this to find the right package: [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)
so you can make the bug report propperly.

edit:

also no need to write novels on bug report.
this should be enough with a good title and necessary logs and informaitons posted along with it. wll maybe you can add a bit but just informaiton you think it would help resolving the issue.
Agreed on the novel bit - but I was pretty lost - still am. Actually, much like my adventures trying to get the hard drives to spin down, the issue seems to be 4 bits of code written by different people, all trying to do the same thing - and to someone in the know, it would probably mean a lot. I work on much lower level stuff and quite a bit of mechanical items, and would appreciate someone offering to take pictures and measurements of something I designed, where it to fail.

I certainly did say in my post that I couldn't figure out the package - it's not that I can't read, it's that I was getting no useful feedback, and no one offered one word of help... And I've made several mentions of this here on the forums as well.


> **Jimmyfj said:**
> I'm not claiming to have knowledge about the problems you encounter. But since your problems just started after 10.04 my suggestion is that you add those repos from 10.04 that holds your sound drivers as I think that your new version of Ubuntu simply have dropped those drivers for what ever reason. So add the repos to your /etc/apt/sources.list and hunt the right driver down.

[QUOTE=Jimmyfj;12137031]As for your problem on restart. It seems that you for whatever reason no longer have the privileges needed to reboot the system. Check your rights and allow yourself to administer the computer (almost root privilege). I had the the same issue some versions ago but this tip made it go away.
The link I shared says just that - I guess it allows you to shut down the computer even if someone else is using it, which is odd, the "who" command, regardless of permissions I run it with, said I was the only person online.

I'm actually convinced there's something helpful here - I set up the machine in question such that I wouldn't have to type in my password when I sudo - and that's when the log-out issue started. It would most certainly be a good bug report to file, but why do I want to get ignored and yelled at again? Forget it.


That said, WOW I would love to get rid of that noise. I don't know a place to host a sound file, perhaps I need to make a video and youtube it, but it's pretty ridiculous.

---

### Post by mastablasta on 2012-07-30
> **AbeFM said:**
>  
Agreed on the novel bit - but I was pretty lost - still am.
 
I certainly did say in my post that I couldn't figure out the package - it's not that I can't read, it's that I was getting no useful feedback, and no one offered one word of help... 

Post relevant logs and all system specs on launchpad and try again. Describe the problem very shorty. And then wait. hopefully someone will pick it up and eithe provide a solution or check and fix the bug. or at leats tell you what is wrong. but you need ot give them a place to start. might also be good to report it to ALSA.
in the mean time if 10.04 worked go back to it. It is still supported until April 2013.
 
I am also having sound issues. 10.04 didn't work, 10.10 worked perfectly, 12.04 when installed worked perfectly and after 2 months and a fe updates to kernel later, sound has issues. it just stops working and wrong "sound card" (dummy output) is set as default. have been reading troubleshooting. in the end i used a workarround. still didn't have the time to report a bug to launchpad but will do so when i can. 
 
you could also try to use development version of ALSA PPA or try to use a different sound architecture instead. i believe there is some alternative to it but i am not sure.
 
Package is likely ALSA, gstreamer and/or similar. there aren't that many main packages thta deal with sound.
 
btw what happens if you switch to analog stero output?
 
> 
That said, WOW I would love to get rid of that noise. I don't know a place to host a sound file, perhaps I need to make a video and youtube it, but it's pretty ridiculous.
 
logs, not video....
 
 
> 
I'm actually convinced there's something helpful here - I set up the machine in question such that I wouldn't have to type in my password when I sudo - and that's when the log-out issue started. It would most certainly be a good bug report to file, but why do I want to get ignored and yelled at again? Forget it.

well you broke one of important security features of the OS. did you expect that all will work well afterwards? i doubt this is a bug since you changed an important feature on the OS that is ment to be there. and it is there for a reason.
 
IMO sudo is rarely needed once all things are installed. so disabling it in such a way is not necessary. especially if it's going to break the system.
 
there are other distributions that don't use Sudo at all. you might want to try those instead.

---

### Post by AbeFM on 2012-07-30
Thank you very much for a balanced and helpful post!

> **mastablasta said:**
> Post relevant logs and all system specs on launchpad and try again.
I'm not sure which logs are relevant - though I did find logs in that other guy's post. I'll admit, I've basically been "just dealing with it" for many, many months now - and I certainly don't remember the research I did then to try to fix it. Guess I'll have to read the other thread again on how to log what.

> **mastablasta said:**
> 
I am also having sound issues..... it just stops working and wrong "sound card" (dummy output) is set as default. have been reading troubleshooting. in the end i used a workarround.
I'd love to find a work around. I guess the more I hear it happening to others, the more I think it needs wider attention so it can be fixed. If it'd only happened after I monkeyed with SUDO, hey, it's my fault, and my problem.


> **mastablasta said:**
> 
 you could also try to use development version of ALSA PPA or try to use a different sound architecture instead. i believe there is some alternative to it but i am not sure.

Huh, think that's something I can choose out of the repository? Certainly worth a shot. Years ago, on another machine under 9.x, I had the exact same issues under Wine. Changing sound drivers under wine worked, but when next everything was upgraded, all that went away. Does seem to be an ALSA issue - but it's that I don't know enough to know what to tell people.


> **mastablasta said:**
> 
Package is likely ALSA, gstreamer and/or similar. there aren't that many main packages thta deal with sound.
 
btw what happens if you switch to analog stero output?

ALSA seems a reasonable guess to me. I just don't have a feeling for how much there is so it's hard for me to guess.


> **mastablasta said:**
>  
logs, not video....

Logs of what? The video is someone else's - but mainly, I'm having trouble describing the quality of the sound. I am trying to avoid fifty people telling me to clean the contacts on the cable. I'm not sure it would show in the log, and really don't know which one to make.


> **mastablasta said:**
>  
well you broke one of important security features of the OS. did you expect that all will work well afterwards? i doubt this is a bug since you changed an important feature on the OS that is ment to be there. and it is there for a reason.
 
IMO sudo is rarely needed once all things are installed. so disabling it in such a way is not necessary. especially if it's going to break the system.

At minimum, I need it every time I install software. And sharing stuff on the network, copying, mounting, editing system files. I'd LOVE to have some one-click-way to give myself permissions on a case by case basis (modifier key?), but I've not found one.

And no, I didn't expect everything would work well - though I was hoping it, and I'm quite happy with the machine since I did it. I can now do things on the fly.

[INDENT]
Total aside:
> **mastablasta said:**
>  
there are other distributions that don't use Sudo at all. you might want to try those instead.
Huh. That's interesting. Sure, I'd be open to it. The biggest issue I have with ubuntu is this "we're hiding the guts from you, but you still need to know they are there". Setting up a RAID? I have to install a bunch of junk, and set it up - and it's hidden ("technical items" under the package manager). If I know enough to fix something, why can't I use the GUI to do this? There's WAY to much typing for things which don't need it, IMO. What would I LIKE? Hold down control and it runs stuff with SU privileges. Since I can't do that, I end up making icons for command line stuff, and gksudoing that.

The best part is when you click on something that comes with a fresh, clean install of the OS and then it doesn't work since you don't have permission. I am glad those features are there, but something to make it more livable would be fun. sudo Nautilus is rapidly becoming one of my favorite commands.

Anyway - didn't want to break it, just wanted to be able to use my PC as a PC, not as a PC plus a memory challenge puzzle I have to complete for 2/3 of the daily activities. A secure way to use the computer with only a mouse would be amazing. Windows does it (not sure how secure it is) [/INDENT]

Again, thanks for a sane, human reply.

---

### Post by mastablasta on 2012-07-31
> **AbeFM said:**
> Thank you very much for a balanced and helpful post!
 
 
I'm not sure which logs are relevant - though I did find logs in that other guy's post. I'll admit, I've basically been "just dealing with it" for many, many months now - and I certainly don't remember the research I did then to try to fix it. Guess I'll have to read the other thread again on how to log what.
 

here is just one example of sound bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/884210](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/884210)
 
check dmesg first to see if there are any errors on system boot.
 
>  
Huh, think that's something I can choose out of the repository? 
 
 
PPA is personal package archive. it's a mini personal repository. for example testing version for sound: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)
 
 
>  
ALSA seems a reasonable guess to me. I just don't have a feeling for how much there is so it's hard for me to guess.

ALSA is the sound architecture (basically sound drivers bundle for linux) 
 
>  
I'm having trouble describing the quality of the sound. 
 
 
it's enough if oyu say that sound is of very poor quality and sounds like static (squeking or whatever). 
 
 
>  
At minimum, I need it every time I install software. And sharing stuff on the network, copying, mounting, editing system files. I'd LOVE to have some one-click-way to give myself permissions on a case by case basis (modifier key?), but I've not found one.

 
you can arrange auto mount.
sudo or rather password is ment so that if you get malware it can not run itself without "typing" in your password. since it doens't know the password it won't run. it's same in windows only there malware doesn't really need to know the admin password to run itself if you run as admin all the time. the result are various botnets, stolen personal data, stolen credit card data etc.
 
 
>  
sudo Nautilus is rapidly becoming one of my favorite commands.
 
 
i hope you ment gksudo nautilus here. sudo nautilus will get you in trouble. 
more on this here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
 
an better and cleaner option would be to increase sudo time out: [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)
 
> If you specify 0 you will always be asked the password. If you specify a negative value, the timeout will never expire. E.g. Defaults env_reset,timestamp_timeout=5 

---

