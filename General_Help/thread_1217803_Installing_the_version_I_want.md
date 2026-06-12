---
title: "Installing the version I want"
date: 2009-07-20
forum: General Help
---

### Post by kooldino on 2009-07-20
So with the new version of KDE (4 vs 3), I find that the available package managers are very limiting and frustrating, and don't allow me to install the versions of things that I desire.

For instance, a few weeks ago, I wanted to install Firefox 3.5.  It wouldn't allow me to, so I spent an hour finding a workaround.

Now I'm trying to install eclipse 3.4 (rather than 3.2 that the package manager insists is the newest) and again I'm unable to do so.  WHY?  How can I fix this?  This is extremely frustrating.

---

### Post by kooldino on 2009-07-21
bump

---

### Post by synapsys on 2009-07-21
Install from source. Grab the latest subversion and compile. The version in the repositories is the newest version custom tailored for your operating system.

---

### Post by kooldino on 2009-07-22
> **synapsys said:**
> Install from source. Grab the latest subversion and compile. The version in the repositories is the newest version custom tailored for your operating system.

I've done that, but it's kind of a pain.

Plus, I'm never quite sure where to put the directory.  /usr/lib/programname is what i've used before.  Is that sensical?

---

### Post by synapsys on 2009-07-23
That will work... /usr/bin is pretty common. Or you can use your home folder. It doesn't really matter as long as you know where it is. This is the only way to get the latest and greatest version, unless you stumble across a site like getdeb.net which compiles newer versions into nice little .debs for you.

---

### Post by Zorael on 2009-07-23
For finer-control packaging, I'd suggest you install Synaptic or Adept Manager. KPackageKit is a good enough "add/remove software" frontend, but not a "package manager" per se. That or head up into the mountains and brush up your aptitude-fu.

As for versions available, if Ubuntu 82.04 shipped with KoolApp 3.2, and then 3.4 is released a few months later, then 3.4 *will not hit the main repositories*. The only updates to KoolApp 3.2 should be minor stuff fixing security/otherwise critical bugs. Ubuntu 82.04, as a distro release, comes with KoolApp 3.2. If you want 3.4 then you could try the backports repo, which historically ports newer versions back to older releases. Else, wait for Ubuntu 82.10, compile KoolApp 3.4 from source, or find a ppa with it.

[Ubuntu Backports wiki entry](https://help.ubuntu.com/community/UbuntuBackports)
> [SIZE="4"]What are Backports[/SIZE]

Ubuntu releases a new version of its OS every 6 months. After a release, the version of all packages stays constant for the entire 6 months. For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time. The Ubuntu team may apply important security fixes to 2.0.x, but any new features or non-security bugfixes will not be made available.

This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, such as your web browser, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

Backports is an official Ubuntu repository and maintained by knowledgeable Ubuntu developers who are often present on IRC and other communications media. But note that software in backports will not receive review or updates from the Ubuntu security team itself.

[PPA Search](http://ppa-search.appspot.com) (should be considered as untrusted/community sources)

---

### Post by ezsit on 2009-07-23
> I'm unable to do so. WHY? How can I fix this? This is extremely frustrating.

This is the whole point of stability. You don't get it, do you? The version that came with your OS release is the version you get. Anything else needs to be done manually. Quit complaining and use what's provided or roll your own.

---

### Post by kooldino on 2009-07-25
> **synapsys said:**
> That will work... /usr/bin is pretty common. 

Well, /usr/bin tends to have execs ONLY, not the entire directory of goodies that go with it.  That's why I was hesitant to put it there.

> unless you stumble across a site like getdeb.net which compiles newer versions into nice little .debs for you.

Ooh, I'll check that out.  It'd be nice if they had a repository I could add.

---

### Post by kooldino on 2009-08-10
> **ezsit said:**
> This is the whole point of stability. You don't get it, do you? The version that came with your OS release is the version you get. Anything else needs to be done manually. Quit complaining and use what's provided or roll your own.

Do you honestly think that upating your version of firefox or Eclipse to the latest and greatest is going to impact your system stability?

Wanting users to upgrade their entire OS just to run a newer web browser is absurd.

---

### Post by 3rdalbum on 2009-08-10
> **kooldino said:**
> Do you honestly think that upating your version of firefox or Eclipse to the latest and greatest is going to impact your system stability?

Wanting users to upgrade their entire OS just to run a newer web browser is absurd.

If Canonical spent all its time updating packages for older distributions, they'd never get any work done.

Don't forget that Ubuntu is designed for use in production environments, which means that the software is "stable" by design. When we say "stable", we mean "The software does not change in any way that the user can see". In other words, there might be bugfixes and security fixes, but Ubuntu will not create the situation where there's a major software update that causes a flurry of Helpdesk calls complaining that "I can't find a button that was in the software yesterday".

Also, some programs require the latest and greatest libraries, which means compiling and packaging those too.

If you want to go to the trouble of packaging all the latest point releases of all the Ubuntu repository software, then go right ahead - I'm sure most of the home Ubuntu users will happily use the fruits of your labour.

Note that Firefox 3.5 is in the Ubuntu 9.04 repositories. Firefox is one of those things that ends off being the exception to the rule, but a major new version will never replace the original default version.

---

### Post by kooldino on 2009-08-10
> **3rdalbum said:**
> If Canonical spent all its time updating packages for older distributions, they'd never get any work done.

That's why version support only lasts so long.  So if they support the most recent 3 versions or so, that can't be that big a deal.  That said, I'm running the latest and greatest release here...I should be able to get the latest and greatest firefox without jumping through hoops.

> Don't forget that Ubuntu is designed for use in production environments, which means that the software is "stable" by design. When we say "stable", we mean "The software does not change in any way that the user can see". In other words, there might be bugfixes and security fixes, but Ubuntu will not create the situation where there's a major software update that causes a flurry of Helpdesk calls complaining that "I can't find a button that was in the software yesterday".

Understandable, but there should be an option for your repositories which could allow you to get the "latest and greatest" apps, as many of us want.

> Also, some programs require the latest and greatest libraries, which means compiling and packaging those too.

Understood, but this isn't a huge task, especially when IMO, they should be supporting the last few releases.

> If you want to go to the trouble of packaging all the latest point releases of all the Ubuntu repository software, then go right ahead - I'm sure most of the home Ubuntu users will happily use the fruits of your labour.

Haha, I wish I could.

> Note that Firefox 3.5 is in the Ubuntu 9.04 repositories. Firefox is one of those things that ends off being the exception to the rule, but a major new version will never replace the original default version.

It wasn't in the repositories when I went to install it...I guess they were very slow to move on it.

---

### Post by Zorael on 2009-08-10
Hasn't 3.5 been in Karmic's repos as Shiretoko for a while now? Because that's the latest and greatest release.

---

### Post by kooldino on 2009-08-20
Karmic?

---

