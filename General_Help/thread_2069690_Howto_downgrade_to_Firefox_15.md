---
title: "Howto downgrade to Firefox 15?"
date: 2012-10-11
forum: General Help
---

### Post by Carborundum on 2012-10-11
Mozilla no longer ships Firefox 16 after discovering a critical security vulnerability [[1]]("https://blog.mozilla.org/security/2012/10/10/security-vulnerability-in-firefox-16/"), and are now recommending users to downgrade to version 15. What is the simplest way for Ubuntu users to do this, preferably via apt-get?

---

### Post by pompel9 on 2012-10-11
You can go here [http://www.mozilla.org/en-US/firefox/new/](http://www.mozilla.org/en-US/firefox/new/) and download the tar. I don't remember how to install in terminal with tar (maybe some other can post the codes).

Or you can uninstall firefox from software center, and then install it again from software center. You should then get v 15.

---

### Post by Carborundum on 2012-10-11
> **pompel9 said:**
> You can go here [http://www.mozilla.org/en-US/firefox/new/](http://www.mozilla.org/en-US/firefox/new/) and download the tar. I don't remember how to install in terminal with tar (maybe some other can post the codes).
Manually installing applications that are also installed via the package manager is generally a bad idea. Overwriting files without telling APT about it is a fine way of ending up in dependency hell.
> Or you can uninstall firefox from software center, and then install it again from software center. You should then get v 15.
No, v. 16 is still in the repos as of posting this.

---

### Post by vasa1 on 2012-10-11
> **Carborundum said:**
> ...
No, v. 16 is still in the repos as of posting this.
Are you on 12.10?

---

### Post by jerrrys on 2012-10-11
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3742828](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3742828)

---

### Post by Carborundum on 2012-10-11
> **vasa1 said:**
> Are you on 12.10?
No, 12.04.
> **jerrrys said:**
> [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3742828]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa/+build/3742828")
Would you care to elaborate on this? The only version available via the PPA for precise is 16.

---

### Post by jerrrys on 2012-10-11
.deb ff15 ??

---

### Post by Carborundum on 2012-10-11
> **jerrrys said:**
> .deb ff15 ??
That would require me to install it via dpkg, which I have already said I do not want to do.

---

### Post by vasa1 on 2012-10-11
@Carborundum, which repo are you getting Fx from?
I'm surprised that Fx 16 is available for 12.04 so soon. Normally, 3-4 days pass before Canonical's version is pushed.

---

### Post by vasa1 on 2012-10-11
> **Carborundum said:**
> Manually installing applications that are also installed via the package manager is generally a bad idea. **Overwriting** files without telling APT about it is a fine way of ending up in dependency hell. ...
I've been using Firefox and Seamonkey direct with any issue. I'm also using LibreOffice direct.
I don't know what is meant by overwriting in this context.

---

### Post by jerrrys on 2012-10-11
Your running ubuntu and you won't install a .deb?!?  Good luck, Ill leave you to it

---

### Post by Carborundum on 2012-10-11
> **vasa1 said:**
> @Carborundum, which repo are you getting Fx from?
I'm surprised that Fx 16 is available for 12.04 so soon. Normally, 3-4 days pass before Canonical's version is pushed.
precise-updates, which is enabled by default.
> **vasa1 said:**
> I've been using Firefox and Seamonkey direct with any issue. I'm also using LibreOffice direct.
I don't know what is meant by overwriting in this context.
Well, I mean if I were to unpack this archive into my /usr/bin, that would overwrite whatever firefox related files were already there, yes? I could of course install it in ~/temporaryfirefox or something, but that wouldn't really solve the problem.

> **jerrrys said:**
> Your running ubuntu and you won't install a .deb?!?  Good luck, Ill leave you to it
I won't install a .deb of something that is simultaneously installed via APT.

---

### Post by pompel9 on 2012-10-11
Sorry about my first half of my post. What I meant was, remove firefox first (neglected to mention that) and then install with the tar.

Do you get v16 now if you install from software center (official release via ubuntu, not PPA)?

---

### Post by Carborundum on 2012-10-11
> **pompel9 said:**
> Sorry about my first half of my post. What I meant was, remove firefox first (neglected to mention that) and then install with the tar.
That would work, I suppose. I was hoping there was an easier way, since Mozilla considers the bug severe enough to temporarily stop shipping 16, but I guess not.

> Do you get v16 now if you install from software center (official release via ubuntu, not PPA)?Yes, I get 16 from (the official, enabled by default) precise-updates repository. I can also choose version 11 from the standard precise repo, but no 15 from what I can find.

For now, I've downgraded to 11 (this can be done with 'sudo apt-get install firefox=11.0+build1-0ubuntu4'). If this bug takes a long time to fix I will uninstall Firefox via APT, and upgrade to 15 manually. Thanks everyone for your help.

---

### Post by bra|10n on 2012-10-11
If you are all that concerned about a vulnerability likely to affect Firefox16 for only the next 12 -18 hours would it not be simpler to install and use another browser until a patch becomes available?

---

### Post by Carborundum on 2012-10-11
> **bra|10n said:**
> If you are all that concerned about a vulnerability likely to affect Firefox16 for only the next 12 -18 hours would it not be simpler to install and use another browser until a patch becomes available?
It probably would. :P

Thing is, I have Firefox configured exactly like I want it, with bookmarks and addons and stuff, so it would be inconvenient to switch to another browser (laziness ho). For now, Firefox 11 does the trick, and if 16 goes live again in less than 24 hours I guess there is no need to start mucking about with installing 15 manually.

---

### Post by Statia on 2012-10-11
> **jerrrys said:**
> [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3742828](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/3742828)

That is a package for ARM.

---

### Post by ALinuxWindowsBalance on 2012-10-11
> **vasa1 said:**
> 
I don't know what is meant by overwriting in this context.

Uninstalling a newer version by hand (rm) and installing an older one by hand (tar -xcvf)
different versions have different dependencies.

For example, let's say you are leaning on something, like a marble tabletop. And somebody, in an instant, replaces it with a splintery wooden one. When you go to look at it, or run it, the system says,
what the hell? and it realizes that it needs less pressure put on the table so the wood doesn't break.
In the computer reality, it looks like this(but not as severe, of course)
```
PANIC KERNEL MODE INTERRUPT
```

---

### Post by Kenno on 2012-10-11
As an arguably more desirable alternative to downgrading, one could upgrade to the fixed version 16.0.1. Although it's not formally released yet (I guess it needs a few more hours of testing) it's already available here:
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)
(Click on "technical details about this ppa" for more info on how to use it.)

**Edit 1:** more info and confirmation that this is indeed the fixed version here:
[https://blog.mozilla.org/security/2012/10/10/security-vulnerability-in-firefox-16/comment-page-1/#comment-110600](https://blog.mozilla.org/security/2012/10/10/security-vulnerability-in-firefox-16/comment-page-1/#comment-110600)

**Edit 2:** as of 5 hours ago, firefox 16.0.1 is available from the repositories (hit "Refresh" if you can't see it), so the point is moot now.

---

