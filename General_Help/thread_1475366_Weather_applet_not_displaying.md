---
title: "Weather applet not displaying"
date: 2010-05-06
forum: General Help
---

### Post by labatts on 2010-05-06
Hi all,

This is admittedly a minor problem, but for some reason the** weather is not being displayed next to the date and time**, nor is there weather information when I mouse hover.

I have ensured that the 'display weather' option is toggled, and that the location is correct.  I have toggled it off and on a couple of times to see if it will reset, but to no avail.  When I enable it, I can see the space being made for it, but nothing is displayed. (I have also tried a different theme to see if that affects it, but it is not that either.)

Lastly, I snooped into the configuration editor, but did not find anything different there either.  (all appropriate fields were checked).

In case it matters, i'm running 10.04 Ubuntu netbook on an asus eee 1005ha.  2 gb ram. (perfect set up for college, love it... but I have to look outside to see the weather!)

Thanks for any help!

---

### Post by ThomasTC on 2010-05-09
I have the same problem. Furthermore, the separate Weather Report applet that has been on my panel for ages has been displaying "--" since yesterday. Maybe the weather server they use has gone down, or changed its API?

Edit: I looked at the network traffic using Wireshark. When I change the location settings of the clock applet, nothing happens! The applet does not even *try* to update. I'll see what the Weather Report applet does...

Edit 2: I'll be damned. I just removed both applets from the panel and added them again, and now both work perfectly! Maybe that works for you as well?

---

### Post by IanBal on 2010-05-09
Removing and replacing the applet didn't work for me. I Had to log out and log back in again.

I think the cause of the problem was that a few days ago, the network was gone for a few hours. My computer was still connected to the router, but the ISP (chello) obviously had some problems (nothing new for them).  When the net was back, the weather didn't work any more.

It's working again but what's really strange now is the current weather display is completely wrong - I'm here in Vienna, Austria, the applet says it's raining, and I can look out my window and see some stars among some thin high clouds.  I also have Brisbane and Cairns Australia in there, but the home is set to Vienna. It's almost like there were some updates somewhere which have messed the gnome clock and weather up...

---

### Post by labatts on 2010-05-09
Hmm.  Well, thats good that it worked for you ThomasTC.  I don't seem to be able to try that, though.  I am running Ubuntu Netbook, and they seem to have disabled the remove function (its grayed out).  I double checked in the configuration editor, and I cannot uncheck the field that says it is locked.  

I believe that this WAS an option (to remove the applets) in 9.10, but I never tried it because I was not sure that I would be able to put Humpty-Dumpty back together.

---

