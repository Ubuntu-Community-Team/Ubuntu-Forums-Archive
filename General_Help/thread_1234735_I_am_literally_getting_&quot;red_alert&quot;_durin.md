---
title: "I am literally getting &quot;red alert&quot; during Boot/Startup"
date: 2009-08-08
forum: General Help
---

### Post by Jerriy on 2009-08-08
As the booting info is beginning to scroll up on the screen (with the usual white letter-font on black background) with each line preceded by a star-key/asterisk, I noticed that recently among those there is a line with a red-cololred asterisk:```
[COLOR="Red"]*[/COLOR] Firewall disabled via /etc/default/firehol
```Using ctrl-q I noticed that the line previous to that is:```
* Skip starting Firewall: ufw (not enabled)
```So the question is: what happened? See I don't remember disabling (or enabling, or for that matter even noticing the existense of a) firewall in Ubuntu. The timing suggests that this started to happen sometime after I upgraded to Jaunty. Does this mean I need to have a firewall now?i.e. get the so called firestarter package? Cuz I don't see "System &#9656; Administration &#9656; Firestarter" in my menu.

---

### Post by Jerriy on 2009-08-08
Again my suspicion is that one of the jaunty-based programs I recently installed must have slipped in this message onto the startup. This made me thinking: does ubuntu need a firewall? Isn't firewall a "winduz floatation-device"?

---

### Post by Sidewinder1 on 2009-08-08
Ubuntu has all ports closed by default; I guess it opens them as needed. If you're not noticing any other strange behaviour in networking or with any other programs, you can probably just ignore those messages.
Side

---

### Post by Jerriy on 2009-08-08
I also have another problem that I noticed began to appear recently (after Jaunty): when it's time to update software (i.e. when the Update Manager shows-up) some of the available updates can't be performed! I can't click on the box to the left of some of the newly available updates, while the other available updates are already clicked-on by default and I have the option of clicking them off if I want to)

I noticed that these are under the "Distribution updates" catagory:

---

### Post by Jerriy on 2009-08-08
> **Sidewinder1 said:**
> Ubuntu has all ports closed by default; I guess it opens them as needed. If you're not noticing any other strange behaviour in networking or with any other programs, you can probably just ignore those messages.
SideThanks for your reply. I don't know whether this is a network-problem or not but I noticed further down on the boot-scrolling screen the following:```
* Starting network connection manager
nm-system-settings: SCPlugin-Ifupdown: device added (udi: /org/freedesktop/hal/devices/... [bla bla bla]): **not well known**
```Should I ignore that or is that as you said a "network problem"?

---

### Post by Sidewinder1 on 2009-08-08
> **Jerriy said:**
> I also have another problem that I noticed began to appear recently (after Jaunty): when it's time to update software (i.e. when the Update Manager shows-up) some of the available updates can't be performed! I can't click on the box to the left of some of the newly available updates, while the other available updates are already clicked-on by default and I have the option of clicking them off if I want to)

I noticed that these are under the "Distribution updates" catagory:

Check out the last listing in the first post in the link below, it may be what you're experiencing:
[http://ubuntuforums.org/showthread.php?t=1145967](http://ubuntuforums.org/showthread.php?t=1145967)

Re the boot messages, I'm more like an Ostrage with head in the sand. I have them set to not display during boot. I figure if anything is really wrong, I'll discover it on a program by program basis. That, however is not everyone's style. :-)
Side

---

### Post by Jerriy on 2009-08-08
> **Sidewinder1 said:**
> Re the boot messages, I'm more like an Ostrage with head in the sand. I have them set to not display during boot. I figure if anything is really wrong, I'll discover it on a program by program basis. That, however is not everyone's style. :-)Well that's one way of looking at it. Btw in my case it that IS already happening: I AM discovering and encountering problems, like for example a half-disabled Upgrade Manager

> Check out the last listing in the first post in the link below, it may be what you're experiencing:
[http://ubuntuforums.org/showthread.php?t=1145967](http://ubuntuforums.org/showthread.php?t=1145967)Tried the fix but nope - Distribution updates are still disabled (and can't be enabled):

---

### Post by Sidewinder1 on 2009-08-08
Odd...Perhaps someone more knowledgeable would be so kind as to chime in. Looks like a KDE display; are you running kubuntu or ubuntu with some KDE programs installed? It shouldn't make much difference but who knows? The more info. you can provide the better. Sorry I wasn't of more help... :-(
Side

---

### Post by 3rdalbum on 2009-08-08
If you don't have any services listening on incoming ports, then you don't need a firewall. This is true of any version of Ubuntu.

Don't worry about the error message.

If you don't already have a firewall in your broadband router, and you want to configure a personal firewall on your Ubuntu machine, I recommend gUFW instead of Firestarter.

---

### Post by 3rdalbum on 2009-08-08
> **Jerriy said:**
> Well that's one way of looking at it. Btw in my case it that IS already happening: I AM discovering and encountering problems, like for example a half-disabled Upgrade Manager

Tried the fix but nope - Distribution updates are still disabled (and can't be enabled):

It's not so much that "distribution updates are disabled" as "those two updates are disabled". This usually indicates a dependency problem of some sort, but sometimes you can upgrade those packages in Synaptic Package Manager without problems.

---

### Post by Jerriy on 2009-08-08
I think you might be on to something, Sidewinder1. I am not sure as to what on the jaunted earth is going on but apparently things are complicated in the ku-/ubuntu world: i used for example Amarok and apparently that thing is a kubuntu thing and as a result of my upgrade to Jaunty, Amarok and/or KDE have been doing funny things like clogging my memory and slowing down my computer - I've noticed them up there high on the Memory Process list (like "kded4" and "knotify4" and kglobalaccel, klauncher, kdeinit4... etc) visible right there in the System Monitor!

But I am a Ubuntu user. Never run kubuntu ever! You reckon that is what's causing the "Update Manager" problem?

---

### Post by Jerriy on 2009-08-08
> **3rdalbum said:**
> If you don't have any services listening on incoming ports, then you don't need a firewall. This is true of any version of Ubuntu.

Don't worry about the error message.

If you don't already have a firewall in your broadband router, and you want to configure a personal firewall on your Ubuntu machine, I recommend gUFW instead of Firestarter.Thanks for the heads-up on the firewall thing!

---

### Post by Jerriy on 2009-08-08
> **3rdalbum said:**
> sometimes you can upgrade those packages in Synaptic Package Manager without problems.So you mean I have to start manually updating my installations? Is that a "normal" way of doing things in Jaunty?

> It's not so much that "distribution updates are disabled" as "those two updates are disabled". This usually indicates a dependency problem of some sort,Meaning what? A "software source" problem?

---

### Post by Sidewinder1 on 2009-08-08
Unless you're using some KDE apps that you can't live without, why not try going into Synaptic and removing KDE? You can always reinstall...I'm running Ubuntu, as are you and installed alot of KDE apps that I never use. When my disk starts getting full I plan on deleting KDE.

---

### Post by Jerriy on 2009-08-08
No, as far as I know there are no KDE aps that I can't live without. Before upgrading to Jaunty I used to play stuff on Amarok but now I don't cuz apparently, an upgrade to Jaunty amounts to a downgrade of Amarok. A while back I started a question on this very subject of the Amarok/Jaunty conundrum but [[COLOR="RoyalBlue"]that thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7641352") seems to have been memoryholed.

---

