---
title: "where to get info on Update Manager updates"
date: 2010-02-24
forum: General Help
---

### Post by alegro on 2010-02-24
Is there an easy way/place to get more info on the updates that the Ubuntu (9.04) Update Manager presents to you?

I know you can highlight one and look below at the "Changes" and "Description". But how can you find a real explanation of what the update *is?*

To give one exampe: There's a 5.0MB update called: openoffice.org-writer

It appears to be a new version of the Writer program?? or is it just security updates??   Should I install it if I'm happy with the current Writer version?

bottom line: where can I get plain talk about what these updates are?

---

### Post by llamabr on 2010-02-24
```
apt-cache search openoffice-writer
```

will search for packages, and return minimal info about them.

```
apt-cache showpkg file
```

will give you a bit more. (hint: I just looked at apt-cache's man page)

---

### Post by alegro on 2010-02-24
The first command above gave one package which as far as I know had nothing to do with any of the updates in Update Manager.

The second command above displayed a bunch of text that may as well be chicken scratch as far as me understanding it. And I'm not sure that it has anything to do with Update Manager updates either.

What I'm looking for is a place or method to get plain English info on the updates that arrive in my Update Manager.

---

### Post by QLee on 2010-02-24
[QUOTE=alegro]Is there an easy way/place to get more info on the updates that the Ubuntu (9.04) Update Manager presents to you?
...
bottom line: where can I get plain talk about what these updates are?[/QUOTE]

There are not going to be simply "feature" updates (upgrades) for 9.04, you can be fairly sure that those offered updates are something you want for security or as a bug fix. Yes you do have to download the whole package again to get the version with the upgrade.

To put it plainly for someone who has to ask this question, "use the force", trust the maintainers. I mean you no disrespect by that, just a plain and simple answer.

As well as the advice poster llamabr gave you, you can also look up a package at 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
find the version you're using and navigate to the page for that package and consult the changelog.
For example:
[http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_3.1.1-5ubuntu1.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_3.1.1-5ubuntu1.1/changelog)

---

### Post by uRock on 2010-02-24
In the update manager window, you click on the update and it shows the details at the bottom.

---

### Post by alegro on 2010-02-24
QLee, Your force reference is well received. : )

on a side note:
Not that I'll probably ever look at the changelog again- but I couldn't find my version there.  1:3.0.1-9ubuntu3.1

Maybe its just a matter of my eyes going crossed while viewing the document.

---

### Post by lavinog on 2010-02-24
Many times a changelog will reference a bug report.
Sometimes a change in one program requires another program to be updated.
If you didn't add any 3rd party repositories, most updates are for patching security holes, or fixing bugs that can cause a loss of data.  It is a good idea to pay attention to what packages are getting updated in case something breaks afterwards.

---

### Post by QLee on 2010-02-24
[QUOTE=alegro]
on a side note:
Not that I'll probably ever look at the changelog again- but I couldn't find my version there.  1:3.0.1-9ubuntu3.1[/QUOTE]

Well, when I use the other "force", a search engine on the Internet I find that package at:
[http://ubuntuupdates.org/packages/show/151945](http://ubuntuupdates.org/packages/show/151945)

However, I'd guess that you need to need to reload the package files to get the latest version. For example, push the check button on update manager while connected to the Internet. Or, reload from the menu in Synaptic, or give the command sudo apt-get update.

---

### Post by alegro on 2010-02-24
I'm looking forward to when they come out with 'force computers'. Like Luke Skywalker, you'll be able to break past the hinderances of technologies, flip up your monitor, and get things accomplished.  Right now I'm spending more time fiddling with the knobs than firing proton torpedoes.

---

### Post by QLee on 2010-02-24
Yes, well say a word of thanks to the Ubuntu maintainers, they have already gone a long way toward that, you would not have liked GNU/Linux much just a few short years ago. It's getting easier to use with each new release, that isn't always apparent to someone who is having problems but, except for disagreements about things like what should be a default configuration, Ubuntu is easy to use.

---

