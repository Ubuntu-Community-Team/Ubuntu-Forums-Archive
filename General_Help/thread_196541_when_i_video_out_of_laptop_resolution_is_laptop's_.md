---
title: "when i video out of laptop resolution is laptop's native res,, not ext. monitors ? ?"
date: 2006-06-14
forum: General Help
---

### Post by syxbit on 2006-06-14
hey guys
i installed the ATI drivers as it says in the ati wiki.
my laptop is 1680*1050 (15.4") and the monitor i connect to is 1920*1200.
on windows if the laptop lid is closed then it works (if i open the lid, then obviously the ext. monitor gets the res. of the laptop screen.)
in Ubuntu however nothing i do can get it to change.
in the change res. option, it only goes up to the laptop's max native res.
any ideas ?

---

### Post by syxbit on 2006-06-15
any ideas ?

---

### Post by rado_london on 2006-06-15
I think you have to edit /etc/X11/xorg.conf . There IMO (not tested) add a new monitor with the ext monitors resolution. To find out about it look for dual monitors.

---

### Post by syxbit on 2006-06-16
thanks for the help
the problem is i don't want to use dual monitors.
i want to use both, but not at the same time
when i'm out, the laptop monitor, and when i'm home, i connect it to my external monitor, and want to just use that monitor.
problem is, when i connect to my external monitor, it's set to the resolution that my laptop's screen is set at
any ideas ?

---

### Post by rado_london on 2006-06-16
As far as my knowledge goes you have to specify two monitor in xorg.conf. Each one will have separate settings eg resolution and refresh rate. You can call them screen 0 and screen 1 (I dont know the exact steps which i am sorry for). Then you have to find a way of switching them when using one of the monitors.

I hope this helps. And also I cant beleive that noone of the gurus here came up with an idea.

---

### Post by Bokonon on 2006-06-16
I had a similar problem with nVida 7800GTX and native 1920x1200 external 1600x1200.  

I had to put both settings under my default monitor in xorg.conf and when I boot the laptop only, it comes up in the correct resolution.  When I boot to the external, it comes up in the correct resolution also.

When the laptop is running and I try to 'switch' to the external monitor, I have to restart gdm with a cntl-alt-backspace, but once I do that, it again comes up on the external monitor with the correct resolution.

Not the smoothest solution, but it works for me.

---

### Post by rado_london on 2006-06-16
[QUOTE=Bokonon]I had a similar problem with nVida 7800GTX and native 1920x1200 external 1600x1200.  

I had to put both settings under my default monitor in xorg.conf and when I boot the laptop only, it comes up in the correct resolution.  When I boot to the external, it comes up in the correct resolution also.

When the laptop is running and I try to 'switch' to the external monitor, I have to restart gdm with a cntl-alt-backspace, but once I do that, it again comes up on the external monitor with the correct resolution.

Not the smoothest solution, but it works for me.[/QUOTE]
Would you post your screen settings so syxbit would get the basic idea of what he has to do for the two monitors.

---

### Post by syxbit on 2006-06-18
Bokonon, if you could, your xorg.conf info would be helpful.
that's the one thing that keeps me in windows (as we all know an LCD with anythiing other than native res. looks awful)
thanks

---

### Post by syxbit on 2006-06-24
is there anyone else who's got this working who could post their xorg.conf ?
this is the only thing keeping me from deleting Windows, as it looks horrible when not in native aspect ratio

---

### Post by syxbit on 2006-06-28
well, it too ages, but now with the new ati driver
ati-driver-installer-8.26.18-x86
it works
thanks for trying rado :)

---

### Post by swivelneck on 2006-07-03
[QUOTE=syxbit]is there anyone else who's got this working who could post their xorg.conf ?
this is the only thing keeping me from deleting Windows, as it looks horrible when not in native aspect ratio[/QUOTE]

[QUOTE=syxbit]well, it too ages, but now with the new ati driver
ati-driver-installer-8.26.18-x86
it works
thanks for trying rado :)[/QUOTE]

syxbit,

When you ask for help here, and somebody is willing to help you and asks for YOUR xorg.conf file posted because it's YOUR problem...it may be a good idea to post it, don't you think? 

I mean, why in the world would you need to see anybody's xorg.conf file as we aren't having the problem? I bet that, if you posted your conf here, that somebody ( maybe more than one ) would have been able to help. If you ask for help...be prepaired to answer questions and aid in that help.

I, for one, am tired of the "Thanks anyways" final posts in UbuntuForums. It just means that somebody is asking for a split second answer to their problem and gets frustrated like little children when they don't get it. Usually new users but, we don't care about new users here...we want everybody to have a great experience!

---

