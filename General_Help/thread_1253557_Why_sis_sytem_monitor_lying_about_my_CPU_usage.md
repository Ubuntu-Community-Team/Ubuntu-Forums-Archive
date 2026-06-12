---
title: "Why sis sytem monitor lying about my CPU usage"
date: 2009-08-30
forum: General Help
---

### Post by mazz0 on 2009-08-30
Can anyone explain the discrepancy between the CPU usage shown in the attached screenshots?  Crazy huh?  I wish there was a better system monitor, like Process Explorer in Windows ("why don't you use Windows if you love it so much?" comments not needed, thank-you)

---

### Post by Liolikas on 2009-08-30
There are btter monitors but they are for terminal geeks (htop etc.). Try them. They are even better than windows one.

---

### Post by mazz0 on 2009-08-30
Am I being thick?  I was thinking that the cpu% column showed percentage for one core, meaning the values in that column add up to 36% of one core.  Does it actually mean 36% of total CPU capacity?  If so, then I suppose that roughly matched what the graph is showing...

---

### Post by P4man on 2009-08-30
One core at 100% and the other idle => 50% cpu load.

Thats not to say gnome system monitor doesn't,because it does. it eats far too much cpu itself. If you want something "better" use top from the command line.

---

### Post by mazz0 on 2009-08-30
> **Liolikas said:**
> There are btter monitors but they are for terminal geeks (htop etc.). Try them. They are even better than windows one.

I was about to say "yeah, I just wish there was a nice gui front end for them", but I just had a play around with System Monitor and found it actually does a lot more than I realised!  Shows the command on mouse-over, shows/searches open files from the menu, shows in a tree by selecting dependencies in the view menu!  I think that's everything I wanted!  How on earth didn't I see those things before?  I'm so stupid.  I'm loving System Monitor now :)

---

### Post by mazz0 on 2009-08-30
> **P4man said:**
> One core at 100% and the other idle => 50% cpu load.

That's not to say gnome system monitor doesn't,because it does. it eats far too much cpu itself. If you want something "better" use top from the command line.

Yeah, it does eat a lot of CPU doesn't it?

I just tried htop like [Liolikas]("http://ubuntuforums.org/member.php?u=67515") suggested - it's nice.  I just don't like having to run things in terminals - it doesn't look cool.  Maybe I should write a pretty front end for it?

---

### Post by jocko on 2009-08-30
> **mazz0 said:**
> Can anyone explain the discrepancy between the CPU usage shown in the attached screenshots?  Crazy huh?  I wish there was a better system monitor, like Process Explorer in Windows ("why don't you use Windows if you love it so much?" comments not needed, thank-you)
What discrepancy? In one picture the few processes that are shown and not rounded down to zero use 36% of the total cpu capacity (15+9+7+3+1+1), in the other the total cpu usage is at about 40%. So both pictures show pretty much the same. What's your problem with that?

---

### Post by Liolikas on 2009-08-30
Some ppl like this way ex:
[http://crunchbang.org/images/crunchbang-screens-02/crunchbang-terminal-htop-worldclock.png](http://crunchbang.org/images/crunchbang-screens-02/crunchbang-terminal-htop-worldclock.png)

But htop mainly is tool for server administration where gui is not possible at all. You should use that gnome thing for gui.

---

### Post by mazz0 on 2009-08-30
> **jocko said:**
> What discrepancy? In one picture the few processes that are shown and not rounded down to zero use 36% of the total cpu capacity (15+9+7+3+1+1), in the other the total cpu usage is at about 40%. So both pictures show pretty much the same. What's your problem with that?

Yeah, for some reason I was thinking those %s were per core, not total.  Don't know why, I must be used to that from some other programme - maybe that's how Process Explorer does it, I don't remember now.

---

