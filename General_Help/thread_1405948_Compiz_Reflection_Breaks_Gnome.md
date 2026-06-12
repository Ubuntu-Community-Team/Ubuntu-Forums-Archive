---
title: "Compiz Reflection Breaks Gnome"
date: 2010-02-13
forum: General Help
---

### Post by chessnerd on 2010-02-13
So I was messing around with some Compiz features in the CompizConfig Settings Manager yesterday and, when I clicked on the box for Reflection, my computer froze completely. No mouse, no Ctrl-Alt-Backspace, no switching to a terminal, nothing. So, I hard booted it and, when I booted it up again Gnome would start to load, but then everything would freeze again. Tried the previous working kernel as well. I can get LXDE to load, but when I disable Compiz settings there it doesn't effect Gnome at all.

So, any ideas what I could do, or should I just backup and reinstall?

---

### Post by CrusaderAD on 2010-02-13
Probably some kind of incompatibility with your graphics card. Can you get to the login screen? Try holding ctrl alt f2 and log in to the command line. From there, try removing compiz.

---

### Post by chessnerd on 2010-02-13
> **raptormanad said:**
> Probably some kind of incompatibility with your graphics card. Can you get to the login screen? Try holding ctrl alt f2 and log in to the command line. From there, try removing compiz.

I can get to the login screen and log into LXDE, but I've been using Compiz features (like desktop cube) for months now without any issue. However, I'll try removing Compiz and see if that'll help.

---

### Post by CrusaderAD on 2010-02-13
Let us know how it goes. Another Michigander here!

---

### Post by chessnerd on 2010-02-13
No good. Loaded up LXDE, went to Synaptic, completely removed Compiz, logged off, tried to load up Gnome and... freeze. The panels at the top and bottom just started to load when everything stopped. Hard boot.

Does removing the Compiz package actually remove Compiz, or are there other things I need to get rid of?

Glad to hear from another Michigander. I hope you're also a Wolverine.

---

### Post by CrusaderAD on 2010-02-13
Check this out:
[http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html")

---

### Post by chessnerd on 2010-02-13
Well, I just stripped off all the Compiz packages. Apparently they all depend on compiz-core, so removing that removed everything else. 

I'm back in Gnome, so it worked. However, I have another issue now: no wireless.

Any reason for that?

---

### Post by CrusaderAD on 2010-02-13
Hm... we're getting there... when you go to System > Administration > Hardware Drivers, do they list any for your wireless card?

---

### Post by chessnerd on 2010-02-13
> **raptormanad said:**
> Hm... we're getting there... when you go to System > Administration > Hardware Drivers, do they list any for your wireless card?

"No proprietary drivers are in use on this system." And the rest is blank. I am using backported drivers under the most recent kernel update and I tried booting into the older one, but it didn't make any difference.

I can see the wireless network, and when I try to connect it will work at it for a while, but I just can't connect to it. I've made sure the password is right in System>Preferences>Network Connections and it was working fine before this all started so apparently something I removed was necessary, but I don't get why a part of compiz would be required to use a wireless network...?

---

### Post by CrusaderAD on 2010-02-13
That's weird, cause it's clearly working if you can see the networks. Try reinstalling compiz and see if it helps. It should set things back to the defaults.

---

### Post by chessnerd on 2010-02-13
Okay, the issue was with the router, not the removal of Compiz. I restarted the router and, boom, internet access. 

At first I was really freaked out because I tried to connect using ethernet and it failed to do so! Then I calmed down and thought, "Okay, there is no way that Compiz could break the ethernet connectivity." So I restarted the router and both the ethernet and wireless now work. (I'm actually typing this on my laptop right now.)

Thanks for your help. I'm going to try to reinstall Compiz and see if everything works okay. If not, I can live without the cube until Lucid comes out.

---

### Post by CrusaderAD on 2010-02-13
Cool, glad you got it working. I thought that was weird and figured it maybe the router... but who knows, could have been a bunch of things. Good thing it was a simple fix.

---

### Post by chessnerd on 2010-02-13
Alright, Compiz is working alright now that I disabled Reflection. I just need to make sure to **never** activate the Reflection again.

Thanks again for your help.

---

### Post by Troy large on 2010-02-14
I too clicked on "reflection" in CompizConfig Settings Manager and had a complete freeze up of the system. After a reboot I got to the log in screen, selected the account, entered the password and after a slight amount of grinding it froze again.  I logged into another account, opened the terminal window and did the following:  su  gconftool-2 --recursive-unset /apps/compiz  That fixed the problem.   I t should, however, be noted that in "freezing", it was so frozen I could not open a terminal window - that is, " F1" would NOT bring up the terminal, thus I was unable to fix it directly. If anyone knows a way to get the terminal window up when compiz is so busted, please say so.

---

