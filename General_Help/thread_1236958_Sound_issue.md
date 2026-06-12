---
title: "Sound issue"
date: 2009-08-10
forum: General Help
---

### Post by MiamiDolphins13 on 2009-08-10
Hey guys, new to the forums, and still pretty new to ubuntu.:KS

Anywho, down to buisness..

Something very strange happend to me, after upgrading to 9.04
i have no sound!

i have searched and searched for solutions, but i just dont understand what to do!

I make it as far as terminal, and when i enter something in, it asks for my password.
which at that point it wont let me type in my password, or anything for that matter.

I just dont know what else to do!

Please help!

I dont even hear my intro sound when re-booting the pc.

---

### Post by jerrrys on 2009-08-10
you do realize that when you type your password in terminal it will not give you any visual display.

and as far as no sound.  i run 804 so i can't help, but can point you here

[http://www.google.com/search?q=no+sound+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=no+sound+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by MiamiDolphins13 on 2009-08-10
something very weird just happend...my sound came back for about 5 minutes? i typed something in like sudo killall pulseaudio, sound came on, restarted my comp.

sound worked fine for first few minutes, now back to hearing nothing!

---

### Post by jerrrys on 2009-08-10
careful how you use sudo it can do damage if not use right.  

so you killed pulse and it worked.  i do not use pulse, but i know it will reinstall itself which is probably what happen to you. i would suggest to google **kill pulseaudio ubuntu **for informationand if you don't get a good answer post back and i will help further[B]...
[/B]

---

### Post by MiamiDolphins13 on 2009-08-10
hey jerry appreciate the help.

but yeah didnt really find anything good searching there...
here ill show ya pretty much what i have done so far...

> 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[/LIST]


i use those commands, then i started to get a weird scratching/beeps from my speakers, which has been the first sound in 3 days coming out of them, so i thought i made progress, rebooted the computer, and my sound worked like i said.

then after a few minutes of that reboot, my sound, mid listening to a song, just drops out and doesnt come back.

i was messing around abit aswell with that sudo apt, tried to re-do those things again, and this time no progress.

i was  using > [http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)
for help, but im kinda lost now that it didnt really help!

i just find it very weird that i got my sound back, only to lose it without doing anything:confused::confused::confused:

---

### Post by MiamiDolphins13 on 2009-08-10
i wouldnt even mind going back to an older version of ubuntu, im just nervous that wouldnt even give me sound either!

i really have no idea how this happend... before i went to bed thursday night, my sound was working perfectly as normal, left the computer on all night(my comptuer is on pretty much all the time) woke up and the sound was gone, and havnt really messed with a fix until tonight, just due to the fact not much time to dedicate to it.

but now im determined to fix it, even if im still new at ubunutu.

---

### Post by MiamiDolphins13 on 2009-08-10
alright jerry! you may think im crazy, but randomlly without doing anything just browsing these forums, my pidgin messenger made the beep of having sound, it actually scared the crap out of me because i have my speakers almost all the way up. now my sound works..i really dont understand this. i did not do anything this reboot.

edit : > i dont want to keep posting new, so i might as well edit this one, my sound works then goes away, works then goes away. this randomness is really making me mad, but its better then no sound at all, im starting to go crazy over here!

---

### Post by jerrrys on 2009-08-10
first off, this fix your using is questionable at best. untested on 904 and most of all 804 does not have this kind of sound problem since 804 default it ALSA.

you say that you wouldn't mind using and older version, 804LTS would probably work out of the box.

another thing, have you installed **ubuntu restricted extras**?

---

### Post by MiamiDolphins13 on 2009-08-10
no i have not, never actually heard of that either.

how would i go about doing so?

and also, what would the best way to get that 8.04 downloaded and installed?

---

### Post by jerrrys on 2009-08-10
system>administration>synaptic package manager and then check ubuntu restricted extras

just download and burn a cd, i assume this is how you got 904...how did you get 904???

---

### Post by MiamiDolphins13 on 2009-08-10
i got 904 by jusing doing normal system updates. after updating, at the top it said upgrade to 9.04 jaunty, so i downloaded and it install automatically.

no disc burning needed to get it

---

### Post by jerrrys on 2009-08-10
ok...was 810 working for you? probably not since restricted extras were not installed and how did you get 810??

---

### Post by MiamiDolphins13 on 2009-08-11
back around january, my windows OS got a nasty virus so my friend install ubuntu on it through a disc. 

8.10 was working fine for me, probably should have read up on 9.04 before installing it. i see that there are lot of people with sound related issues :(

---

### Post by jerrrys on 2009-08-11
yes, a lot of issues out there.  can you get your friend to reinstall 810?

EDIT

thinking about this, 904 is not in that bad of shape on your box.  shall we just go ahead and fix the sound?

---

### Post by MiamiDolphins13 on 2009-08-11
definately like that idea!

lets get this working! :guitar:

---

### Post by jerrrys on 2009-08-11
ok, but its pass 2am and im fried.  so if you can, lets get together this evening.  and who knows, maybe someone else will step in and help by then.  also please to post your computer model and specifications and is this 9.04 32 bit or 64 bit.  goodnight miami...

---

