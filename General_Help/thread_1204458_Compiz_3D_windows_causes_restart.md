---
title: "Compiz 3D windows causes restart"
date: 2009-07-04
forum: General Help
---

### Post by NoizMaker on 2009-07-04
Hey guys, I'm new on the forums. Nice to meet you. I poked around here and can't find a solution to my specific problem so I thought I'd ask.
 
I am running a Wubi installation of Ubuntu 8.04.2 LTS on Windows 7 and the only issue I'm having is the "3D Windows" Option in the compiz setting menu. The desktop cube works fine until I select 3D Windows, then when I try to initiate the cube Ubuntu restarts automatically. Now I don't think this is my video drivers because I used Ubuntu 9.04 for a bit, but I migrated to this distro because 9 was slow and too buggy for me yet. 
 
Anyone know a solution? 
 
Thanks in Advance
 
Edit: The problem is now for compiz in general, it started restarting itself every time I try to use it. Should I just suck up and stick with 9.04?

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> Hey guys, I'm new on the forums. Nice to meet you. I poked around here and can't find a solution to my specific problem so I thought I'd ask.
 
I am running a Wubi installation of Ubuntu 8.04.2 LTS on Windows 7 and the only issue I'm having is the "3D Windows" Option in the compiz setting menu. The desktop cube works fine until I select 3D Windows, then when I try to initiate the cube Ubuntu restarts automatically. Now I don't think this is my video drivers because I used Ubuntu 9.04 for a bit, but I migrated to this distro because 9 was slow and too buggy for me yet. 
 
Anyone know a solution? 
 
Thanks in Advance
 
Edit: The problem is now for compiz in general, it started restarting itself every time I try to use it. Should I just suck up and stick with 9.04?

Hi and welcome, what is the model of the graphics card and what driver are you using?
Are you able to use the normal effects under system, preference, appearance,  visual effects tab.

---

### Post by NoizMaker on 2009-07-04
> **overdrank said:**
> Hi and welcome, what is the model of the graphics card and what driver are you using?
Are you able to use the normal effects under system, preference, appearance, visual effects tab.
 
I have an Intel 945 Chipset integrated video and I certainly can use the normal effects and select whichever option I wish in visual effects.
Thanks for replying so quick.

---

### Post by earthpigg on 2009-07-04
go to system -> administration -> hardware drivers

try a few different drivers, see what works :P

---

### Post by NoizMaker on 2009-07-04
> **earthpigg said:**
> go to system -> administration -> hardware drivers

try a few different drivers, see what works :P


It says "No Proprietary Drivers are in use on this system" Is that a bad thing?

---

### Post by earthpigg on 2009-07-04
> **NoizMaker said:**
> It says "No Proprietary Drivers are in use on this system" Is that a bad thing?

it means you are free and richard stallman would approve.

buuuut if you are a function-over-fashon kind of guy, you may want to give proprietary drivers a shot.

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> I have an Intel 945 Chipset integrated video and I certainly can use the normal effects and select whichever option I wish in visual effects.
Thanks for replying so quick.

Hi and the intel graphics with Hardy 8.04 should work well but I can not remember if I had any issues with the 3d windows on the cube. How much system memory? You may try and adjust the amount shared with the intel graphics in bios.

---

### Post by NoizMaker on 2009-07-04
> **overdrank said:**
> Hi and the intel graphics with Hardy 8.04 should work well but I can not remember if I had any issues with the 3d windows on the cube. How much system memory? You may try and adjust the amount shared with the intel graphics in bios.

Ok well I have 2 gigs of ram and I'll check the bios and see what I can do, however I used Jaunty previously and had no problem except it lagged a bit.

Edit: I have 128mb dedicated to video & the only option I have is to step down to 64

---

### Post by earthpigg on 2009-07-04
tried enabling proprietary driver?

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> Ok well I have 2 gigs of ram and I'll check the bios and see what I can do, however I used Jaunty previously and had no problem except it lagged a bit.

Edit: I have 128mb dedicated to video & the only option I have is to step down to 64

Ok you can use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and use the i810 and you may also install the 915 resolution package from synaptic manager also. This is going of my memory from using Hardy 8.04 :)

---

### Post by NoizMaker on 2009-07-04
> **overdrank said:**
> Ok you can use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and use the i810 and you may also install the 915 resolution package from synaptic manager also. This is going of my memory from using Hardy 8.04 :)

Hmm, well I have i810 enabled already. I tried installing the specific driver too and still the same issue, I can use Expo Wobbly Windows and stuff but the Desktop Cube appears to be the only problem.

Update: Ok I installed the 915 resolution and still the exact same issue... Thank you for your help, you are teaching me alot.

---

### Post by NoizMaker on 2009-07-04
> **earthpigg said:**
> it means you are free and richard stallman would approve.

buuuut if you are a function-over-fashon kind of guy, you may want to give proprietary drivers a shot.

I have no option in Hardware Drivers. Just a blank window and the message I described. Am I supposed to dl the proprietary drivers? Sorry I'm so new to Ubuntu it hurts, lol.

---

### Post by earthpigg on 2009-07-04
> **NoizMaker said:**
> I have no option in Hardware Drivers. Just a blank window and the message I described. Am I supposed to dl the proprietary drivers? Sorry I'm so new to Ubuntu it hurts, lol.

do this:

[http://cybernetnews.com/wp-content/uploads/2007/10/ubuntu-software-sources-proprietary-drivers.jpg](http://cybernetnews.com/wp-content/uploads/2007/10/ubuntu-software-sources-proprietary-drivers.jpg)

then, this:

[http://cybernetnews.com/wp-content/uploads/2007/10/enable-restricted-drivers.jpg](http://cybernetnews.com/wp-content/uploads/2007/10/enable-restricted-drivers.jpg)

full article, if you need it:

[http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/](http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/)

---

### Post by NoizMaker on 2009-07-04
> **earthpigg said:**
> do this:

[http://cybernetnews.com/wp-content/uploads/2007/10/ubuntu-software-sources-proprietary-drivers.jpg](http://cybernetnews.com/wp-content/uploads/2007/10/ubuntu-software-sources-proprietary-drivers.jpg)

then, this:

[http://cybernetnews.com/wp-content/uploads/2007/10/enable-restricted-drivers.jpg](http://cybernetnews.com/wp-content/uploads/2007/10/enable-restricted-drivers.jpg)

full article, if you need it:

[http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/](http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/)


Thanks, I tried but still a no go. Still not detecting any proprietary drivers at all.

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> Hmm, well I have i810 enabled already. I tried installing the specific driver too and still the same issue, I can use Expo Wobbly Windows and stuff but the Desktop Cube appears to be the only problem.

Update: Ok I installed the 915 resolution and still the exact same issue... Thank you for your help, you are teaching me alot.

Ok what key combination are you using for the desktop cube rotation? 
Everything works except for when you try and rotate the cube with ctrl, atl, single mouse click and hold to rotate the cube?

---

### Post by NoizMaker on 2009-07-04
> **overdrank said:**
> Ok what key combination are you using for the desktop cube rotation? 
Everything works except for when you try and rotate the cube with ctrl, atl, single mouse click and hold to rotate the cube?

That is it exactly. My computer reboots immediately as soon as I try.

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> That is it exactly. My computer reboots immediately as soon as I try.

Ok from the FAQ's, to set up the desktop cube
> Then, in System > Preferences > Advanced Desktop Effects Settings, go to General Options, Desktop Size tab, and make sure Horizontal Virtual Size is set to 4. Go back to the main window, and enable the Desktop Cube and Rotate Cube plugins.
You can "spin" the cube by pressing Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and click and drag.
and the last thing I can think of is what resolution are you using?

---

### Post by NoizMaker on 2009-07-04
lol, Yeah I know what you mean. My resolution is 1200x800 and I can do the side to side spin no problem. It's only pulling out the cube with ctrl+alt+click/drag that's causing the issue and it's intermittent. So I think to solve any more headache, I'm just going to wubi install Jaunty. I'll deal with the lag I had on it, lol.

---

### Post by overdrank on 2009-07-04
> **NoizMaker said:**
> lol, Yeah I know what you mean. My resolution is 1200x800 and I can do the side to side spin no problem. It's only pulling out the cube with ctrl+alt+click/drag that's causing the issue and it's intermittent. So I think to solve any more headache, I'm just going to wubi install Jaunty. I'll deal with the lag I had on it, lol.

You may also look at the link in my signature about intel graphics in Jaunty if you choose Jaunty again :)

---

