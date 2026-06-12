---
title: "Turn Visual Effects ON by default (HELP Please)"
date: 2010-11-04
forum: General Help
---

### Post by tphive on 2010-11-04
I'm trying to set up a netbook using Ubuntu Netbook Edition 10.04 LTS.  I'm wanting to set it up via OEM install, and do all tweaking and updating through the temporary OEM account. That way when the end user turns on the machine it's like it's fresh from the store, waiting for them to create an account.

Problem I noticed, with this netbook at least, (Acer Aspire One AOA-110) Visual Effects aren't available after install, so you have to install Compiz yourself, which I figured out how to do. But upon creating a new user account I realized that Visual Effects are OFF by default. :(

I want to set Visual Effects ON and at max by default, or at least Normal, so any account created on that machine has the effects without any user intervention.

I tried the IRC Channel with little success, most of them didn't think it could be done. A couple people did mention a few things, and perhaps they will help in finding a specific solution but I couldn't find anything that would help me:

gconf (Configuration Editor)
/etc/gconf/2
composite manager
Create default template for new accounts by copying to /etc/skel


Thanks for any help. :KS

---

### Post by kerry_s on 2010-11-04
compiz + netbook, don't mix, causes all kinds of problems. that's the reason it's not installed.

---

### Post by tphive on 2010-11-04
> **kerry_s said:**
> compiz + netbook, don't mix, causes all kinds of problems. that's the reason it's not installed.

On a different netbook running ubuntu 8.something it works just fine, and even on the current machine it works just fine after installing it yourself. There's a tool that checks to make sure the machine is capable of it: [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

It passed all checks, so it's not an issue. I just want to get what's mentioned in the OP accomplished. Thanks.

Edit: Please refrain from making replies without any reason or basis, without an explanation it doesn't solve problems or help in any way.

---

### Post by kerry_s on 2010-11-04
i understand it can run compiz, what i'm telling you is the netbook ui causes problems when compiz is on. that's the reason it was blocked, then dropped from netbook.

for example: 
maximus(it makes the windows maximize) & compiz, causes the panels to go invisible or crash.

the compiz effects causes ui lockups randomly.

etc...

if you just have to have it, simply put "compiz --replace" in the startup & enjoy.

---

### Post by tphive on 2010-11-04
Thank you for the much more informative reply. So far I haven't had any issues with the interface, I'll consider not using Compiz with it though. If I wanted to keep it however, what do you mean by put it in the startup? How would I do this? Thanks. :KS

Edit: Quick off topic question, since you seem like you know what you're talking about. Any way to turn on the Ubuntu sound theme by default? So far it doesn't have any annoying alerts and it has a nice login sound, I'd like the end user to be greeted by it upon launch.

---

### Post by kerry_s on 2010-11-04
1. system-> preferences-> startup  (first pic)

2. you can just right click the volume icon (pic 2 & 3)

3. login sound: system-> administration-> login (last pic)

---

### Post by tphive on 2010-11-04
Thanks alot! :D

When I said 'by default' with the sound though, I meant where any new accounts created will have it on automatically, not just the current user. Any setup I do will be done solely from the OEM account. Perhaps though I'm underestimating the power of the OEM account, would be nice if any preferences like that you set, are automatically tagged as the default settings.

Side note: Issue I just ran into when trying to install UNE 10.04  as OEM, can't seem to find a way to actually begin OEM installation, am seeking help on IRC but no avail yet, might Alternate install take care of this? Or just no OEM for netbooks? O.o

---

### Post by kerry_s on 2010-11-05
when you boot up the installer, as soon as you see the keyboard + man on the bottom hit "enter", then i think it's f6 menu?

---

