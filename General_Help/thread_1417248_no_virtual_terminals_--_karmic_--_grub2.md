---
title: "no virtual terminals -- karmic -- grub2"
date: 2010-02-27
forum: General Help
---

### Post by shawnisalk on 2010-02-27
Hello,

I love virtual terminals...but I can't get them to work on my Karmic laptop.
I have a Radeon card and I'm running Grub2.

I just upgraded to 9.10 and didn't have virtual terminals in Jaunty either,
BUT
the first time I tried to use a virtual terminal **after** the upgrade, it worked!
...but only for 1 second...then it became a curtain of colorful lines.

I added additional resolutions to /etc/default/grub but this hasn't changed anything.

Since it did display for that one second, I assume the solution is only a matter of configuration, but what? and how? (refresh rate?)

Can anyone help?

Thanks!

---

### Post by dcstar on 2010-02-27
> **shawnisalk said:**
> Hello,

I love virtual terminals...but I can't get them to work on my Karmic laptop.
I have a Radeon card and I'm running Grub2.

I just upgraded to 9.10 and didn't have virtual terminals in Jaunty either,
BUT
the first time I tried to use a virtual terminal **after** the upgrade, it worked!
...but only for 1 second...then it became a curtain of colorful lines.

I added additional resolutions to /etc/default/grub but this hasn't changed anything.

Since it did display for that one second, I assume the solution is only a matter of configuration, but what? and how? (refresh rate?)

Can anyone help?

Thanks!

Old Nvidia cards are only fully supported up to 8.04 IIRC, if this is your issue newer video hardware may be the simplest solution.

---

### Post by shawnisalk on 2010-02-27
Hmph... Well, that's unfortunate... How the heck do you replace the video card in a laptop?

Thanks for the info,
Shawn

---

### Post by shawnisalk on 2010-02-27
Help! 
I installed the fglrx driver to try to fix the problem, but that didn't work, so I uninstalled it.
No driver was recognized and I had to run gdm in low graphics mode.

Then, I installed envyng hoping that it would be smarter than me, but that didn't work either (running in low graphics mode).

Then, I re-installed the open source Radeon driver, and that didn't work either.
And I'm still stuck (this very moment) in low-graphics mode.

Any suggestions on how to get back to where I was with a more or less working video card?

[I'm now uninstalling envyng...]

---

