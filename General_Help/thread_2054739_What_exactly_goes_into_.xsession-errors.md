---
title: "What exactly goes into .xsession-errors?"
date: 2012-09-08
forum: General Help
---

### Post by Roasted on 2012-09-08
There's a hidden file in your home directory called .xsession-errors. I know the name of the file is probably pretty obvious, but I'm curious as to what *exactly* goes into that file. Reason I ask is this. I have a server running downstairs with a regular Ubuntu 12.04 instance. I chose to use the desktop variant for my server because I have a spare 17" LCD monitor. I wanted to have this monitor hooked up to my server so when I'm in my office I can watch the video surveillance feed outside on a 3rd monitor without occupying my dual screen setup on my desktop (my server and desktop are right next to each other).

For a while I ran the video stream through Totem. I noticed things would begin to stop working. Most notably, Subsonic is the first I noticed. Then I go into troubleshooting Subsonic only to find out later the entire hard drive is maxed. When I run ncdu (awesome disk space terminal based app), I find that .xsession-errors has maxed out the rest of my HDD space. No problem! Wipe it and you're good.

After this, I set up a basic HTML page which contained the MJPG URL's of the streams from my network cameras. I figured maybe it was something with Totem that was populating the .xsession-errors. Then, go figure, things go south a few weeks later and I totally forget about this issue. Sure enough, ncdu brought it back to my attention - HDD maxed, thanks to .xsession-errors.

I just set up a basic bash script to run daily which removes the .xsession-errors file, however I still have to wonder... what *exactly* goes into that file??

---

