---
title: "Minecraft"
date: 2011-10-24
forum: General Help
---

### Post by Jaybyrrd on 2011-10-24
Perhaps this belongs in the gaming and leisure portion of this forum, however I think this may be a Java related issue. Simply put the game works very sketchily on my distribution, I am using Oneiric Ocelot, and it worked very sketchily on my Natty Narwhal distribution as well, I just didn't feel like digging into the issue as much becuase I was COMPLETELY new to Ubuntu then and gave up. Now I feel more ready and confident to even try fixing this issue. My system specs in terms of RAM, Processor, and Video Card are
 
4 GB Kingsten DDR2 Ram
AMD Phenom II AM2+ Quad Core Processor
EVGA 9800 GTX+
 
When running Minecraft all four processors run at 100% and the game has low performance. Easily an instant cue into there being an issue. The reason I posted it here in General Help is because this may be more of a Java and Ubuntu issue, then it is a Minecraft and Ubuntu. Any suggestions as to where to start?

---

### Post by dolphin194 on 2011-10-24
What Java are you running on the system?

---

### Post by Jaybyrrd on 2011-10-24
I am not on the machine right now, however, I am pretty sure that I am using OpenJDK 6. (Default)

---

### Post by dolphin194 on 2011-10-24
Ok. Next, what version of minecraft are you using? Is it a version of the beta, or is it the classic version?

---

### Post by Jaybyrrd on 2011-10-24
Honestly I am not sure, I am pretty sure just the latest version that is automatically downloaded when you login for the first time in a new machine. So 1.8.x?

---

### Post by liquidmonkey on 2011-10-24
just did this today actually. on my samsung series 9 laptop (has no dedicated graphics card).
try this...
[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)

even with graphics on low, distance at normal etc, its not very visually orgasmic to say the least.
BUT i can play, although i'd rather use my desktop at home tbh.

---

### Post by dolphin194 on 2011-10-24
Judging by what you said with "1.8.x," i would imagine you're running the beta version of minecraft.

I have searched around the forums a bit and found a thread at [http://ubuntuforums.org/showthread.php?t=1473293](http://ubuntuforums.org/showthread.php?t=1473293) that has a similar problem that you're having right here. I looked through it and they're having issues with slow Java on their machine.

Someone posted the following
> Here's what I did to get games on Pogo to work on my Acer Aspire 5517-5136 running 64 bit Edubuntu 10.04 LTS:

- quit Firefox

- go to System-->Administration-->Software Sources and make sure  the Partner repository is checked under third-party software.

- in Terminal run sudo apt-get update (to update the lists of software available from the Ubuntu repositories)

- in Applications-->Ubuntu Software Center remove OpenJDK Java 6  Runtime (doing so will automatically remove its other two dependencies)

- in System-->Administration-->Synaptic Package Manager check mark  and install sun-java6-plugin (doing so will automatically check mark  and install its required dependencies)

- reboot

- now go to pogo and try a few games to confirm that this procedure worked.

He said that his neighbor was having issues because the latest versions of Ubuntu have been using the Open JDK (like the one you are using) to run Java. 

Try using the closed-source sun-java6 plugin to run Minecraft and tell me what happens.

---

### Post by Jaybyrrd on 2011-10-24
Okay great, thank you both for your responses, I am going to go to work before making my way home tonight, but when I do this I will post an update. Thanks a ton! I really appreciate it!

---

### Post by dolphin194 on 2011-10-24
Exactly what the forums are for.

---

### Post by Jaybyrrd on 2011-10-24
I agree completely and really good news! The performance has increased significantly! However still not where it needs to be. So I did some reading and found this: [http://www.reddit.com/r/Minecraft/comments/hfp7m/to_anyone_with_a_nvidia_graphics_card_and_having/?utm_source=twitterfeed&utm_medium=twitter](http://www.reddit.com/r/Minecraft/comments/hfp7m/to_anyone_with_a_nvidia_graphics_card_and_having/?utm_source=twitterfeed&utm_medium=twitter)

However none of these are Ubuntu fixes so any recommendations to force minecraft, or even Java as a whole to use my graphics card?

---

### Post by Thelinuxgeek on 2011-10-24
In terms of Minecraft, I've found that the game runs much better on 64-bit operating systems. (Maybe this is the turning point for x64?)

---

### Post by Jaybyrrd on 2011-10-24
Perhaps, I think that because Java in itself is less efficient then, say C#, there is always a bit of a processing issue, but 64-bit really helps. The thing is that the graphics should not be processed by RAM or the CPU, that is why we buy GPU's. So I want to make sure it is running on that for the best performance.

Note: Just did a test, running average of 60 frames per second 1920 x 1080, and it is improving as I am in the game environment longer. I just find this odd when that is about where Crysis performs on benchmarks as well. :/

---

### Post by oldtimer7777 on 2011-10-24
> **Jaybyrrd said:**
> I am not on the machine right now, however, I am pretty sure that I am using OpenJDK 6. (Default)

Here is the one that works best for me:

[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)

Always use Sun Java, not the other kind. And use OpenGL if you are having video issues.

---

### Post by dolphin194 on 2011-10-25
So the problem is solved? You should probably mark the thread as [SOLVED]

---

### Post by Jaybyrrd on 2011-10-25
As of right now yes Solved. Thanks guys, I still had questions about the Video, but it's working fine enough. :)

---

### Post by liquidmonkey on 2011-10-26
please remember that MC is still in BETA so certain aspects are not entirely optimized. hopefully when the 'real version' is released (nov 11th i think) things like video card performance might be improved.

but i see where your coming from. who would have thought a pixelated blocky game would require more than crysis????????

---

