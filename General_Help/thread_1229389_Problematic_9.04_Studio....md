---
title: "Problematic 9.04 Studio..."
date: 2009-08-02
forum: General Help
---

### Post by pianoman91210 on 2009-08-02
[COLOR=DarkRed][SIZE=3][FONT=Comic Sans MS]Ok, so recently I installed Ubuntu Studio 9.04 (Jaunty Jackalope) on my computer, and I have come to see a lot of problematic bugs, or at least what it seems like. Now I know I'm no expert when it comes to Linux, but I learned a lot about Ubuntu 9.04 just reading some articles and etc., and here is what I gathered.

As I see, Ubuntu 9.04 is said to support a realtime kernel, which I heard was also very problematic thing, not intentionally of course. But to go beyond that, installation was a breeze, and everything was great - so it seemed - until the big problem : Freezing. I discovered that every time I would try to use some kind of internet application, regardless wether it was Synaptic Package Manager or Firefox, the screen would freeze up and then the mouse, and before you know it, Ubuntu had put on its "crashy pants" and forced me to my last resort - to restart the system.

Now I had read this article here: 
[http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904](http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904)
(by the way, kudos to Dave Phillips who wrote it) and I seemed to have the same stream of problems as he did, and coincedentally in the same timeline, if you will. First thing I noticed was my nVidia splash screen didn't show up, and I learned how to use terminal as my friend reading this article too. But I was in luck and changed the realtime kernel flags posted in this article and (like Dave said) voila! It stopped freezing and crashing, and so far, I've worked a way around JACK and its setup and connections to work without having to fix the Pulseaudio problem - though I do still have a problem...and I have a feeling its not just my computer.

Recently, I installed a realtime effects processor known as Rakarrack, v0.3.0 via a .deb package I found, and it installed correctly and everything was fine - untill JACK decided to freak out again, and the uprising of the "Freezing" matter came back to me yet again. Now (what my guess is) since the computer is what appears to be running on only one Dual Core Processor on my PC, the graphic display is very sluggish and it takes a century and a half to load JACK. When it finally does, here comes "crashy pants" again and freezes the computer. Now it freaks with Ardour and any other program that has to run with JACK, forcing me to restart the system. I'm in a whirl of trouble, knowing that I DON'T know what the problem is, but I could really use some feedback about 9.04 and its so-called "crashy pants". I have this distribution for the DAWs and the Video/graphics editing programs, but no sense in getting it if I can't even run them, and it seems to be a fixable problem. I know I'm not alone in these stream of problems (with all my research) so I could really use the help!! What am I in for, what am I missing and what's going on with Ubuntu Studio!?? :confused: :confused:
[/FONT][/SIZE][/COLOR]

---

