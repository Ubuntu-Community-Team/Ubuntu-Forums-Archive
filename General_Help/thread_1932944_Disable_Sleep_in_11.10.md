---
title: "Disable Sleep in 11.10"
date: 2012-02-28
forum: General Help
---

### Post by Reiik on 2012-02-28
I recently migrated from Fedora to Ubuntu 11.10 on my laptop. I'm really happy with the change so far, except that I often have the need to run a series of hour-long jobs overnight, and as best I can tell, Ubuntu goes to sleep after about an hour and a half nomatter what I do.

I can only tell because when I hit a key to wake the screen up in the morning it takes a few seconds (normally comes up instantly), and when I check its progress a series of tasks that should've taken 4 hours max is less than halfway done. I know it's not the job just taking longer than it should - I'm basically running the same thing over and over, and I inserted date commands between each run and I can see the jobs running exactly as long as I expect, up until it hits the point where it just stops, usually after the first or second run.

I would expect this to be fairly trivial to solve but it's really important for what I'm doing that I get this figured out. I have the power settings on "Don't Suspend" regardless of whether it's charging or not (and I obviously leave it charging when I do this), I leave the lid up, and I tried installing Jupiter and setting it Maximum Performance. No dice. Any help would be greatly appreciated.

**EDIT:** After trying a few suggestions I found elsewhere, the only solution I found was to install Caffeine and set it to keep the system from sleeping while Bash is running. This seems to have fixed the problem.

---

