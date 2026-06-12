---
title: "Trying to ENABLE bell in gnome-terminal"
date: 2009-11-19
forum: General Help
---

### Post by Blueshell on 2009-11-19
I can't get the system bell to work in gnome-terminal in Karmic.  Typing ^G or backspace at a blank line does nothing; neither does echo -e '\a' in bash or echo -n '\007' in tcsh.

I know that lots of effort went into silencing the system bell in Karmic, but I really want it---I rarely have anything plugged into my audio-out, and I -need- to hear notifications.

Here's what I've tried (not in this order), along with several logouts, reboots, etc just in case things weren't getting properly reset after each change:

Commented-out the blacklisting of pcskpr in /etc/modprobe.d/blacklist.conf and did modprobe pcspkr.  lsmod shows pcspkr there, and a reboot shows it still there.

Went into alsamixer, raised Beep to 100%, and unmuted it.

Made sure that "Terminal bell" in the profile for my gnome-terminal is checked.  (Also tried unchecking it, from a report elsewhere that claimed the checkbox worked backwards from appearances.)

Installed "beep" with synaptic.  Beep itself works (showing that my hardware is good -and- that the kernel can talk to it), although apparently event0 isn't where my internal speaker is---I have to use beep -e /dev/input/by-path/platform-pcspkr-event-spkr and -then- the command beeps.  (That's actually a symlink to event5 for some reason on this motherboard, an MSI MS-7511 aka a K9N2G Neo-FD.)

Did xset q and noticed that the bell percent was 0.  Did xset b 100 and now it's at 100.

Tried xset b 100 1000 100 to change the default pitch from 400 to 1000; no effect.

Did sudo gconf-editor and drilled down to desktop -> gnome -> peripherals -> keyboard and changed bell_mode from off to on.

(Jeez, how many different places did they stab at to try kill the bell?)

I've also read through about a dozen threads on launchpad where people were complaining about how to turn the bell -off-, as well as [http://ubuntuforums.org/tags.php?tag=bell](http://ubuntuforums.org/tags.php?tag=bell).

So what's left?  I'm suspicious that beep required an explicit path; I wonder if maybe gnome-terminal needs to be informed somehow?  I see bell_custom_file in gconf-editor, but I assume that's if I want the sound card to actually play a sample stored in some file---at this point, even a workaround that called beep with the right arguments would be a step forward, but I suspect that I can't just plug in an arbitrary command & args into that slot.

Help?  Thanks...

---

### Post by Blueshell on 2009-11-19
I just realized this is more general than gnome-terminal---the system bell doesn't work in Emacs, either.  In my much-older installations (Breezy, Hoary, etc), typing ^G to Emacs beeps the system bell.  In Karmic, nothing.

---

### Post by professorYaffle on 2010-01-11
> **Blueshell said:**
> I just realized this is more general than gnome-terminal---the system bell doesn't work in Emacs, either.  In my much-older installations (Breezy, Hoary, etc), typing ^G to Emacs beeps the system bell.  In Karmic, nothing.
I'm starting to upgrade to Karmic and have the same problem. Did you manage to get the bell working eventually?

---

### Post by Blueshell on 2010-01-11
It's possible, but it requires changing several settings, applying a patch, and adding something to your local startup scripts and to your .bashrc, too.  See [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154), comment #50, for the entire procedure (and the enormous rest of thread for what a giant pain the whole issue is---you should add yourself as a "this bug affects me too" (use the link at the very top that says "Does this bug affect you too?") and maybe if enough people do that, the issue will rise upwards in various peoples' priority lists).

---

### Post by rifter on 2010-03-01
> **Blueshell said:**
> It's possible, but it requires changing several settings, applying a patch, and adding something to your local startup scripts and to your .bashrc, too.  See [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154), comment #50, for the entire procedure (and the enormous rest of thread for what a giant pain the whole issue is---you should add yourself as a "this bug affects me too" (use the link at the very top that says "Does this bug affect you too?") and maybe if enough people do that, the issue will rise upwards in various peoples' priority lists).

For people trying to find answers here, the direct link to the aforementioned comment is _[color=blue] [here](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154/comments/50)[/color]_.

This problem is highly annoying to me.  The initial reason for neutering the pc speaker was that besides it being "outdated" you had to grovel through 8 miles of innards to get it to be turned off.  Unfortunately the solution resulted in no beep at all (so much for the "outdated" idea -- if it was outdated to have the pc speaker beep why didn't they make a configurable alert sound take over for it?).  It also means you have to grovel through 8 miles of innards to get it back on again, and even then it's actually a sad string of hacks designed to turn it back on after the bits put in by the bell-killers turn it off.

When I first ran into this, I thought it was a resurrection of an _[color=blue][xterm bug]("http://invisible-island.net/xterm/xterm.log.html#xterm_243")[/color]_ that had plagued me in cygwin (which required me to recompile xterm for that platform), but no such luck.

By the way, a whole other set of directions regarding the bell in ubuntu are [color=blue]_[here]("http://ubuntuforums.org/showthread.php?t=1377990")_[/color].

I've done everything in the bug comment except for patching metacity, and everything in this thread and the other one I referenced except for the bit about changing the bell sound.  What I don't like is that I have to remember to do

xset b 100

every time I boot up because even though it's in my .xinitrc it doesn't happen.  I've put it in my .profile, but that is a hack.  I should be able to configure the x bell with respect to x, using its init files.

What I have not explored yet, is the probability that the bell is still neutered with respect to the computer's state before X is launched, and regular consoles.  Console beeps should work, or at least be configurable in some way.

What would be nice is if you could easily set this without having to grovel through all these places, and whatever you did to do it would undo the things that were done to neuter the bell rather than reacting to them.  What would be even nicer is if you could set the bell sound, too.  It appears that you can, if you dig deep enough, but at this stage I'm still trying to make sure I have the bell turned on in enough places, and I find more places that it is not and more places where my settings are ignored every day.

Applications that don't speak to sound mixers should be allowed to produce pc speaker beeps, as should the kernel itself.  If we are going to try to intercept that, it should be in a way that ensures it will still work, and make both the interception and what we do with it configurable. Likewise, errors made in gui apps and other apps that can speak to the sound mixer should have a configurable sound.

I hope that anyone who is affected by this finds a solution that works for them.  Expect to have to wrestle it awhile, and to have a frustrating time going through all these places.  I did get my beep to work, I just have to keep turning it back on, and I still worry that there are situations in which the beep is still not happening when it should.

---

