---
title: "random cut and paste"
date: 2010-07-01
forum: General Help
---

### Post by SuizenJen on 2010-07-01
Hi. I have googled this a bit and am coming up with naught. Heres the deal.

Im running netbook remix on a eeepc 1005ha. It is my only OS and Im loving it except for one obnoxious quirk. 

It randomly cuts text and randomly pastes it. If there is something in the clipboard, it will usually paste that, but just as often it will cut random text and paste that.

The pastes occur when the cursor focus jumps back to the location of the cursor on the screen. I dont know a better way to phrase that, but thats what it is doing. Say... I put the cursor over the word "pastes" in the paragraph above... even though Im typing in this paragraph, the focus will "jump" to the cursors physical locale (the word "pastes") and then paste whatever is in the clipboard. If the cursor is outside of the textbox, the page will jump to the bottom.

This behavior occurs across programs and in *any* place text can be entered.

I can find no rhyme or reason for it... it just... happens. Sometimes even when Im away from my computer, so its not like Im hitting some key on accident.

I have loved everything about this ubuntu distro, but this issue is just toany obnoxious. Writing psych papers on this thing is going to be near impossible if I dont get this fixed before I go back to school.

Thanks for your help!

Jen

---

### Post by bobcollard on 2010-07-01
You may have two things going on here.  The jumping around you are speaking of may be due to your touch pad being brushed by a thumb while typing.  The other thing is what I discovered, if you copy text from something like a browser and close the browser the text is no longer in the clipboard.  This seems to be a Linux thing in all the distros I've tested.  I never had it in Windows or Apple systems.

---

### Post by SuizenJen on 2010-07-01
Thanks.

I considered at first that it might be a touchpad bump, but it does it when I am not typing as well, even off in another room.

I dont have to manually copy or paste nor does it give any indication that it is doing either task, until text-vomit pops up on my screen absolutely nowhere near where I am typing.... The text is usually cut from something I typed earlier in the same post or paper, but I have gone to do a google search or type in a URL and it has pasted there as well. 

There HAS to be a reason for this and a way to turn it off. :(

Jen

---

### Post by bobcollard on 2010-07-01
> **SuizenJen said:**
> Thanks.

I considered at first that it might be a touchpad bump, but it does it when I am not typing as well, even off in another room.

I dont have to manually copy or paste nor does it give any indication that it is doing either task, until text-vomit pops up on my screen absolutely nowhere near where I am typing.... The text is usually cut from something I typed earlier in the same post or paper, but I have gone to do a google search or type in a URL and it has pasted there as well. 

There HAS to be a reason for this and a way to turn it off. :(

Jen
Sounds like Gremlins, sorry, a little humor.  Do you have Clipman running in your Panel?  I never had much luck with it.  It is a way to control your clipboard.

---

### Post by Carloshz on 2010-07-05
I've been doing research on this, but I've yet to find a solution. The same thing happens to me on my EEEPC 1005HAB. The top right section of the touchpad is fixed so that if you tap it, it pastes automatically.

If anyone's got a fix, lemme know!

---

### Post by SuizenJen on 2010-07-11
I havent been able to intentionally replicate my random cuts of random text or the pastes that occur when Im not typing, but it looks like Carloshz found one of the big issues. 

The touchpad is so close to the keyboard that it is easy to brush it while hitting space, even when trying NOT to... and the paste function requires only the tiniest tap on the uppermost edge of the pad to paste. 

Ive tried to turn off the mouse while typing, using the bundled mouse preferences software, but that doesnt fix it.

As big of a kludge as it might be, I might try a strip of electrical tape across the upper mouse edge and see what that does.


Jen.

---

### Post by bobcollard on 2010-07-11
> **SuizenJen said:**
> I havent been able to intentionally replicate my random cuts of random text or the pastes that occur when Im not typing, but it looks like Carloshz found one of the big issues. 

The touchpad is so close to the keyboard that it is easy to brush it while hitting space, even when trying NOT to... and the paste function requires only the tiniest tap on the uppermost edge of the pad to paste. 

Ive tried to turn off the mouse while typing, using the bundled mouse preferences software, but that doesnt fix it.

As big of a kludge as it might be, I might try a strip of electrical tape across the upper mouse edge and see what that does.


Jen.
Install gpointing-device-settings with either Synaptic Package Manager or Terminal.  You can start the applet with either Application Startup, Terminal or Alt F2 (Run Program)

---

### Post by IceDoE on 2010-07-22
I haven't attempted the solution you suggest yet, but to help clarify a few things:
I've been working on this problem and searching for a solution for about a month now myself, heres is a bit better idea of what is going on.

Wherever your cursor is currently will be selected for a past of something randomly copied somewhere you have been or typed. The length is usually not especially long, but it can be up to several lines. If, for instance, you are typing in a text field with a place holder, it will change your place as well to wherever the cursor is periodically (thus upsetting your typing).

While you continuously type and a decent speed you should not have this problem, or not as often, depending on your settings. If you stall up for even a very brief time (and I mean less than a second here) it may decide to paste something. 

It does not matter what program is being used (Firefox, Tomboy Notes, Chrome, Empathy, etc) though I haven't seen it in terminal yet.

---

### Post by RJARRRPCGP on 2010-07-22
> **bobcollard said:**
> if you copy text from something like a browser and close the browser the text is no longer in the clipboard. 

I don't like that! I wanted text to stay in the clipboard when I close an application I don't need at that moment! 

Windows don't have that quirk. :(

---

### Post by bobcollard on 2010-07-22
> **RJARRRPCGP said:**
> I don't like that! I wanted text to stay in the clipboard when I close an application I don't need at that moment! 

Windows don't have that quirk. :(
Try clipman, it keeps things as long as you want them.  Right click your panel and Add it to the panel, then configure it.

---

### Post by IceDoE on 2010-07-26
So I tried the solution you suggested but no dice. It did seem to help scrolling around a bit maybe, but still the weird random copy/cut and pasting.

---

### Post by SuizenJen on 2010-08-08
I tried the proposed solution too and gave it a while, messing with settings, to see if I could get it. It helps, but a cure it is NOT.

---

### Post by SuizenJen on 2010-08-09
Couldnt stand it anymore. Ended up kludging it with some tape over the very uppermost part of the pad. Inelegant but better than nothing.

Jen

---

### Post by IceDoE on 2010-08-10
Disabling Tap to click seems to have helped.

A bit annoying as I liked being able to tap the touchpad to click, but better than random cut and pastes. Not sure why it randomly simulates a middle click though...

---

### Post by paolo lim on 2010-09-07
am having the exact same problem. hope someone can provide a fix. :(

---

### Post by SuizenJen on 2010-09-11
Got my touchpad back! The solution to the nightmare? I switched distros. Puppeee Linux, the eeepc dialed version of Puppy linux, is super light, crazy fast and does everything I need... 

Its not as pretty as ubuntu, but it works really good and my mouse doesnt have random bouts of idiocy while Im trying to write. 

Bummer, because I like ubuntu. Just not enough to put up with that nonsense anymore.

---

### Post by japs_it88 on 2010-10-17
I don't have the problem myself, but i know who does and did some research.

I think it might help if, on Kubuntu, you go to the Touchpad Settings (Alt+F2 touchpad) and in the tapping tab, you link all unwanted corner tapping events to None.

Hope it helps.

---

### Post by Dittothat on 2011-01-19
Has there been any progress on this issue? I too have the problem and wonder if there are any fixes other than electrical tape. I have tried the various suggestions in this forum without luck. Next step will be changing distros.

Thanks.

---

### Post by djxcon on 2012-09-18
Same issue on EEEPC 1001PX. I tried changing Window Managers from Gnome, to Gnome Classic, to LXDE, to XFCE....all have the same problem.

---

### Post by djxcon on 2012-09-18
Has anyone tried this to see if it still works? it was written in 2010.

[http://ubuntuforums.org/showthread.php?t=1602226]("http://ubuntuforums.org/showthread.php?t=1602226")

---

### Post by nothingspecial on 2012-09-18
Hi,

Please start a new thread. This one is old.

---

