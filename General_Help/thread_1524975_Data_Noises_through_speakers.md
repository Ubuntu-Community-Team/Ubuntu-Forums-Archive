---
title: "Data Noises through speakers"
date: 2010-07-06
forum: General Help
---

### Post by timfinley on 2010-07-06
Hey. I am getting what I am calling data noises through my speakers. I imagine it has something to do with maybe my onboard sound card. But I feel like there should be a way to filter it out. I am using Ubuntu 10.04 but it has been this way since I started using ubuntu many years ago. It always bugged me so i thought i would go ahead and see if there is some kind of fix for it. any help would be appreciated.

---

### Post by Yarui on 2010-07-06
Could you maybe describe what you are hearing and when?

---

### Post by ScarletWyvern on 2010-07-06
It kind of sounds like it might be cellphone interference.

---

### Post by Yarui on 2010-07-06
Oh, does it sound kind of like a series of short buzzing noises that lasts for a few seconds and then stops?  If so that probably is from some form of interference, and if that's the case you can't really do anything to fix that.  If it is coming from your cell phone then you would just have to try to keep your cell phone away from the speakers if you are bothered by it.

---

### Post by timfinley on 2010-07-06
No it isn't cell phone interference. I know what that sounds like. It is a constant ticking sound. kind of quite. no matter what level I put the speakers or the system volume the sound stays the same. If I am doing anything cpu or ram heavy, like converting a file or burning a cd, the ticking speeds up and sound more like a buzzing. when it was really bad before I would move the mouse and it was almost like the mouse had it's own sound effect. It gets really annoying when i am trying to watch a movie or listen to music at low levels because you can hear the ticking sound over the music. some times it goes away, but i can never figure out why so I can repeat the solution. very puzzling. 

It is not cell phone interference. While that does happen when my phone rings I am not worried about it.

---

### Post by Yarui on 2010-07-06
Are you sure it is coming from the speakers?  I think I know what kind of noise you are referring to and in my experience that noise most frequently comes from inside the computer, from hard drives, I believe.  If you turn off your speakers does the noise go away, or is it still there?

---

### Post by timfinley on 2010-07-06
Jesus dude, i'm not an idiot. The sound is coming from the speakers.

---

### Post by kieran_uk on 2010-07-06
Hey calm down man, he just trying to help!! :/

Regards, Kieran..

---

### Post by QLee on 2010-07-06
timfinley,

Sometimes stray noises can be fixed by muting the mic input to a sound card, even when there is no microphone connected. Worth a try if nothing else works.
 
If it is a desktop, make sure no cables carrying a signal run close to the soundcard chip which might induce a noise. 

From your description it doesn't sound like a hum which might be induced by bad filters in the power supply.

Doesn't sound like a good thing to have, it must be frustrating.

---

### Post by Yarui on 2010-07-06
> **timfinley said:**
> Jesus dude, i'm not an idiot. The sound is coming from the speakers.
I don't think you are an idiot even if that was the case.  It is easy to overlook something obvious and sometimes it's better to ask those kinds of questions before you spend days trying to troubleshoot the wrong problem.

I'm out of ideas as to what could cause it.  I don't know a ton about ALSA.  There are only two things I can think to suggest at this point.  One is to make sure your speaker plug is making good contact with the socket on your motherboard and that it is plugged into the right socket.  The other is to try using an ALSA alternative like OSS.

Some computers have strange issues with ALSA that can't really be fixed and if you happen to be one of those people, you may want to try out OSS.  For quite some time OSS has been considered a little bit deprecated, I think, but supposedly it is starting to catch back up with ALSA.

---

### Post by Yarui on 2010-07-06
> **QLee said:**
> If it is a desktop, make sure no cables carrying a signal run close to the soundcard chip which might induce a noise. 
Come to think of it, this could be your problem.  I have seen this problem before when a mouse cable was too close to a speaker cable.  The mouse signals can cause some interference with your speakers, and that could be why you are hearing more interference when you move your mouse.  It's definitely worth a try, and a preferable solution to switching drivers, which wouldn't even work if this were the issue.

---

### Post by cascade9 on 2010-07-06
> **Yarui said:**
> Come to think of it, this could be your problem.  I have seen this problem before when a mouse cable was too close to a speaker cable.  The mouse signals can cause some interference with your speakers, and that could be why you are hearing more interference when you move your mouse.

1st I've heard of a mouse doing that, but you learn something new everyday.... 

BTW, its possible that enabling 'spread spectrum' in the BIOS will help. 

[http://en.wikipedia.org/wiki/Spread_spectrum](http://en.wikipedia.org/wiki/Spread_spectrum)

[http://www.rojakpot.com/showFreeBOG.aspx?lang=0&bogno=266](http://www.rojakpot.com/showFreeBOG.aspx?lang=0&bogno=266)

---

### Post by timfinley on 2010-07-06
Hmm Sounds like maybe a rearrangement and maybe some more digging into this problem a little more. I mmoved the speaker away from the screen and it made the ticking quieter, so it might be that. I might try moving the speaker off the desk completely.  Sorry about that "idiot" remark.

---

### Post by Yarui on 2010-07-06
> **timfinley said:**
> Hmm Sounds like maybe a rearrangement and maybe some more digging into this problem a little more. I mmoved the speaker away from the screen and it made the ticking quieter, so it might be that. I might try moving the speaker off the desk completely.  Sorry about that "idiot" remark.
No problem, I know where you are coming from.  I'm sure we have all reacted that way to something at one time or another, especially when frustrated while trying to troubleshoot something.  Hopefully reorganizing your cables will totally fix the problem.

---

### Post by jonobr on 2010-07-06
Mmm... Interesting thread, and just as an aside, 
I used to listen to a lot of radio during quite periods in work while I would be working on documents or other stuff.
I used to do my documentation on a windows box.

I had a wired mouse, and noticed that when the volume was loud enough I used to hear pretty much the same thing, you would hear what I would call "blippy" noises,
I would just turn down the volume to get rid of it.
I only say this as I dont think its uniquely ubuntu

Cheers

PS, Im not sure blippy is a real word but it sounded accurate!

---

### Post by Yarui on 2010-07-06
> **jonobr said:**
> I had a wired mouse, and noticed that when the volume was loud enough I used to hear pretty much the same thing, you would hear what I would call "blippy" noises,
I would just turn down the volume to get rid of it.
I only say this as I dont think its uniquely ubuntu
Yeah, it's definitely not unique to Ubuntu.  This is caused by the lack of shielding on the cables.  Pretty much any cable that carries information emits enough of an electromagnetic signal to interfere with other such cables.  This is the reason that network cables are twisted in pairs, it is meant to reduce this radiation.  It is also the reason many cables have a layer of metal mesh and/or foil.  Using such methods to shield cables isn't always practical, though, so speakers and computer input devices don't generally have any kind of shielding.

---

