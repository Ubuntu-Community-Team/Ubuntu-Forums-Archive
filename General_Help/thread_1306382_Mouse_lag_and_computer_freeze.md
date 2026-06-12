---
title: "Mouse lag and computer freeze"
date: 2009-10-30
forum: General Help
---

### Post by Kazur on 2009-10-30
I upgraded to 9.10 from 9.04 today, but I have the following problems:

1. The mouse lags when I press any key on the keyboard. For example, if I type a letter, while moving the mouse, the mouse stops for about a second. The same is for any keyboard shortcut.

2. From time to time, everything just freezes, and I have to turn off the computer holding down the power button. One of the times, I was watching south park, and I heard "From your, from your, from your, from your..." just like when playing old scratched cds. I could move the mouse, but nothing else worked.

Both of these are really annoying, and I hope there's a solution. I've been using Ubuntu since 6.04 and never experienced any problems of this kind. Thanks.

---

### Post by phamnewan on 2009-11-01
Mouse lag has been significant for me.  This is especially when using wine apps.  Lag can last for several seconds.  9.04 had no such issue and the only change was the upgrade to 9.10.  My laptop has also had the same thing, but to a much lesser degree.

---

### Post by Mechaphoenix25 on 2009-11-08
I'm having the same 2 issues, on an Inspiron 1501 laptop with ATI graphics, clean install of ubuntu 9.10.  I've been using Ubuntu since 7.04, the random crashing has been gone since I switched to free ATI drivers, but it's back now.  Also, the mouse lag is not due to compiz, and happens even when it's off.  It also only happens when using my trackpad, my trackball (Logitech Trackman, wired) does not experience the lag.  My theory is the issue is due to the touchpad drivers being run in userspace rather than kernel space, but I don't know anything about how it's configured, since xorg.conf no longer has an entry for the touchpad.

Any help would be appreciated.

---

### Post by phamnewan on 2009-11-09
To prove out that it is not hardware related I have booted to older version (9.04) and it runs fine.  If I boot to 9.10 then the problem is back.

Clearly related to portions very specific to the upgrade because older software was removed in the upgrade.  Booting older kernel shows an odd blend of 9.04 and 9.10, but it still works (except sound isn't working now in the 9.04)...

What in 9.10 would cause this issue?

---

### Post by Aemaeth on 2009-11-09
I was having this same issue whenever i was runnign firefox or transmission. did a package upgrade today and all seems to be well

try

sudo apt-get update

then 

sudo aptitude safe-upgrade

Cheers!

---

### Post by Mechaphoenix25 on 2009-11-17
HAHAHAHAHAHAH! found the solution to the mouse lag issue, boy do I feel dumb.  The default in 9.10 is to disable touchpad movement while typing, which is why I didn't see a delay on my trackball.  You can fix this by using gconf-editor and changing the value in
/-->desktop-->gnome-->peripherals-->touchpad-->disable_while_typing
to false.  If it's not there, install gsynaptics and run it once to create it.  Enjoy your now lag-free touchpad gentlemen, sometimes it's just that simple.

Still no word on the random crashes, they appear to be memory-corruption-on-suspend related on my machine at least.

---

### Post by Kazur on 2009-11-22
I don't have the freezing issue anymore, and I don't know what fixed it.

But I still have the mouse lag problem. I tried to deselect the disable_while_typing, but it's still laggy. Anyone else with this problem, or a solution to it?

---

### Post by Kazur on 2009-11-22
Ok, so now the problem seems to be fixed. I don't know exactly what did it, but I've removed **a lot** of packages.

I searched for "mouse", "keyboard", "key", "input", "pad", "trackpad" "auto" and more input/mouse/keyboard-related words and removed a lot of packages. Now the lag seems to be gone. I also removed gnome-do, but I have no idea if that was related to the lag. Just wanted to tell you all, in case anyone else ever experiences the same thing again.

:)

---

### Post by reeboker on 2009-11-22
Weel looks that I'm not in the freezing issue alone, sadly. Seems to me that where there are running lot of processes the system freezes, that's only one explanation of which I could think of. Because on my machine, compiz is disabled (now), and when I re-enable it, this freezing thingie buggie is occuring more then with the compiz disabled. Or it's just random, really don't know. Somedays it could happen twice or three times, and on the other hand, doesn't happen at all. Would be nice to see some official-helpfull explanation here. :|

---

### Post by exoticorn on 2009-11-27
For your reference:
Disabling the mouse while typing is caused by the "mouseemu" package.
You can remove it with "sudo aptitude remove mouseemu" to solve this issue, or you can try to figure out how to switch off this feature without removing the whole package.

---

### Post by morisila.ardiel on 2009-12-24
> **reeboker said:**
> Weel looks that I'm not in the freezing issue alone, sadly. Seems to me that where there are running lot of processes the system freezes, that's only one explanation of which I could think of.

My desktop freezes just starting up. The login screen has been known to freeze. Just a random observation, but mine seems to freeze when I'm doing *less*

---

### Post by m4lte on 2010-01-04
> **Mechaphoenix25 said:**
> HAHAHAHAHAHAH! found the solution to the mouse lag issue, boy do I feel dumb.  The default in 9.10 is to disable touchpad movement while typing, which is why I didn't see a delay on my trackball.  You can fix this by using gconf-editor and changing the value in
/-->desktop-->gnome-->peripherals-->touchpad-->disable_while_typing
to false.  If it's not there, install gsynaptics and run it once to create it.  Enjoy your now lag-free touchpad gentlemen, sometimes it's just that simple.

This solved the problem for me. thanks a lot!!

---

### Post by widda on 2010-03-05
Since upgrading from jaunty to karmic, gnome - the mouse!
If I click on a link or an arrow or anything at all, it doesn't activate till I move the cursor OFF where I clicked. That seems to be speed issue?

BUT, it's worse when I've opened a dropdown, cos if I move too soon, menu disappears and its back to the arrow for me. grr can be 3 times.
And overall, also a general slowdown in file system.
 
Tried xfce etc desktops in case my 512Mb was struggling with Karmic, but they're possibly even worse.
I changed to a Xubuntu flavour somewhere in there, didnt seem to affect problem either way.
Tho I'm not at all sure anymore what or why is xubuntu lol. 
Lightweight maybe.
I could clean reinstall 9.04 I guess from the disc, but it seems that 512mb is though to be adequate.
will try safe upgrade?

---

### Post by maddg3241 on 2010-03-05
xubuntu is better for older computers if you have an older one

---

### Post by tonytraductor on 2010-07-15
I am having random system freezes with 9.10 (netbook-remix install, but using xubuntu-desktop/xfce, not gnome with that nauseating, bloated netbook-remix interface).
Oddly, I don't seem to be having any "mouse" lag (with touchpad).
Just, the system randomly freezes.
Mostly the entire desktop seems frozen (nothing moving, no response to keyboard or touchpad/mouse).
Once, however, once, with xfce4-sysmon running, lost response to keyboard+mouse, but I could still see the sysmon tracking cpu and mem use on the graph...weird.
Also rather odd, I can not identify any specific event or reason for these freezes.  They even seem to occur frequently when cpu/mem usage is not remarkably high, or, even, when such use is quite low, indeed.

I tried to upgrade the system to 10.04, but freezes during the upgrade were troublesome.  I eventually got the system fully updated, but 10.04 gave me a whole world of headaches I won't discuss on this thread, so I returned to 9.10 (yes, the system freezes, being the only issue I'm having with 9.10, are much more tolerable than the whole legion of issues in 10.04).

This 9.10 is a fresh install from a usbkey, and was updated fully. (froze during that update, but I restarted it and did dpkg --configure -a, etc., to complete and correct any issues there).

The machine previously had hardy/8.04 on it, and ran rather nicely (with the exception that wifi was fickle, whereas in 9.10 said wifi functions flawlessly).

Sometimes it runs for several hours with no problem, with relatively heavy loads (google-chrome, exaile player, etc.).
Other times, it's on for 5 minutes, and chokes when I'm doing absolutely nothing.

Would posting dmesg | less or something be useful?

---

### Post by gabaS on 2010-07-17
Are you using Ubuntu One?
Ever since i'm using Ubuntu One on Karmic i have these freezes discussed above, no respond to any input, even the clock stops at the minute.

I have no idea what else i've changed than using Ubuntu One, but on the other hand on my 10.4 netbook remix everthing is fine. 

I will disable it and test if these freeses still occur.

Cheers

---

