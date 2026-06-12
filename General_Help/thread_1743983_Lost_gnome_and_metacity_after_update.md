---
title: "Lost gnome and metacity after update"
date: 2011-04-29
forum: General Help
---

### Post by zachthejones on 2011-04-29
I did a clean install of 11.04 and then installed the updates it prompted me to. After restarting I was missing metacity and when I checked in synaptic I didn't have gnome installed. Here's the error message I got when I tried to install gnome (and dependencies):

[IMG]https://lh3.googleusercontent.com/_VqpKhc2JmsU/TbtysB5nBWI/AAAAAAAAAMk/faYAw1Foj4o/s800/Screenshot-2.png[/IMG]

help please!

---

### Post by Hedgehog1 on 2011-04-30
zachthejones,

You are not running the standard Natty 11.04, but have loaded the Gnome-Shell 3.0 over the top of the base Natty install.

Metacity and Gnome 2.x were un-installed when you install Gnome-Shell 3.0

Beyond that little bit of knowledge, others will have to help you.

***The Hedge***

:KS

---

### Post by zachthejones on 2011-04-30
thanks man - that sounds about right. I had enabled some extra repositories and I'm thinking one of them threw gnome-shell 3.0 on top of my initial install. Since I had just started getting stuff setup I just started over from scratch and stayed away from that repository. Things are working great now!

---

### Post by zachthejones on 2011-04-30
yeh....so it somehow happened again on this install....the only repository I added that might have switched me over to gnome-shell 3.0 would be the Gnome 3 repository - would that do it?

I installed kubuntu-desktop so i can work outside gnome and try and fix things...gonna try uninstalling the gnome stuff and disabling the repository and then reinstalling ubuntu-desktop...unless you have any other suggestions...

---

### Post by zachthejones on 2011-04-30
Well, in removing different gnome 3.0 packages I finally managed to make the OS unstable and unresponsive. So I went for another clean install and pulled it off without a hitch this. I had been using Ubuntu Tweak to add repos and install stuff, but this time I just used the command line and only added the kupfer and hotot repos.

Did a reboot and everything still runs like it's supposed to....just trying to get used to this unity shell thing. Not too bad so far....

---

### Post by Hedgehog1 on 2011-04-30
Sometimes, A clean install is the only real solution.  It can be a hassle, but what are you going to do?

Glad you are operational again!

***The Hedge***

:KS

p.s. There are a few Unity tips in the second post of this thread: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

---

