---
title: "Graphics Tablet is very glitchy"
date: 2011-01-12
forum: General Help
---

### Post by turtle153 on 2011-01-12
I have a Trust Flex Design Tablet that I recently bought, but I'm having problems configuring it on Ubuntu. (It works absolutely fine on Windows)

I've tried with the Wizardpen (xserver-xorg-input-wizardpen) and the Wacom (xserver-xorg-input-wacom) driver but they both have the same problems.

The 'name' of my tablet is "         WALTOP             Tablet    " (yes, with all the spaces :S)
The waltop driver gives some basic configuration options (I can turn off buttons etc) but not the settings I really need.

Here are the problems:
-The tablet doesn't respond unless I press the pen onto it, which means it draws. The tablet does support hovering but it won't work.

-It sometimes freezes for a bit and I have to press the pen in hard to get it moving again (the mouse works)

I'll be able to post any terminal outputs here if needed

---

### Post by Favux on 2011-01-12
Hi turtle153,

You don't say what release of Ubuntu you are using.

See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").

It turns out the xsetwacom TPCButton command ("off" is hover) was broken in xf86-input-wacom but the fix was added to the git repository last night.  So if you clone the git repository hopefully you'll now have hover mode available.  Provided you're in Maverick.

---

### Post by turtle153 on 2011-01-12
> **Favux said:**
> 
You don't say what release of Ubuntu you are using.

Maverick 10.10

I'll take a look now :)

---

### Post by neonboy on 2011-02-20
Hi Turtle, did you came up with a strategy?

I've got the same trouble

try to solve it in many ways.. but nothing near to success.


there is a bug on launchpad about trust flex design on 10.10

but it seems abandoned to itself.


Thank you anyway

---

### Post by Supergnu on 2011-04-02
So is it working yet?
I'm thinking of buying one.

---

