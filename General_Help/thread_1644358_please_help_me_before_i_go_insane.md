---
title: "please help me before i go insane"
date: 2010-12-13
forum: General Help
---

### Post by crazymonkeyfamily on 2010-12-13
hi all

i absolutely love ubuntu but i have recently had to change back to windows

the problem is this 

when i have ubuntu installed i cannot watch tv on the web properly 
it is very jerky and just not very pleasent to watch at all

hence this is the only reason i have gone back to windows as it plays fine...

so what can i do to solve it so i can get away from retchid windows ??

my graphics card isnt very special at all just an on board chip nvidea gforce 6100

sooooo please help me 

thanks all

---

### Post by amauk on 2010-12-13
Have you installed the nvidia binary driver (for 3D acceleration)

System > Admin > Hardware Drivers

---

### Post by BlueSpecial on 2010-12-13
Don't know if this applies to you but in my case I was experiencing the same difficulties. So I install "Ubuntu Restricted Extras" on Software Center and the problem was solved.

---

### Post by theozzlives on 2010-12-13
I have an nVidia 6100 on-board my MSI motherboard. I set the CMOS to share 256 MB RAM and installed ubuntu-restricted-extras and it works fine with Flash.

Oh, I also installed the restricted drivers.

---

### Post by crazymonkeyfamily on 2010-12-13
ok thanks 

i will format and reload ubuntu later on and see how i get on with your suggestions

:popcorn:

---

### Post by crazymonkeyfamily on 2011-01-11
hi all again

sorry i came down with flu so havent had chance to sort this damn issue out....

i have enabled the 3d nvidea and installed ubuntu access thing which you all said to do....


well the report is thus so far

i can get the tv to play online in a small box but it is real jerky on full screen

so what else can i try ?

this is the only thing i have issues with as we watch our tv online as we dont have a tv in the house

hope to hear from you soon

---

### Post by Foxcow on 2011-01-11
> **crazymonkeyfamily said:**
> hi all again

sorry i came down with flu so havent had chance to sort this damn issue out....

i have enabled the 3d nvidea and installed ubuntu access thing which you all said to do....


well the report is thus so far

i can get the tv to play online in a small box but it is real jerky on full screen

so what else can i try ?

this is the only thing i have issues with as we watch our tv online as we dont have a tv in the house

hope to hear from you soon

Are you running the 32 or 64 bit version of Ubuntu?  Is the content you are trying to watch flash content?

---

### Post by Quackers on 2011-01-11
Have you installed ubuntu-restricted-extras?

---

### Post by asmoore82 on 2011-01-11
The problem is very simple but hidden in a twisted maze.

Audio players are for playing music.
Video players are for playing videos.
Web browsers are for browsing the web.

We are all increasingly guilty of using web browsers for playing videos.
It just wasn't meant to be that way. Sure, for your typical quick and dirty
video needs, browsers have been working fine. It is when you want to watch a
decent quality video full screen, you really begin to notice the problem.

More specifically, though, the problem is usually Adobe Flash Player.
It is not optimized to take advantage of direct rendering or video acceleration on Linux.

The free Gnash player would perform much better but it is typically blocked from watching such videos.

So what's the root of all this insanity?

The real villain is DRM(Digital Restrictions Management).

---

### Post by marl30 on 2011-01-11
If your issue is with flash, you may want to try the flash-aid plugin. It has really dealt with all the issues I have had with flash. All my flash videos run smoothly now. Here's the link:[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

