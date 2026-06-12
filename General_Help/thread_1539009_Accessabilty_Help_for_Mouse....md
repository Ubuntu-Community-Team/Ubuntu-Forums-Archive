---
title: "Accessabilty Help for Mouse..."
date: 2010-07-26
forum: General Help
---

### Post by Professor Bear on 2010-07-26
What is it?

I don't know if this really counts as a How-To or not, but it sure comes in handy... What is it? It's an easy way to switch from Left-Hand (LH) Mouse to Right-Hand (RH) Mouse with a single click.

Why?

When pointing devices (mouse) first came out on the scene (yes, I am about 150 years old), I learned to use the mouse with my left hand, and single hunt and peck on the keyboard with my right... Then I re-learned it the other way around, then it got all mixed up in my head, and so I like to use sometimes my left hand to use a mouse, sometimes my right hand.  I got the idea that it would be nice to have a single-click way to change the mouse from LH to RH and vice versa. Oh sure, there are mouse applets that can do the same thing, but they all take several clicks to get the job done.

When I put my feet up on the stool that is on the left side of my desk, I want to use a RH mouse. When I put my feet up on the right side, I want a LH mouse. I switch often just because I want to.

How?

Here's how to do it. First, I made a couple of little icons. One is 'L' for LH mouse, the other is 'R' for RH mouse. Make them with any simple drawing program, and save them as .png - size 32 x 32 pixels - save in /usr/share/icons.

"Other Click" on the desktop, and choose create new link to application. For the LH button, the command is xmodmap -e "pointer = 3 2 1"  and for the RH button, the command is xmodmap -e "pointer = default"  (assuming your default is RH).

Change the "launch icons" to the little pictures you put in /usr/share/icons, and there it is. Easy change from RH to LH mouse.

Attached is a picture of what the icons look like on the desktop. You can make yours pretty...

---

