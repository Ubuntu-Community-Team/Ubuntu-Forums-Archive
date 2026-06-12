---
title: "sound sometimes stops working, but only for programs on an external monitor (laptop)"
date: 2012-03-30
forum: General Help
---

### Post by sbellerby12 on 2012-03-30
Hi all,

I'm using Ubuntu Lucid (though not all of your typical Ubuntu-default stuff is on here, I did a minimal install and added what I felt I actually cared for on top of that without grabbing all of the GNOME packages or all of the Ubuntu artwork or what have you) on an Inspiron E1505/6400.

Because the graphics card is an ATI Mobility Radeon X1400 which was causing issues with using external displays (which I needed to have working for things like presentations, but am also totally using with a little converter thingy to watch stuff on my television) I installed the backported 3.0.x (it currently thinks it's 3.0.0.17 I think) kernel. Before, the external displays would be all wobbly; now, they're not.

The thing is though, any time I open something I need to have it appear on the main display for the sound to work. When I don't have an external display enabled I don't have (or at least haven't had as of yet) sound issues, but when I do have a second display and move things onto it sound starts getting iffy. By that I mean if I move it there it will continue to work, but if I pause it for whatever reason then unpause it, it won't work until I close down the entire application and reopen it.

This has mainly been a problem with watching videos. If I go fullscreen in something like Flash that forces it to the leftmost display, and the external display is leftmost (so the place with the source for the Flash plugin is on the main display still) then it doesn't give me issues (well, hasn't yet anyway) but if it's a locally stored file then regardless of where the external monitor is placed pixel-coordinate-wise it has this issue.

I initially figured that perhaps it was simply an issue that would be fixed by getting backported ALSA modules just like the backported kernel, but as of yet I have not found any sort of packages or PPAs or anything for this, the best I can find calls itself a backport but is still for a kernel in the 2.6.x line, which is no longer what I am using.

Is anyone familiar with a problem that sounds like this (pun unintended) or anything similar enough to have any thoughts on the matter.

To hopefully preemptively answer a couple questions or otherwise clarify some points:

[LIST]
[*]The primary display is just directly connected to the card using I-don't-know-what because it's a laptop display. The secondary display is connected via VGA.
[*]The audio could be from my laptop speakers, or I can connect those to external speakers of a few different forms too, it doesn't really matter because all of them have issues.
[*]The one time I tried having both screens be the same it didn't have this issue, but since closing the lid puts both displays to sleep and having the same thing on two displays does funny things to my eyes after a while I would prefer not using this approach, plus counterintuitively the Television seems to like 640×480 better than 1024×768 anyway, and I haven't figured out how to have them overlap with different resolutions (though I'd imagine that ARandR or whatever it was called could do that, but then fullscreen on the smaller-resolution screen would be tricky anyway)
[*]The audio device calls itself "N10/ICH 7 Family High Definition Audio Controller" in the output of lshw, made by Intel.
[*]Again, the graphics would be ATI Mobility Radeon X1400 (128MB RAM, if there are multiple models for different laptop models it's the one for the Inspiron E1505/6400)
[*]I'm using a backported kernel 3.0.0.17 to fix the external monitor issue.
[*]If any other information sounds useful I'll be glad to go try to find it (might need help finding it depending on whether I ever noticed it before you ask though, so some potential I might require instructions to find it).
[/LIST]
Hopefully my setup isn't so far and away from the ordinary as to keep this from being solved. I've almost got everything worked out this week transitioning from Karmic (yes, I know, so very thoroughly dead is Karmic by now) and this is one of like two things left that are still bugging me any.

---

### Post by imachavel on 2012-03-30
the screen resolution will have absolutely nothing to do with a sound error. That is a back end error. Some .conf file for gnome audio or whatever Ubuntu uses for audio now has malfunctioned with some very deep back end code. This error is so weird, I wouldn't even know what to explain to you. Very sorry I don't know what to explain to you, but the monitor is simply streaming in video data bits. It has NADA to do with the sound working, the drivers are completely separate.

You wrote such a well informed post and well researched post, I wish I could answer your question better. Anyway what can I do? That is such a weird error. Sounds like an IRQ error. But I can't explain what any of this. Doesn't make sense. I'd google around for a dual monitor configured .conf file, this is probably what is responsible for the sound not working in a program in an external monitor. What is strange to me is, if your main monitor is off, you can still hear the sound. If your sound is off, your monitor will display things. I can't figure out how the bios can mess this up, wtf linux developers? I thought you guys made an OS that DIDN'T break like windows. Thanks Linus :lolflag:

Btw, 128 mb of video ram should make no difference to your configuration. 16 MB of ram is enough to run most video programs using the current video api(if it's windows, probably a directx version, or Opengl for Ubuntu)
Now if you are running videos or games, then yeah it might make a difference, 128 mb video ram might bottle neck while caching for dual display. Aside from that, simple things use much much less video memory. May I ask what programs you use in the other display often?

---

### Post by sbellerby12 on 2012-03-30
Well, okay, it's certainly not a bad feeling to start off finding I'm not the only one who can't make too much sense of what exactly is going on and put it in words.

I think I may have mis-explained the trouble slightly, or at least the setup in which the trouble occurs. I don't actually have the main monitor off to get the sound to consistently work but rather set up both displays to have exactly the same thing (so typically if I don't do anything but click on the mirror display checkbox, both the laptop and television/external/whatever I've hooked it up to this time will have 1024×768, and anything on one screen will be on the other) so technically, while on the second display, things are on the first display as well.

On the other hand, if the two displays are separate (i.e. NOT displaying the same thing) then the external one will have this inconsistent sound issue. It's not a complete lack of sound unfortunately, as that would probably be easier to trace to something, but rather that sound will not work if it tries to start from something displaying on the external display. If I drag something over there after it opens on the laptop display it will usually continue to work, but if I pause it then I'm out of luck.

The program in question that is consistently doing this (it's the one I've been using enough to notice the problem) is VLC. Again, if I have a browser on the laptop display and arrange the displays relative to each other such that the external gets fullscreen, that does not seem to cause this audio issue, or at least hasn't so far.

Thank you for the quick reply, hopefully this leads somewhere.

(Also, I'm sure Windows was just listed as an example, but to be clear I am NOT dual-booting)

---

### Post by sbellerby12 on 2012-03-30
Well, I just ran into this <sarcasm>awesome</sarcasm> detail:
Apparently the problem has spread to my main monitor. It occurred to me that I hadn't tried using it in the last couple of days (this installation is literally like a week old, and this problem didn't initially exist right after I got the external display working) and so I went to try that again. When I did so, I found that apparently this problem is in fact system wide. So, to sum up...

Good news:
This problem is now almost certainly only tied to the audio, the video thing had been thought to be an issue before because it seemed to only be on external displays. This is no longer likely to be the case as it can happen on any display.

Bad news:
Ugh, that means somewhere I must've done something to my audio (or maybe it was the kernel upgrade and I was just lucky the first couple times... oh the joys of inconsistent computer failures) and now there's more searching to be done to see if anything similar to sound just *generally* not working after pausing and resuming pops up.

(sorry, as I mentioned install is just a week old, didn't have this issue a couple days ago but I've been fine-tuning the machine much of this whole time so yeah...)

---

### Post by sbellerby12 on 2012-04-03
Well I guess now I need to figure out how to mark this as solved...

Apparently what changed between when I had initially started and when I ran into this problem was that I installed something that pulled in PulseAudio without me noticing. I'd noticed this mentioned in other threads before, but as I mentioned initially my particular install of Ubuntu is kind of built from the command line, and as I had put in most everything manually (very few packages were used to pull in other packages, it's meant to be very minimal GNOME so I can dedicate system resources to other things) and as I had not personally specified PulseAudio I did not realize I even had it.

Based on the list of things that try to remove themselves when I pretend to remove it, I think it may have been pulled in by a small handful of KDE apps I installed. Anyway, how it got there is not so relevant as the fact that it seems to gladly force itself into the system without one necessarily selecting it. Fetching pulse plugins for my media players seems to have resolved the issue.

I guess I'm going to look for a thread solved thing. Lesson learned I suppose: PulseAudio pulls itself in with KDE stuff, even if you've turned off recommended and suggested packages to only get the absolute minimum of dependencies...

(hopefully this proves helpful to someone who also thinks they don't have it from a comparable setup... man, feels really awkward to just find it's something that other posts mentioned like this, I just *really* did not think I'd installed it)

---

### Post by BodssmoofeBit on 2012-04-03
Hi  Perhaps the forums are some sailors.  What is the best boat for the novice sailor?  Thank you in advance for all answers.

---

### Post by raja.genupula on 2012-04-03
> **BodssmoofeBit said:**
> Hi  Perhaps the forums are some sailors.  What is the best boat for the novice sailor?  Thank you in advance for all answers.
hey , give us more information on what you wanna do . we can help you in a better way .

---

