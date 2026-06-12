---
title: "Firefox sluggish in Vista"
date: 2009-08-23
forum: General Help
---

### Post by BlackSwordD2 on 2009-08-23
I know this is "Ubuntu forums" not "Vista forums" but honestly windows forums in the past have helped me none.

in a nutshell, Firefox goes from normal smooth and quick internet to sluggish if not completely frozen in Vista while IE flies circles around it. this bothers me quite a lot. in my Ubuntu partition there doesn't seem to be an issue of speed.

I'm running 64bit Vista and i have the most up to date Firefox. not sure if there's a different Firefox that i should be running (such as 32bit or 64bit being as there is a difference for IE).

i can't seem to figure out why it goes to a crawl (usually happens on sites that stream media or while on Facebook)

---

### Post by starcraft.man on 2009-08-23
> **BlackSwordD2 said:**
> I know this is "Ubuntu forums" not "Vista forums" but honestly windows forums in the past have helped me none.

in a nutshell, Firefox goes from normal smooth and quick internet to sluggish if not completely frozen in Vista while IE flies circles around it. this bothers me quite a lot. in my Ubuntu partition there doesn't seem to be an issue of speed.

Sir, I am aghast! The day IE is beating firefox at anything, I shudder.

> I'm running 64bit Vista and i have the most up to date Firefox. not sure if there's a different Firefox that i should be running (such as 32bit or 64bit being as there is a difference for IE).

i can't seem to figure out why it goes to a crawl (usually happens on sites that stream media or while on Facebook)
I run 64 bit vista, no problems. Few pointers.

[LIST=1]
[*]Open up taskmanager and put it in a corner set to processes, sort by mem usage, firefox always at the top. Boo. Use it monitor application.
[*]Open firefox, disable all addons. Restart, see if it slows down again.
[*]If it stops slowing down, selectively enable add ons till ya find the troublemaker.
[*]If persists in slow, even with disabled addons. I suggest ya consider looking at your profile, it may be damaged in some way. It is located in a directory, see [here]("http://support.mozilla.com/en-US/kb/Profiles"). Anyway, copy it somewhere else, then delete it. Close firefox and start again it will generate ya a new profile. If slow down persists. we got something really FUNKAY going down. You can always copy back the profile after deleting the new one and it will go back to using old profile.
[*]If the above didn't work, I'd try uninstalling and reinstalling latest firefox. Try and compare against older 3.0 and 3.6 alpha. If it's still a proble, woah. I'll have to think up more stuff. Might also want to try reinstalling plugins at same time, like flash and java.
[*] Also see the pointer tips [here]("https://help.ubuntu.com/community/Firefox#Custom%20Configuration") in your about:config, good for speeding it up a bit. 
[/LIST]

---

### Post by BlackSwordD2 on 2009-08-23
thanks im gonna go ahead and try those, theres one addon that i haven't used before that may be the culprit

thanks for the tips!

ok knocking out a few of the add-ons deff improves the speed, least for now

the trouble maker seemed to be the Skype plugin

---

### Post by starcraft.man on 2009-08-23
> **BlackSwordD2 said:**
> thanks im gonna go ahead and try those, theres one addon that i haven't used before that may be the culprit

thanks for the tips!

ok knocking out a few of the add-ons deff improves the speed, least for now

the trouble maker seemed to be the Skype plugin

AH HA! Damn it! I should have known that, I had to disable it on my dad's pc to get firefox working. So that's their plan, rather than come up with a good business plan to make money off skype.... they intend to sabotage the worlds firefox browsers! 

Those B#%%$*#&%! It's so brilliant.... well I don't know anyone who'd have thought of it.

/end humour

Ya, skype, delete the plugin ><.

---

