---
title: "Shift+F3 in terminal not behaving as expected"
date: 2010-07-19
forum: General Help
---

### Post by SlaughterDog on 2010-07-19
So for a while now at work I've been using Ubuntu and it's been working quite well. I run tn5250 in gnome-terminal and everything works, except when I try to hit shift + an F key. 
What happens when I do is something like 01;2R gets inserted. 

How might I make this work?

---

### Post by Funkey Monkey on 2011-03-05
Has anyone been able to figure out how to get ****+F3 (F15) to work, as I need it to debug my program in tn5250

---

### Post by dwiel on 2012-11-06
I'm also still having this problem in 12.04.  I want to assign a key to shift+F3 in emacs, but it gets turned into ";2R" Lots of *-f* combos have similar a effect.  I have noticed that xterm does not have this problem, only gnome-terminal.

```

shift+f2          - ;2Q
shift+f3          - ;2R
shift+f4          - ;2S
alt+f2            - ubuntu captures this chord
alt+f3            - ;3R
alt+f4            - ;3S
shift+alt+f2      - ;4Q
shift+alt+f3      - ;4R
shift+alt+f4      - ;4S
ctrl+f2           - ;5Q
ctrl+f3           - ;5R
ctrl+f4           - ;5S
ctrl+shift+f2     - ;6Q
ctrl+shift+f3     - ;6R
ctrl+shift+f4     - ;6S
alt+ctrl+shift+f2 - ;8Q
alt+ctrl+shift+f3 - ;8R
alt+ctrl+shift+f4 - ;8S

```

---

### Post by wildmanne39 on 2012-11-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

