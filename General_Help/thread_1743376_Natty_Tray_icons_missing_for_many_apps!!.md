---
title: "Natty: Tray icons missing for many apps!!"
date: 2011-04-29
forum: General Help
---

### Post by andrei_1 on 2011-04-29
The tray icons for many apps (especially QT apps) are missing!

Important apps that become unusable after being minimized to tray - due to having no tray icon:

* Pidgin
* KeePass
* JungleDisk

Anyone know if this can be fixed? A workaround? An explanation? Is this a known (rather extremely serious I should say) bug?

---

### Post by andrei_1 on 2011-04-29
Will try this:

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

- to see if it fixes it.

Strange thing, it seems the user has to go through an arcane interface just to make some very popular applications like Pidgin usable??

---

### Post by andrei_1 on 2011-04-29
> **andrei_1 said:**
> Will try this:

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

- to see if it fixes it.

Strange thing, it seems the user has to go through an arcane interface just to make some very popular applications like Pidgin usable??

The systray-whitelist solved it, mind-boggling as it is.

---

### Post by TheCat on 2011-04-29
Oh, thank goodness I found this.  I just changed the system tray white list to 'all'.

---

### Post by andrei_1 on 2011-04-29
> **TheCat said:**
> Oh, thank goodness I found this.  I just changed the system tray white list to 'all'.

Actually I think it's ['all'] - it would not let me drop the square brackets.

---

### Post by timgood on 2011-04-29
> **andrei_1 said:**
> Actually I think it's ['all'] - it would not let me drop the square brackets.

Great stuff! Thanks - this was driving me mad. Now got Shutter and Radio Tray working...

---

### Post by 4manifold on 2011-04-29
That totally worked.  Thanks!

---

### Post by nathan.f77 on 2011-05-10
Sorry but WTF???? Who thought it was a good idea to have a systray 'whitelist'?

11.04 & Unity are making me say WTF waaaaay too much.

---

### Post by 5149.5 on 2011-05-10
> **nathan.f77 said:**
> 11.04 & Unity are making me say WTF waaaaay too much.

After a few weeks with 11.04, I gotta agree with this. Do the devs use what they produce? I'm guessing they don't. If they had to use what they are producing, a lot of these stupid problems would go away.

---

### Post by Ghost|BTFH on 2011-05-10
Yes, most of them *do* use what they make - the problem is, they get the idea in their head that ||1||"to protect against a malicious attack where the user might not see the program since it is hiding in the tray, we'll set up a whitelist for the tray..." and then they use that whitelist for all their software, forgetting to do so for ALL STANDARD REPOSITORY SOFTWARE because, hey, having 10k+ software listed in the whitelist would just be plain silly...so it'd be easier to just use ['all'] and then everything can go into the system tray but then in order ||goto1||

Cheers,
Ghost|BTFH

PS: In short, this whole release was rushed, it's not an LTS by a long shot, give it a month, they'll have it fixed...until then, you could check out Fedora's Gnome 3, which will also make you say WTF a lot as well.  Basically, Gnome, it is a' changin'...get with the program or switch to KDE/LXDE or some other flavor of desktop.  Unity is nothing more than a smarter Gnome 3, unstable though it may be.

---

### Post by andrei_1 on 2011-05-10
> **Ghost|BTFH said:**
> Yes, most of them *do* use what they make - the problem is, they get the idea in their head that ||1||"to protect against a malicious attack where the user might not see the program since it is hiding in the tray, we'll set up a whitelist for the tray..." and then they use that whitelist for all their software, forgetting to do so for ALL STANDARD REPOSITORY SOFTWARE because, hey, having 10k+ software listed in the whitelist would just be plain silly...so it'd be easier to just use ['all'] and then everything can go into the system tray but then in order ||goto1||

Cheers,
Ghost|BTFH

PS: In short, this whole release was rushed, it's not an LTS by a long shot, give it a month, they'll have it fixed...until then, you could check out Fedora's Gnome 3, which will also make you say WTF a lot as well.  Basically, Gnome, it is a' changin'...get with the program or switch to KDE/LXDE or some other flavor of desktop.  Unity is nothing more than a smarter Gnome 3, unstable though it may be.

Totally agree.

---

### Post by ketan.khope on 2011-06-02
> **andrei_1 said:**
> Will try this:

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

- to see if it fixes it.

Strange thing, it seems the user has to go through an arcane interface just to make some very popular applications like Pidgin usable??
That Worked! I was dying to get my radio tray working..  Thanks a lot!

---

