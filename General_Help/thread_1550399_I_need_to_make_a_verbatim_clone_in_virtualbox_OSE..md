---
title: "I need to make a verbatim clone in virtualbox OSE..."
date: 2010-08-11
forum: General Help
---

### Post by rainbowagent7 on 2010-08-11
Hi all. I am running Lucid and just installed Virtualbox OSE with lucid on it as well so I can test changes before I apply them to my host system. Everything went great with the install, but I need something that I can use to make the virtual machine a verbatim (bit for bit) exact replica of my main system. I tried Grsync a while back with my old computer to synchronize two hard drives, but ultimately wound up pulling most of my hair out and going office space on it. Okay, that's stretching the truth, but it was very frustrating. I only have one hard drive now and just need a utility to make periodic synchronizations between the main system and the .VirtualBox folder in my home directory, can anyone point me in the right direction???

---

### Post by betlog on 2010-08-11
clonezilla worked for me..
it copies the base install though, not any snapshots

---

### Post by rainbowagent7 on 2010-08-11
Thanks for the speedy reply, although I'm not sure what you meant. I do know that I need something that can copy EVERYTHING because if I'm going to be tinkering around in the virtualbox I need all of the same factors to be present that are on my main system, or else what's the point? Thanks again for your reply:-]

---

### Post by rainbowagent7 on 2010-08-12
I think I may try the Grsync again being as how I don't have to jump across two different hard drives now, unless someone knows of a better program or method, wink wink nudge nudge... anyone?... anyone?
=D>:guitar::-({|=:-\"

---

### Post by howefield on 2010-08-12
> **rainbowagent7 said:**
> but I need something that I can use to make the virtual machine a verbatim (bit for bit) exact replica of my main system.

Thing is, you aren't going to get that, are you ?

Running a virtual machine isn't the exact (bit by bit) same as running on the "bare metal".

You'll be using different drivers on host/guest for a start.

---

### Post by rainbowagent7 on 2010-08-12
That's good to know and it makes sense. I'm still fairly new to Linux so I always ask before making a big step like this. Thanks for replying, I guess I'll just replicate as much as possible and go from there. Peace. 
Oh yeah, I'll slap a solved sign on this one.

---

