---
title: "use external monitor as static desktop?  separate X window required?"
date: 2009-09-29
forum: General Help
---

### Post by Pitt Stains on 2009-09-29
Hi,

I'm running 9.04 on a laptop from System76 with Intel integrated graphics.  When I use an external monitor, I use a Dell monitor via VGA.

I've set up my desktop with 4 horizontal panels; i.e., in Compiz my desktop has a horizontal virtual size of 4, one for each side of the rotating cube.  I believe the default key binding for switching between them is Control + Alt + Left or Right arrow key, if you're not sure what I mean about my desktop settings.

Ideally, I'd have the external monitor separate and static, meaning I'd like for the external monitor to display the same desktop view all the time.  When I switch from one virtual desktop view to another on my laptop screen, the external monitor should stay put.  Does that makes sense?

If I can't get that, I'd at least like to control which monitor my Gnome panels show up on.  I have my external monitor above my laptop screen, and when I use System > Preferences > Display, Gnome assumes I want my panels on the top screen, which is not what I want.

I'm not too familiar with this aspect of Ubuntu config, though I'm comfortable in other areas.  I'm not even sure what to Google for!  Thanks for any help.

-Pitt

---

### Post by Pitt Stains on 2009-10-03
Here's what I leared after much research:

Metacity no longer (but apparently used to) support a static screen (i.e., one screen switches to a virtual desktop but the other stays put).  There are some window managers that do, but at this point I don't want to move away from Metacity.  A work-around is to, in the monitor you'd like to have remain static, pin the windows of interested to the visible works (i.e., right-click the window and check "Always on Visible Workspace."

I couldn't find a way to designate my laptop screen as the primary and still keep it below the external screen.  So I compromised, and this is working fairly well for me.  I right-clicked the bottom panel, selected properties, and unchecked "Expand."  Then I dragged it to the bottom of my bottom screen and expanded it again.  Now my top panel is at the very top of the top screen, and my bottom panel is at the very bottom of my bottom screen.

---

