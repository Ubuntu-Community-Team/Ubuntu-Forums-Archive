---
title: "How to set up multiple conkys"
date: 2009-08-02
forum: General Help
---

### Post by josephellengar on 2009-08-02
All right, I'm getting a new computer soon and would like to get a new conky setup.  I don't have very much experience and keep getting error messages when I try to run more than one conky.  I've attached the screenshot of my conky and my .conkyrc.  Here is what I'd like to do:

I'd like to take the system information and everything under the system heading to run along the top of the screen, directly below the gnome-panel.

I'd like to have the processors, memory, and HDD information on the middle left.

I'd like to have both top process headings on the middle right of the screen.

And I'd like to have all of the network information in the middle on the bottom.

---

### Post by squaregoldfish on 2009-08-03
It's easy to set up multiple copies of conky - you can add the -c <filename> flag to the conky command to make it read a different file, and from there you can run as many copies as you like.

If you'd prefer to have only one copy of conky running, you can play around with the offset flags in your conkyrc file to move things around. I've never played with this, so don't have any tips, but I can't think that it's very hard to figure out...

Steve.

---

