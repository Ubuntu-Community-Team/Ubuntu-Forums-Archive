---
title: "Display which files are currently open right now"
date: 2011-08-27
forum: General Help
---

### Post by [V] on 2011-08-27
I am running a mulithreaded python script. 
I keep getting errors that I have reached my maximum open file limit.

My script spawns several child processes and uses subprocess to run a bunch of things.

I just need a way to view files currently open due to this process AND all of its child processes.

Is there an easy way to do this, so I can view these in real time?
This way I can figure out which part of my program is hogging my nofile setting.

Thank you!

---

### Post by AlphaLexman on 2011-08-27
What are the exact errors?

Have you looked into '**lsof**' (list open files)

---

