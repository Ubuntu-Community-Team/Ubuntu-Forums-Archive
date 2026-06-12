---
title: "Problems with the &quot;Second Life&quot; game"
date: 2010-05-28
forum: General Help
---

### Post by ensleepent on 2010-05-28
My mom has finally gotten tired of the atrocious Windows Vista and all its issues, and decided to start  singing the Ubuntune with the rest of us "cool" people.  And it's great.

But there seems to be one little problem:  Her favorite PC game, "Second Life," isn't working right.  And the fact that a Linux version of this game is available played a large part in convincing her to switch over.

She has a Toshiba PSAFGU-055002 laptop with an ATI x1200.  Upon launching Second Life, we get a message warning us that the machine has less than the game's system requirements.  And the graphics are all garbled.

So I looked on Second Life's webpage for the system requirements, and it says that this kind of graphics card is untested and therefore may not be compatible.  This game was previously running fine on this machine, with Windows  Vista, so I'm not sure what to think.

I, for one, am not very familiar with modern PC games (I'm mostly a retrogamer), so I don't know anything about these "viewers" that Second Life requires in order to run.  There are apparently many of them.  Could this be the problem?  A different viewer is needed?  I've tried a couple, with similar results, but I don't know.

Is the computer just not powerful enough?  I find it strange that it works with Windows Vista, but not Lucid Lynx.  It's the same machine, why should this make a big difference?  Is there something I don't know?

I have the feeling that this might just be some minor wrinkle that's easy to work around...  if you know how.  But I have yet to find anything on the web -- let alone in this forum -- that addresses this particular issue, so I thought I'd ask.

I have no idea what other hardware information to provide that might be relevant, so feel free to ask.

---

### Post by Ozymandias_117 on 2010-05-28
Do you have the 32-bit Ubuntu or the 64-bit Ubuntu? (If you aren't sure, type in a terminal ```
uname -m
```)

---

### Post by ensleepent on 2010-05-28
Oh, it's the 32-bit version.  I should've mentioned that already.

I actually tried the 64-bit version first, but had problems with it right away (Adobe Flash Player).  The 32-bit one worked fine, so I went with that one.

Perhaps I could try downgrading to Hardy Heron or something.  But I'll try to get  Second Life working on 10.04 first.  :)

---

### Post by hreichgott on 2010-05-28
Hi, I use Second Life on Ubuntu, with the official Linux viewer.

Second Life is a very graphics-heavy program and it really does require a graphics card that can handle everything.  That said, you can still run Second Life with some graphics cards that aren't on the list.
Did it run with the same hardware on Windows?  if it did, it should also work in Ubuntu.

Things you can try--
- Turn off SLVoice and force Second Life not to use PulseAudio.  See this thread on the Second Life forums for more info.
[http://blogs.secondlife.com/message/96916](http://blogs.secondlife.com/message/96916)
(the thread is about a crash problem with an older SL viewer, but I found that once I simplified the sound, everything especially graphics worked better, since the computer had more resources available)
- Try different viewers... older viewers have more generous system requirements.  Check for older Linux viewers (on the official website) that have version numbers starting with 1.
- Go into the Preferences window and set all the graphics settings to the absolute minimum.  (minimum draw distance etc.)

Good luck,
Heather (aka Miriam Forsythe on Second Life)

---

### Post by ensleepent on 2010-05-28
Well, thanks for the advice, but unfortunately none of those things helped.  :(
 
The problem doesn't seem to be "lack of power" so much as "inability to draw graphics correctly."  It's hard to describe, but everything looks wonky, sometimes you can see through stuff you normally can't, sometimes you can't see through stuff you normally can, and the whole image just looks like it isn't done being drawn, like it's a prototype or something.  And there aren't many colors either.  It sort of looks like a photographic negative in some ways.
 
At any rate, it renders the game practically unplayable, although everything else seems to work fine.  It's just hard to see what's going on.
 
And it gives me that message upon launch telling me that I don't meet the system requirements.  This same game ran fine on this same machine when it was running Windows Vista.  And not exactly with minimal performance settings, either.
 
I just don't get it.  The differences between operating systems running the same game on the same hardware can't possibly be *this* extreme.  There must be *something* I can do for at least a little improvement.
 
Why does the OS matter, anyway?  Don't they ever write software in plain ol' machine language anymore?  Why does everything have to go through the OS these days?  Especially games.  Games are resource hogs, and you generally aren't busy with a bunch of other programs when you're playing them.  Games would love to have the OS go away and free up system resources when they're running.
 
Well, enough of my ranting.  :)  I just feel like there's some little system setting or file I need to tweak, or some other software rubbing Second Life the wrong way, or some little thing like that.  Problems like these with games are often like that.  Like there's just some magic button to press that fixes everything...  if you know which one it is.

---

### Post by hreichgott on 2010-05-28
Weird.  So it will run, but has bizarre graphics.

I fear we may be beyond what I can help with, but would you kindly post a screenshot of the weirdness, so other people can see it and possibly help?

Good luck
Heather/Miriam

PS You may have better luck on the Second Life forums, actually--they have a dedicated Linux area.

---

