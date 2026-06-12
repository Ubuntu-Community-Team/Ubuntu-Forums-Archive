---
title: "Make each monitor separate workspace/viewport"
date: 2010-10-26
forum: General Help
---

### Post by drmichael on 2010-10-26
I have a dual-monitor setup (laptop screen to HDMI TV screen) and would like to have each monitor be its own workspace or viewport.  Currently, each monitor has two workspaces/viewports.  

How do I make this work?

Is it possible to have two viewports/workspaces for the laptop screen when the TV is not plugged in and then have them each have their own when both displays are plugged in?

Thanks!

---

### Post by papibe on 2010-10-26
I know how to do it with an nvidia card, and using the nvidia driver. What graphic card do you have?

Regards.

BTW: I think the term you're looking for is "two different XScreens".

---

### Post by drmichael on 2010-10-26
> What graphic card do you have?

I can't believe I forgot this.  It's an Intel Mobile 4 Series Chipset Integrated Graphics Controller GM45.

---

### Post by papibe on 2010-10-26
I'm afraid I'm not very "verse" on intel graphics, but it seems there's a linux intel graphic driver. Search the forums to learn how to install and configure it. So far I've found this old one: [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582").

In the latests version of Ubuntu, the nvidia driver is available on System -> Hardware Drivers. There, you just activate it. Check if the Intel driver is available there for you.

Good Luck!

---

### Post by drmichael on 2010-10-26
I don't believe that the problem is with the driver.  Everything seems to display correctly.  Something in Ubuntu is just generating 4 different viewports/workspaces (2 per display) when I want it to just do two (1 per display).

Also, I'm on Ubuntu 10.10

---

### Post by papibe on 2010-10-26
Ohh!!... sorry, I did not understand correctly. Do this:
[INDENT]Rigth click on the little workspaces icons (bottom right corner).
Select Preferences.
Reduce the number of workspaces
It may be necessary to repeat this in the other screen (monitor)[/INDENT]

Good Luck!

---

### Post by drmichael on 2010-10-27
That't what I wanted for the most part.  Now, is there a way to make it so that when there is only one monitor plugged in, I automatically get 2 viewports for the single monitor?

---

