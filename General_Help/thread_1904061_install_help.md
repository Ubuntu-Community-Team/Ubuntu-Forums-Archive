---
title: "install help"
date: 2012-01-03
forum: General Help
---

### Post by buku2 on 2012-01-03
radeon graphics card popped put in a georce x5200 128bit agp when i tried to start it bios comes up then i lose signal to my tv tried to reinstall atfer i select install i lose signal again went through my stack of distro disk finally got fedora 15 installed but due to graphics card issues gnome 3 could not be initiated i need my mythbuntu back on my  desktop whats wrong please help me

---

### Post by topsites on 2012-01-04
One thing at a time.

When you say the Radeon popped, do you mean it stopped working, or do you mean you removed / "popped" it out?
Please, be specific, I don't understand this popping.

Assuming you meant that it stopped working...
Do you have any way, such as a spare computer, with which to test the monitor?
Because I am starting to wonder if it isn't the monitor that's malfunctioning.
Once we have eliminated the monitor as a possible source of the malfunction, we can proceed.

---

### Post by buku2 on 2012-01-04
the card made a pop sound and quit working after that the moniter is actually a 36inch samsung tv hooked through s-video, i do have a test monitor a 27inch lcd samsung monitor everything works fine on it

---

### Post by buku2 on 2012-01-04
i have built a few desktops for family and friends ill slap them together install a linux distro usually zorin or ubuntu ive tried this card several times always have the same issue even when i hook it up using my lcd monitor instead of my tv i click the "install to hard disk" and the other installation options dont work either i lose signal if use factory monitor out works fine no loss of signal but i need the s-video on my card for my old hdtv which has no monitor in no dvi and only one hdmi port
 sorry never good and explaining stuff i always get everything jumbled so if you can find the patince to work with i will be enternally gratefull

---

### Post by Buntumatic on 2012-01-04
You are right about one thing, you are hard to understand.

You are losing display when TV is attached?
This is due Xorg server not getting correct EDID reading and using resolutions not supported by your TV. Have you tried changing resolution using Ctrl+Alt+Minus ? I'm not sure if this is enabled in Ubuntu by default, though.
You could use Ctrl+Alt+Fn to switch to console and set up your Xorg server from CLI.

Your Radeon probably has one or more exploded capacitors, it happens when fan gets stuck and the details overheat. In most cases it can be fixed by greasing the fan and replacing capacitors.

---

### Post by buku2 on 2012-01-04
hay man, thnaks for the help, i used my pc monitor downloaded everything  nvidia and then workedd my way through it all till i got it so thank you very much, and thanks to everyone else who replies to rambling idiots like me, evreyones ones post in the other forums and many other linux forums, you all are genusis at what you do keep up the good work and remember buku2 is eternally gratefull especially to buntumatic

---

### Post by Buntumatic on 2012-01-04
You are welcome, glad you got it sorted. :D

---

