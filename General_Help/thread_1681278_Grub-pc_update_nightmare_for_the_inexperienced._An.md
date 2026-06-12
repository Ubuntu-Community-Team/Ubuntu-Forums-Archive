---
title: "Grub-pc update nightmare for the inexperienced. Any suggestions?"
date: 2011-02-03
forum: General Help
---

### Post by Kir_B on 2011-02-03
Hey all.

I'm running Ubuntu 10.04LTS, which I installed just over a month ago, from the 10.04.1 maintenance release livecd. This is a brand new PC and I'm not dual booting.

I've just done an update via the &quot;update manager&quot; and following the security and normal package updates, I'm greeted with the following message to do with grub-pc (and I believe grub-common is also being updated).

> Configuring grub-pc
 -------------------
 
A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified.

 1. install the package maintainer's version
 2. keep the local version currently installed
 3. show the differences between the versions
 4. show a side-by-side difference between the versions
 5. show a 3-way difference between available versions
 6. do a 3-way merge between available versions (experimental)
 7. start a new shell to examine the situation

What do you want to do about modified configuration file grub?I'm not sure why I'm getting this message, as I've yet to change anything to do with grub and the only alterations I've made so far, are adding some of my favorite applications, changing the theme, wallpaper, added codecs, fonts, Etc..... Definitely nothing to do with any configuration files.

I'm a little reluctant to proceed without a little advice, as the last time I encountered something similar, I encountered a nightmare getting my system to boot again. The other reason for asking for advice, is so that other newbies encountering this might be able to find an answer to this issue.

Thank you all for any input you might have.

Kirby

---

### Post by Kir_B on 2011-02-04
WOW! Have I stumped the community?

If anyone has dealt with this, or has any idea how I should proceed, I'd really, really appreciate the input, as I'd like to finish this update before nature throws another power outage my way.

Thanks in advance. ](*,) Kirby ](*,)

---

### Post by Quackers on 2011-02-04
If you have edited your previous /etc/default/grub file (for example the grub timeout, or including a splash image, or deleting the Memtest entries) you are being given the choice to keep those changes, or have a new and updated version. If you elect to have the new one, any changes you have made will need to be done again.

---

### Post by Rubi1200 on 2011-02-04
Exactly as Quackers said; you are offered these choices because you probably made changes to GRUB configuration files.

I haven't tested all the options, but > 2. keep the local version currently installeddid exactly that.

---

### Post by oldfred on 2011-02-04
If you keep the local version, it will not update the menu with the new kernels it you have a new kernel downloaded. sudo udpate-grub should then find that if it still boots with the old kernel. Otherwise you have to manually edit the grub line in the grub menu.

I found it is best to separately backup any edited system files so I know what changes I made and accept the maintainers version. I have had too many times where the new version was so different, it created more issues than any problems I would have in re-editing a file.

---

### Post by Kir_B on 2011-02-04
Thanks for the response Quackers.

Thats the funny part, I haven't changed a thing yet, but at some point I will get around to that.

I take it, that for me, being that I haven't changed a thing, I really shouldn't even be seeing this and that it should have just automatically chosen #**1, install the package maintainer's version.** The reason that I say that, is that being a complete newbie just over a year ago, these kinds of questions can be a little intimidating and also, can be quite confusing for the people new to Ubuntu, especially without a proper explanation, any meaningful safe suggested course of action, or any documentation concerning this circumstance to be found anywhere. 

This is another one of those "paper cuts" that are keeping Ubuntu from being accepted into the mainstream, as a real alternative to the criminal Micro$oft monopoly. I for one, look forward to the day that I don't see these types of things anymore, so that I can begin to recommend it to everyone I meet, instead of telling everyone how great it is and then followed by having to tell them that it's not for everyone, because you need to be very patient, willing to learn (not that everyone shouldn't already be), willing to spend hours reading, be good at Google searching, be willing to ask questions on a forum and be willing to fix your operating system when you've somehow done something wrong, or it's broken itself for seemingly no reason. Phew, that was a mouthful.

Don't get me wrong, I really don't want anyone to think that I'm ungrateful, because that's definitely not the case and in fact, quite the opposite. I love Ubuntu, FOSS and the wonderful community that surrounds it, but I'm afraid that I have got to find an alternative to grub2, as every time there's a problem, it seems to be culprit number 1!

Thanks again Quackers, and everyone else that took a look at this thread. Much appreciated and I hope that this answers the question for all those that may be a little confused, when seeing that screen, right at the end of a simple security update.

Have a great day all. Kirby ):P

---

### Post by Kir_B on 2011-02-04
> **Rubi1200 said:**
> Exactly as Quackers said; you are offered these choices because you probably made changes to GRUB configuration files.

I haven't tested all the options, but did exactly that.

Thanks for the further clarification Rubi1200.

Kirby

---

### Post by Quackers on 2011-02-04
No problem :-)
As I have changed my /etc/default/grub file I would expect to be offered the option to keep my changes, but it may well be standard behaviour to offer everyone the choice by default, whether edits have been made or not.

---

### Post by Kir_B on 2011-02-04
> **oldfred said:**
> If you keep the local version, it will not update the menu with the new kernels it you have a new kernel downloaded. sudo udpate-grub should then find that if it still boots with the old kernel. Otherwise you have to manually edit the grub line in the grub menu.

I found it is best to separately backup any edited system files so I know what changes I made and accept the maintainers version. I have had too many times where the new version was so different, it created more issues than any problems I would have in re-editing a file.

Thank you oldfred.

I kind of thought that was the case, but as I said above, I really couldn't find a source that would clarify things.

Again, thanks a lot. Kirby ):P

---

### Post by chirojoseph on 2011-02-04
Hey Kirby...im in the same boat as you buddy. I can sympathize with everything you just "ranted" about...installed LUBUNTU about 5 months ago on a brand new eeepc asus and have really put in over 60 hours searching forums for everything from getting wireless to work to making the mousepad somewhat useable to trying to watch low res vids to getting TRANSMISSION to work..etc etc..

once I did the recommended upgrades and my pc totally hung up on the WINDOWS FONTS upgrade which required like the official "i agree not to rip off windows of their propietary BS" tick box...was left with my system "half updated" i think and couldnt TYPE or Move my mouse ..luckily finally borrowed an external keyboard so that i could use the TERMINAL and re-update or some such thing.

now the first time i actually NEED the netbook cause im traveling and the DAY AFTER i was expounding to a dinner party the virtues of LUBUNTU the damn system is experiencinng this seemingly universal problem of the INIT NOT FOUND, TRY BOOTRAG, blah blah blah...and although ive made a LIVE USB and im able to get into terminal NONE of the 400 suggestions in this forum have yet worked...I still always end up booting into the INITFRAMS or whatever....arrrghhhhh

**questions for the PROS...**

1) its a brand new computer...how can i check (through terminal) to rule out that maybe the hard drive isnt screwed up to make sure its not a hardware issue?

2) Is the whole "purge and install new grub2" thread really my only recourse here? Ive already tried the fsck dev/sda1 deal and nothing really changed, also the editing of GRUB menu as seemed to work for some people..NADA...the LUBUNTU splash screen comes up but then it goes right to the INTFRAMS or whatever screen and no dice..

3) also, when i first made the liveUSB (actually i tried out about 6 different linux "flavors" making the LIVEUSBs the machine always booted up fast...and yes, using this EXACT same thumbdrive which does NOT have US3 on it) now its taking over 15 minutes to boot from the live USB (which I made with Linux LIVE USBcreator)so is **that** some sort of diagnostic indicator for anybody reading this or is it possible i need to make the USBLIVE with a different program (using a windows machine)??

Since SOOOO many people are having this error, even having NOT UPDATED recently, of the machine not being able to find grub..or init..or whatever...has there been any "official UBUNTU" answer thread that i just havent found yet??

thanx so much for any insight..we just gotta be tenacious eh Kirby??

chirojoe

---

### Post by oldfred on 2011-02-04
chirojoseph
It would be best to start your own thread with your problem and eeepc in the title. Those more familiar with those issues then can help.

Have you checked:
Note Known Issues section
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)
Specific Issues by machine:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/)

---

### Post by Jack Brown on 2011-02-09
Regarding the 'Debconf on [PC]' - Configuring grub-pc window, you can safely select "show the differences between versions", "show a side-by-side difference between the versions", "show a 3-way difference between available versions", and they will just give you a preview of differences between current and downloaded update.

After you click Forward, you will be shown the differences. Click Forward again and you're back at the same choice.

The simplest / shortest and quickest to understand option would be 'show the differences between versions', choose the other ones if you want to make sure.

So as can be observed, these options are there to help you make the right decision, and for 'show the differences', changes have been made to make it easier for the new user to make less mistakes.

@chirojoseph - you can try ubuntu netbook edition for eeepc.  I've used the lucid (10.04 LTS)version on a 701 (one of the oldest eees) and wireless works out of the box. Also the FN shortcut keys.  It's not super responsive, but enough for net browsing and research.  But since you've got a new eeepc, the specs would be even better.

You can also install eee-control, which might help.

Have a nice Ubuntu day.

---

