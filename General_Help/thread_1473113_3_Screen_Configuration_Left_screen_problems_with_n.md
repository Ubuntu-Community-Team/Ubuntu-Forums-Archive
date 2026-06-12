---
title: "3 Screen Configuration: Left screen problems with nvidia-common and xinerama"
date: 2010-05-04
forum: General Help
---

### Post by damien_d on 2010-05-04
Hello all,

I have recently upgraded from 9.10 to 10.04 on my main desktop and I have been having some problems with a triple-screen setup that used to work flawlessly under NVIDIA Drivers 185 and 190.

I have also done a complete re-installation of the system, and I have observed the same problems.

In my setup, I have 3 screens: 
  - Screen 0, a Samsung 23" with 1920x1080 in the physical centre on GPU 0
  - Screen 1, a HP 17", with 1280x1024 on the physical left on GPU 0
  - Screen 2, an LG 17" with 1280x1024 on the physical right GPU 1

GPU0: nVidia GTX275
GPU1: nVidia GT240

When I have the HP screen on the left (whether or not the LG is enabled or disabled), when I move the mouse cursor to left-hand screen, it starts flashing around, going crazy near the border.  If I try to move the mouse, sometimes, it goes back into the centre screen, other times, I have no other option than ctrl-alt-backspace.  Once, it caused gdm to crash and I got the login screen again (with the nvidia splash screen).

If I disable xinerama, then I can have this screen on the left with no problems (though, of course, I have 3 separate desktops and cannot move windows between desktops).

If I instead put the HP on the logical right of the LG (hence, I need to go over the right edge of the LG to get to the HP screen), then I do not have any problems and I can use the screen normally.

Has anyone else encountered these issues?  I have attached my xorg.conf files for when this appears to happen for each of the scenarios listed.

  -- Damien

---

### Post by btelles on 2010-05-04
YES!!! I'm experiencing EXACTLY this same problem! 

In addition to your description, I'd like to add that I've tried upgrading, and using a clean install of Lucid.

I have also tried this with Kubuntu (my usual desktop environment), and then with Gnome.

In all of the above situations I had exactly the same problem (mouse keeps flashing when it crosses to the left-most monitor).

Also same as you, if I disable Xinerama and use separate X screens, the  problem goes away. I am rather certain that the problem only occurs when  Xinerama is enabled.
Here's a quick environment rundown:


[LIST]
[*]GTX275
[*]GTX275
[*]64-bit Ubuntu
[/LIST]
Thanks for starting this thread!!!!
Lack of relatively simple video support like this makes it difficult to want to continue using Linux, but luckily the community is great, and hopefully someone knows of a quick work-around or can patch up the driver. By the way, do you know if nVidia is aware of the problem?

---

### Post by damien_d on 2010-05-04
> **btelles said:**
> YES!!! I'm experiencing EXACTLY this same problem! 

In addition to your description, I'd like to add that I've tried upgrading, and using a clean install of Lucid.

I have also tried this with Kubuntu (my usual desktop environment), and then with Gnome.

In all of the above situations I had exactly the same problem (mouse keeps flashing when it crosses to the left-most monitor).

Also same as you, if I disable Xinerama and use separate X screens, the  problem goes away. I am rather certain that the problem only occurs when  Xinerama is enabled.
Here's a quick environment rundown:


[LIST]
[*]GTX275
[*]GTX275
[*]64-bit Ubuntu
[/LIST]


I too am 64-bit Ubuntu.

What's your physical layout arrangement (what screens on what ports)? Are you able to post a working and broken xorg.conf?

> 
By the way, do you know if nVidia is aware of the problem?

No idea. Probably not :)

If we don't get much luck here, there is a nvidia linux driver forum, but they will probably tell us to install the vanilla driver and start from there.  

Getting the vanilla driver working along side the ubuntu repo one is a world of pain in itself...

Thanks for the reply... at least I now know I'm not crazy :)

  -- Damien

---

### Post by damien_d on 2010-05-04
I just tried putting my LG screen on the left (which is on a different GPU) with the same results as reported in the first post.

  -- Damien

---

### Post by SkaffenUK on 2010-05-06
I believe you've hit [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100") - it's not NVidia-specific, it's a general problem with X and Xinerama and having screens to the left of Screen 0. Fingers crossed they'll bring the fix into Lucid.

---

### Post by btelles on 2010-05-07
Hi guys,

I manually changed the devices in my xorg.conf such that screen 0, device 0 and monitor 0 were pointed to the left-most monitor. This workaround worked beautifully, albeit it took half an hour of fiddling (I don't know what most of the stuff in an xorg.conf file does).

Here's where I found the solution:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/574386](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/574386)

Hope this helps!

---

### Post by damien_d on 2010-05-07
I might give the xorg.conf hacking a shot.  However, my task bar is on my 23" monitor, and I have a habit of having a lot of windows open :)

Still, if I can get a workaround, it might be useful.

  -- Damien

---

### Post by johansson.seb on 2010-05-08
This is probably what is known as bug [#563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100"):

> According to the Xorg people working with the bug, in Xinerama mode - event coordinates are relative to the primary secreen - Screen 0. But, in the version of Xorg that now is in use with Lucid (1.7.6) event coordinates are unsigned integers.

With unsigned integers, negative coordinates can not be represented, thus xorg can not function with screens above or to the left of Screen 0. So, if you can, let your upper-left screen be Screen 0.

The xorg people have a patch that seems to be working (simply changing back to signed ints). I hope that this will make it into an updated ubuntu Lucid package soon.

> As Daniel Dadap wrote, this seems to correspond to the Xorg bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=24986]("https://bugs.freedesktop.org/show_bug.cgi?id=24986")

---

### Post by Quentusrex on 2010-05-08
Yes, this looks like the same bug. the tl;dr. form is that screen positions variable for x and the one for y was changed from a signed int to an unsigned int. 

What does this mean for you? It means you need to look up which of your monitors is monitor 0, and if you have multiple GPU's you need to find which one is GPU 0. Then you have to place GPU 0 / Monitor 0 in the top left, with GPU 0 Monitor 0 to the right of the first. Then GPU 1 has to go below GPU 0, with monitor 0 on the left and monitor 1 on the right.

---

### Post by SL666 on 2010-06-03
I also have this issue.. but rearranging the physical monitors in the fashion has worked.

however... Now i have my panels on my left most monitor, any idea how to get them to the middle monitor?

---

### Post by SL666 on 2010-06-03
fixed my panel issue with advice from here.

[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/8152](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/8152)

basically 

run 
gconf-editor

explore to apps/panel/toplevels

Go to the panel you want to change set "monitor" to the number you want eg 1 then click on another value, and the panel should move.

---

### Post by damien_d on 2010-06-07
In the following bug, there is a ppa package with a new xorg server that worked for me:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100)

With the package, my issues are resolved. It may work for you too.

  -- Damien

---

