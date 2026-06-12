---
title: "Ubuntu for an Autistic Teenager"
date: 2010-03-04
forum: General Help
---

### Post by SteveTheRed on 2010-03-04
My son is 15, autistic and mentally retarded. He is moderate-low functioning and loves to watch Barney the Dinosaur, Thomas the Tank Engine and other young children's programming on YouTube on his computer. He can talk in a limited way and can read out loud at about the first-grade level, though he seems to have little or no comprehension of what he's read (hyperlexia).

I'm having problems with viruses and spyware because he lacks the judgment that keeps the rest of us from clicking on every window that pops up. We've had a particularly nasty crop of ad-ware viruses lately that pops up graphic porn ads even when the browser is closed. I've had enough of this.

The computer is an ancient Dell Dimension 4600 desktop (circa ~2002) running Windows XP. I've run Ubuntu from a live CD and installed flash as a test. YouTube videos play fine, so that's not a problem. I don't really want to replace the computer becasue it still works and is only used by him to run firefox. I am willing to buy a new computer if that turns out to be the only option.

I've been using Ubuntu exclusively on my laptop for several years and I would like to remove Windows from his computer and replace it with Ubuntu. I'm wondering how I can make his computer as accessible as possible to him while not sacrificing too much security.

My son has very poor fine motor control over his hands. He can use a mouse with some difficulty, but using a keyboard is out of the question. He can use the mouse to click on the shortcuts to his favorite videos, but I can't think of how he would be able to enter a password for his account. Not only does he have the fine motor problem, but he is not able to remember any usefully secure password.

Does anyone have any ideas about how to make his computer accessible to him without opening a gaping security hole? Two ideas that I've kicked around are creating a user with absolutely the minimum privileges required to use firefox and no password or finding some way to enter a password that doesn't require a keyboard. I haven't come up with how to implement either of those ideas successfully.

Sorry for such a long post. I'd really appreciate any ideas that anyone has about this. Thank you.

---

### Post by Onesimus on 2010-03-04
Regarding the Internet security you could look at installing various add-ons in Firefox (e.g. adblock plus, ProCon-latte)

Only today I came across Gnome-Nanny ([http://www.unixmen.com/news-today/853-gnome-nanny-a-control-prental-for-gnome-ubuntu-]("http://www.unixmen.com/news-today/853-gnome-nanny-a-control-prental-for-gnome-ubuntu-")).  It seems to be a complete solution for restricting web access, mail, and amount of time a user gets to spend on the computer.  I haven't yet tried it though.

Hope this helps !

---

### Post by LowSky on 2010-03-04
You can have the PC login automatically to a certain account, and give it a time limit to auto log into any account if he accidentally logs out.

he wont need a password for normal internet use, and shouldn't really need to install anything. So I would worry about him accidentally installing anything.

ad-block is a great plugin for firefox. Also placing icons on the desktop might be beneficial for him, maybe remove the applications menu and the system trays so he doesn't accidentally click on things that might confuse him. You can even set it up to look like windows xp for familiarity.

---

### Post by kanikilu on 2010-03-04
For a home desktop, there really isn't much loss of security to have an automatic login. In fact I have mine set that way because it's an annoyance.

I believe in Karmic you can choose to set this during install, or if you need to change it later, it's in System > Administration > Login Screen.

It sounds like any "administrative" tasks would be done by you anyways, so you shouldn't have to worry about your son needing to put in the password during normal use. And of course, as I'm sure you know, there is little to any risk of malware by running Linux.

To make things easier for him, you could probably also set Firefox to run on start up in System > Preferences > Startup Applications ([https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)).

---

### Post by Onesimus on 2010-03-04
When creating a new user (System->Administration->Users and Groups), there is an option to make the user's profile: Unprivileged.

In addition, if he is the only user of the machine you could set it up so that it automatically logs into his account when it boots up.
(System->Administration->Login Screen)

Hope this helps as well

---

### Post by Agent ME on 2010-03-04
Even if he's not the only user, setting his account to auto-login wouldn't be a bad idea.

You should install Ubuntu, set up your user account first (as admin), then create his account, and set it to auto-login. Then switch to his account, and customize it how you want (Firefox autostart, bookmarks, etc).

Whenever you want to use the computer on your own account (including doing admin stuff like installing software and updates), just click at the top right and switch to your account.

---

### Post by kurros on 2010-03-04
Are you aware of [http://www.zacbrowser.com/](http://www.zacbrowser.com/) ? It runs pretty well under Wine and is a great closed environment with interactive and animated things.

---

