---
title: "Anyway to downgrade from 12.04 back to 10.04?"
date: 2012-04-27
forum: General Help
---

### Post by Demented755 on 2012-04-27
Just finished upgrading to 12.04 and it's just downright horrible. I can't edit anything, themes are all messed up, have tried installing Ubuntu Tweaks and whatnot but nothing works, am getting white backgrounds with white text, and it's just downright impossible to figure out how to fix any of this stuff. 

Are the devs so sadistic that they would release a LTS that cannot be edited in any way?

---

### Post by forrestcupp on 2012-04-27
There are a lot of people who love 12.04 and aren't having problems. You must have some hardware compatibility problems. It's usually wise to try something that's that drastic of a change from a Live CD/USB first.

But unfortunately, there's no way to downgrade. Your best bet is to back up your /home folder and reinstall 10.04 from scratch. You might try installing another desktop environment, like Gnome Shell, Lxde, or Xfce before going to that trouble, though.

---

### Post by QIII on 2012-04-27
> **Demented755 said:**
> Are the devs so sadistic that they would release a LTS that cannot be edited in any way?

No.  Do you think they just sit around figuring out ways to make us miserable?  Do you suppose that all of us are having the same issues?

It would be nice if nobody had issues, but it is an imperfect world.

We're here to help, so if you could give us some details on one issue, we can try to help resolve it.  Sometimes these things are synergistic and one solution knocks out several problems.

Once we get one thing resolved here, start a new thread with the next issue you want to tackle.

---

### Post by Demented755 on 2012-04-27
I did try it from a live CD at first but unfortunately all of these issues had not happened with that.

---

### Post by Vaphell on 2012-04-27
care to elaborate what you mean by 'Are the devs so sadistic that they would release a LTS that cannot be edited in any way?'

also upgrades are more risky and prone to failure than clean install. Usually it works, sometimes it doesn't. Between 10.04 and 12.04 were tons of changes made, for example whole Gnome2 framework out, gnome3 in - Ubuntu team's hand was forced as the Gnome devs abandoned v2 completely. Upgrade literally tries to rip 2/3 of the system out and put completely new parts in place. That is orders of magnitude more complicated than installing from scratch which is nothing more than 'copy few thoroughly tested packages, unpack them to proper places, run few scripts and 20 minutes later call it a day'.
 
Best way to avoid problems with upgrades and reinstalls is to have a dedicated partition for user data and much smaller partition for OS itself. Data partition can be reused between systems with no problem.
Having separate /home is good enough but there is a drawback: different OS versions would overwrite each other's settings in user home and that can lead to instabilities of programs. To overcome that problem some suggest having pure data partition with no user configuration files and not bothering with separate /home - in such a setup home dir would act as nothing more than a config folder.

---

### Post by Demented755 on 2012-04-27
> **QIII said:**
> No.  Do you think they just sit around figuring out ways to make us miserable?  Do you suppose that all of us are having the same issues?

It would be nice if nobody had issues, but it is an imperfect world.

We're here to help, so if you could give us some details on one issue, we can try to help resolve it.  Sometimes these things are synergistic and one solution knocks out several problems.

Once we get one thing resolved here, start a new thread with the next issue you want to tackle.

> **Vaphell said:**
> care to elaborate what you mean by 'Are the devs so sadistic that they would release a LTS that cannot be edited in any way?'

also upgrades are more risky and prone to failure than clean install. Usually it works, sometimes it doesn't. Best way to avoid problems is to have a dedicated partition for user data and much smaller partition for OS itself. Data partition can be reused between systems with no problem.
Having separate /home is good enough but there is a drawback: different OS versions would overwrite each other's settings in user home and that can lead to instabilities of programs. To overcome that problem some suggest having pure data partition with no user configuration files and not bothering with separate /home - in such a setup home dir would act as nothing more than a config folder.

Lets see...there's the issue of not being able to really change themes. I have tried installing tools that were suggested that could let you change themes, but nothing works. I've tried installing Gnome but it's like it's a half assed attempt at the gnome user interface, am getting a bunch of errors but cannot read what they are due to the whole white text on white background thing, desktop text and icons are blurry, cannot move or edit anything on the task bar or even edit the task bar itself, application icons are showing double (one pixelated as hell and one that is just fine), and that's basically what I've found so far. Haven't been able to really do anything since the upgrade finished so I'm not sure about everything that's not working.

I would try backing up all of my files that I need and trying a fresh install rather than the update, but I'm stuck without a way to write DVD's or CD's and no external hard drive that isn't already full of stuff.

---

### Post by QIII on 2012-04-27
Pick one thing.  It's easier that way.

If people stop by a post and see a laundry list, they most often move on.

(By the way, GNOME II is dead.  The GNOME developers dropped it.  That's not Canonical's issue.  Whatever form GNOME has taken is in the bailiwick of the GNOME developers, not Canonical.)

---

### Post by Demented755 on 2012-04-27
Well, it's not just one thing that is making this install nearly impossible to use. If it wasn't a laundry list of issues, I wouldn't be here complaining about it.

Edit: I know Gnome 2 is dead...and that's why I installed 3.4, but what can I say, nothing seems to want to work. Things ran fun for every upgrade up to 11.10, but once I got to 12.04 it's just gone to hell.

---

### Post by QIII on 2012-04-27
I realize you have a bunch of things giving you trouble.

Pick one thing for this thread and we can work through the issue.

It is impossible to try to fix everything at once in a single thread.

---

### Post by forrestcupp on 2012-04-27
> **Demented755 said:**
> Lets see...there's the issue of not being able to really change themes. I have tried installing tools that were suggested that could let you change themes, but nothing works.

I assume you tried going to System Settings and clicking on Appearance? In the bottom right you can change to one of the other pre-installed themes. That should take care of the white on white thing.

Other than that, it sounds like you're not really having problems; you just don't like Unity or Gnome Shell. Maybe you should try installing Lxde or Xfce, and give one of them a try.

And for future reference, you're more likely to get better help if you just ask for it instead of starting off bashing the devs. ;)

---

### Post by Hector23 on 2012-04-27
> **forrestcupp said:**
> It's usually wise to try something that's that drastic of a change from a Live CD/USB first.

That's exactly what I thought!

The first version I came across, which I thought was the standard version was 

ubuntu-12.04-dvd-amd64.iso

instead of:

ubuntu-12.04-desktop-amd64.iso

The DVD version is not listed on the https server. I explained everything here:

[http://ubuntuforums.org/showthread.php?t=1967176](http://ubuntuforums.org/showthread.php?t=1967176)

There apparently is lots of developers on this group as moderators and I don't get a single answer. I did have crap from an idiot, but it was soon erased.

When Ubuntu can't even provide hashes, what's next? Will I have to download the standard version, then, eventually, upgrade from 10.04 ?

Doesn't Shuttleworth understand mirrors might get fed up giving their bandwidth for free to idiots?

---

### Post by Demented755 on 2012-04-27
> **QIII said:**
> I realize you have a bunch of things giving you trouble.

Pick one thing for this thread and we can work through the issue.

It is impossible to try to fix everything at once in a single thread.

> **forrestcupp said:**
> I assume you tried going to System Settings and clicking on Appearance? In the bottom right you can change to one of the other pre-installed themes. That should take care of the white on white thing.

Other than that, it sounds like you're not really having problems; you just don't like Unity or Gnome Shell. Maybe you should try installing Lxde or Xfce, and give one of them a try.

And for future reference, you're more likely to get better help if you just ask for it instead of starting off bashing the devs. ;)Yes, I have tried that, but then I'm either getting a dark gray with black text or off white with white text. 

To me, it seems as if the OS is trying to use both my old theme I had when using 10.04 and the new stuff I'm selecting now.

I'm starting to think something got royally messed up following the directions to upgrade to 12.04 from 10.04. 
Upgrade to 10.10...that's 3 hours gone. Then upgrade to 11.04, another 3 hours, then 10.10...then finally 12.04. It's madness.

---

### Post by mc4man on 2012-04-27
> **Demented755 said:**
> 

I'm starting to think something got royally messed up following the directions to upgrade to 12.04 from 10.04. 
Upgrade to 10.10...that's 3 hours gone. Then upgrade to 11.04, another 3 hours, then 10.10...then finally 12.04. It's madness.
That was a poor path & poor advice to follow.
Maybe you can square up, if it was me I'd copy out anything of value & do a fresh install of what suits you

---

### Post by Demented755 on 2012-04-27
> **mc4man said:**
> That was a poor path & poor advice to follow.
Maybe you can square up, if it was me I'd copy out anything of value & do a fresh install of what suits you
If it's a poor path and poor advice, then it should be removed from the main website. 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Edit: 11.04 to 11.10* Just noticed that typo, but still.

Found an old IDE hard drive that I can back things up to, but for some reason it's not allowing me to back-up the /home folder. I keep getting a bunch of errors.

---

### Post by mc4man on 2012-04-27
That page should be updated, it's 4 months old & doesn't mention 12.04

But it does say this, highlight mine

> To avoid damaging your running system, upgrading should only be done from one release to the next release (e.g. Ubuntu 9.04 to Ubuntu 9.10) [COLOR="Blue"]or from one LTS release to the next[/COLOR] (e.g. Ubuntu 6.06 LTS to Ubuntu 8.04 LTS).

As in 10.04 directly to 12.04

---

### Post by Demented755 on 2012-04-27
> **mc4man said:**
> That page should be updated, it's 4 months old & doesn't mention 12.04

But it does say this, highlight mine



As in 10.04 directly to 12.04
There was no option to do that otherwise I could have. Update manager only showed 10.10, and yes, I did try setting it to LTS only as well as normal releases.

---

### Post by QIII on 2012-04-28
> **Hector23 said:**
> There apparently is lots of developers on this group as moderators ...

Oh?

Your initial post there is two hours old.  Some of us do have lives besides volunteering on this forum.

There is likely some explanation for what you saw.

Just a hint -- when you call people idiots, don't expect much help.

And don't hijack someone else's thread.  Demented755 has his hands full and he's understandably pissed off, but at least he's acting like he realizes someone is trying to help.  Please let him have the floor, as you expect in your thread.

Someone will come by your thread to help.  Remember that we are all volunteers, we live around the world and no one person has an answer to every question.

---

### Post by mc4man on 2012-04-28
> **Demented755 said:**
> 
Found an old IDE hard drive that I can back things up to, but for some reason it's not allowing me to back-up the /home folder. I keep getting a bunch of errors.
Post up the errors, I'm sure people can help you.

I would only copy out my files & possibly a few others, most of the rest aren't of any value at this point. May take a bit longer to pick thru for value but no sense putting back compromised config type files anyway

---

### Post by QIII on 2012-04-28
Yes, do give the errors. But generally, Demented, I tell people that the "Blast off and nuke 'em from orbit" is not a good first attempt.  In this case, since we really can't reconstruct what happened, it might be the only option left, unfortunately.

But I have one other suggestion before we go there.

> **Demented755 said:**
> Yes, I have tried that, but then I'm either  getting a dark gray with black text or off white with white  text.

Are other colors otherwise rendered properly?

Can you see your way to post us a screen shot?

We may also be able to have you install the Gnome Color Chooser and see if we can at least get you text visible enough that we can see what else is going on.

---

### Post by mc4man on 2012-04-28
Just out of curiosity - 
Have you tried creating a new user, logging into it & seeing if things work better?

---

### Post by Demented755 on 2012-04-28
> **QIII said:**
> Yes, do give the errors. But generally, Demented, I tell people that the "Blast off and nuke 'em from orbit" is not a good first attempt.  In this case, since we really can't reconstruct what happened, it might be the only option left, unfortunately.

But I have one other suggestion before we go there.



Are other colors otherwise rendered properly?

Can you see your way to post us a screen shot?

We may also be able to have you install the Gnome Color Chooser and see if we can at least get you text visible enough that we can see what else is going on.
The colors render properly unless I'm logged in with Unity and try changing things with MyUnity, then the text renders like you're looking at a 3D image without 3D glasses. 

The print screen shortcut isn't working and I just tried the screenshot tool in GIMP which isn't working either. 

I will try the new user idea right now.

---

### Post by Demented755 on 2012-04-28
Creating a new user account and logging in with that slightly fixes the theme issues. Am no longer getting the odd colors, but that just created a new issue where the text starts scrambling like it's CRT fuzz.

---

### Post by QIII on 2012-04-28
So, it still sounds like text is an issue (I realize there are still others, but let's try to nail that one down.)

I'm going to hunt around a bit on that.

Did you have a proprietary graphics driver installed during the upgrade process, or did you un-install it before you started upgrading.

Edit:  Still searching for diagnostic courses of action, but here is one:  Try checking out your font rendering settings.

Another edit:  I'm probably going to have a wild grandchild showing up shortly and my have to shut down.  Don't take it as a snub.  There will be others getting home from work and stuff as the world spins, so stand by.

---

### Post by Demented755 on 2012-04-28
Installed during. 
I'm just backing up all that I can and am going to reinstall 10.04. 12.04 is just turning out to not be worth the hassle to me. Unity doesn't want to work right, Gnome doesn't want to work right, Xlde doesn't want to work right...

I'm just at a loss because everything worked wonderfully on 10.04, 10.10, 11.04, and 11.10. It's already bad enough I wasted 10 hours going through that mess, but now I've got to back up and copy over 460gb of CAD files and other stuff. Fun...

---

### Post by QIII on 2012-04-28
Leaving the graphics drivers installed during an upgrade (as opposed to a fresh install) is almost a sure ticket to problems.

If you are going to back up and reinstall -- and you can stomach the time -- might it not be worth going forward rather than back?

If Unity is a pain (I can't say how much I really don't like it, personally.  But that is just my opinion and doesn't mean it's bad.), you might try Kubuntu (KDE has really improved) or Xubuntu.  I haven't played much with Lubuntu, but I did used Lxde a few years ago on a DSL install.

Gnome is troublesome for me on this machine because it has ATI cards and Gnome doesn't work well with them right now.  The Gnome developers are trying to juggle cats right now and have their hands full trying to nail down what I think will be a good product in the end.

---

### Post by Demented755 on 2012-04-28
I've just got simple onboard graphics that are recognized by Ubuntu straight away, so I doubt that's been the problem. 

10.04 worked, so going back to it seems like the logical option to me. I can't really stomach the time since this is going on 3 days now that I've lost working on this mess, but I have no other option. I probably never should have upgraded in the first place, but everything worked just fine when trying a live CD of 12.04.

Unity is a big pain and that's part of my issues since it's not allowing me to do things that I need, but I could get around that if it wasn't for all of these other issues. Gnome and Gnome classic are even having the same issues.

---

### Post by poonjabi on 2012-04-28
> **Demented755 said:**
> I've just got simple onboard graphics that are recognized by Ubuntu straight away, so I doubt that's been the problem. 

10.04 worked, so going back to it seems like the logical option to me. I can't really stomach the time since this is going on 3 days now that I've lost working on this mess, but I have no other option. I probably never should have upgraded in the first place, but everything worked just fine when trying a live CD of 12.04.

Unity is a big pain and that's part of my issues since it's not allowing me to do things that I need, but I could get around that if it wasn't for all of these other issues. Gnome and Gnome classic are even having the same issues.

You really should switch to something like LMDE and pure debian, and then you never have to go through this again. I feel bad for you man, but I am loving 12.04 in Fallback session. Faster, better, in my opinion.

---

### Post by QIII on 2012-04-28
Kubuntu and Xubuntu have given me no trouble at all.

I just upgraded (not fresh install) a Kubuntu machine this evening without any problems.

I'm not telling you not to go back (except that EOL end of support leaves you out in the cold next year).  But it would be a shame if we couldn't help you go forward.

---

### Post by Demented755 on 2012-04-28
> **poonjabi said:**
> You really should switch to something like LMDE and pure debian, and then you never have to go through this again. I feel bad for you man, but I am loving 12.04 in Fallback session. Faster, better, in my opinion.
It's been lagging and slower for me unfortunately.

> **QIII said:**
> Kubuntu and Xubuntu have given me no trouble at all.

I just upgraded (not fresh install) a Kubuntu machine this evening without any problems.

I'm not telling you not to go back (except that when support runs out you may find yourself out in the cold).  But it would be a shame if we couldn't help you go forward.
Going backwards is forwards in my position, at least for the time being.

---

### Post by xyzzyman on 2012-04-28
I'm not going to add anything in regards about downgrading, etc... Only than I'm amazed this thread has gotten this long without someone pointing out that data should be been backed up BEFORE doing upgrades. Just adding that as a reminder for any newbie who may read this thread later. And if your data is THAT important should have had a backup anyways even without upgrading.

---

### Post by OpenSourceRules on 2012-04-28
My humble suggestion: USB sticks are ubiquitous, so you may store your information onto USB sticks.  
Yep, different DE (Desktop Environment) often changes something.

---

### Post by zombifier25 on 2012-04-28
Are you using an external theme? That might be the problem.

---

### Post by 3togo on 2012-04-28
It sounds stupid to downgrade but if u insist, you could try
1) sudo sed -i s'precise//oneiric/g' /etc/apt/sources.list
2) sudo apt-get remove x11-common --force-yes -y
3) sudo apt-get update && sudo apt-get dist-upgrade

It will downgrade most of your desktop software to oneiric which should suffice your request.

---

### Post by Demented755 on 2012-04-28
> **xyzzyman said:**
> I'm not going to add anything in regards about downgrading, etc... Only than I'm amazed this thread has gotten this long without someone pointing out that data should be been backed up BEFORE doing upgrades. Just adding that as a reminder for any newbie who may read this thread later. And if your data is THAT important should have had a backup anyways even without upgrading.
I've yet to loose any files when upgrading distros in I don't know how many years.
> **zombifier25 said:**
> Are you using an external theme? That might be the problem.
I was using one of the stock themes from 10.04.

Back on 10.04 now though and everything is working just fine. I'll probably try installing a clean install of 12.04 on another HD sometime later and see if I get the same issues.

---

### Post by xyzzyman on 2012-04-28
> **Demented755 said:**
> I've yet to loose any files when upgrading distros in I don't know how many years.


I've never had a loose file. Mine are pretty tight. Never lost one either 'cept from own stupidity, but any time spent in the +1 beta forums for Ubuntu knows that it does happen to people or any OS for that matter.

---

