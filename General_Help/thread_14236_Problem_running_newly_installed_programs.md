---
title: "Problem running newly installed programs"
date: 2005-02-05
forum: General Help
---

### Post by petenz on 2005-02-05
Ok, got Ubuntu installed and got a few things working - many thanks to ubuntuguide.org and other posters in the forums.

I've noticed that a couple of things I installed (games actually - thought I'd start with some non mission-critical things  :wink: ) don't seem to run, although some do.

Any clues? Could they just be broken? For a while I thought that it might be because they were in the filesystem rather than my home directory - but this doesn't seem to be the case as one of them does work.

I did try moving one which doesn't run with Nautilus into my home directory by dragging and dropping, and got the error message 

""/usr/games/nInvaders" cannot be moved because you do not have permissions to change it or its parent folder."

So I guess to move this you'd sudo mv it to where you want it - is there a way to do this within Nautilus?

A minor question - but I'm hoping the answer will help if I hit the same problem with other applications.....

One day (probably/hopefully soon) I'll look back on this post and shake my head at what a newbie I was......

---

### Post by benjamin on 2005-02-11
This is not the solution to your problem, because the right locatin of games is /usr/games.

BTW if you want to have root permission with nautilus start it from terminal
sudo nautilus

bye

---

