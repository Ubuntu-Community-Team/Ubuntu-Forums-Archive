---
title: "texlive configuration fails"
date: 2012-01-22
forum: General Help
---

### Post by CapnKirk on 2012-01-22
I recently installed Ubuntu 11.10 on my brand new Dell laptop.

I don't recall the exact order of what I did, but after the basic install was completed and I had a working system, I installed texlive 2011 directly from the TeX.org site. I use TeX extensively, experiment a lot. And I want to be absolutely up to date. So I did not install the Ubuntu texlive-* packages.

I also installed kile for a UI. Either kile has a dependency for texlive-base-* or something else I installed pulled in the texlive packages. But something glitched. Whenever I do the apt-get upgrade thing, it attempts to configure 16 texlive packages and fails:
```
# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up texlive-base (2009-13) ...
texconfig: unknown option `paperconf' given as argument for `texconfig dvips'
texconfig: try `texconfig dvips' for help
...
```

and a whole lot more error messages.

I'm not sure how to resolve this. Since I installed texlive directly outside of the apt-get package system, I don't really need the Ubuntu packages. I configured kile to look for texlive in the directories I used to install it (in /usr/local). Question is, what if kile or other packages don't like my removing the Ubuntu packages?

What would be "best practice" for a situation like this?

TIA!

Kirk

---

### Post by CapnKirk on 2012-02-16
I thought I would update this, since no one has replied.

The problem of the configuration failure was mysteriously solved when I happened to use syntaptic to install an unrelated package. It did TheRightThing(tm) at configuration time, unlike Ubuntu's package manager. Since I wasn't monitoring the install, I didn't see what synaptic did differently. Kudos to synaptic!

As for getting Ubuntu's texlive to live nicely with a direct install of texlive, I note that Ubuntu puts texlive modules in the /usr/share hierarchy. The direct install puts texlive in /usr/local/texlive, so there's no file collision.

If, when installing texlive from the tug.org installer, you choose the option "create symlinks in standard directories" as is [**recommended in the docs**]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-280003.2.4"), then the /usr/local/texlive hierarchy will be used before going to the Ubuntu tex files:

```
$ which pdftex
/usr/local/bin/pdftex
```

If you do need to set environment variables, [**here are the details**]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-320003.4.1").

I use Kile as my IDE, so I make sure that the /usr/local/ hierarchy is used in Kile's settings.

I just wish I could figure out which Ubuntu texlive packages (ideally, all of them) could be removed...

Kirk

---

### Post by 4manifold on 2012-05-01
> **CapnKirk said:**
> I thought I would update this, since no one has replied.

The problem of the configuration failure was mysteriously solved when I happened to use syntaptic to install an unrelated package. It did TheRightThing(tm) at configuration time, unlike Ubuntu's package manager. Since I wasn't monitoring the install, I didn't see what synaptic did differently. Kudos to synaptic!

As for getting Ubuntu's texlive to live nicely with a direct install of texlive, I note that Ubuntu puts texlive modules in the /usr/share hierarchy. The direct install puts texlive in /usr/local/texlive, so there's no file collision.

If, when installing texlive from the tug.org installer, you choose the option "create symlinks in standard directories" as is [**recommended in the docs**]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-280003.2.4"), then the /usr/local/texlive hierarchy will be used before going to the Ubuntu tex files:

```
$ which pdftex
/usr/local/bin/pdftex
```If you do need to set environment variables, [**here are the details**]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-320003.4.1").

I use Kile as my IDE, so I make sure that the /usr/local/ hierarchy is used in Kile's settings.

I just wish I could figure out which Ubuntu texlive packages (ideally, all of them) could be removed...

Kirk

Hi CapnKirk,

I tried installing TexLive 2011 the same way you did (in Precise), and encountered the same problems with the error "unknown option 'paperconf' given as argument for 'texconfig dvips' " and several other similar errors.

Did you ever figure out how to make dpkg configure the packages properly?

Cheers,
4manifold

---

### Post by CapnKirk on 2012-05-02
It was the package manager synaptik that did it: I used it to install an unrelated package and when it came to the configuration step, it made dpkg do the RightThing(tm).

That cleared the problem. I did not use synaptik to install any tex stuff. So, give synaptik a try: install some package you want and see what it does at the configuration step.

Kirk

---

### Post by 4manifold on 2012-05-02
Brilliant!  Worked for me too.  Thank you.

---

### Post by CapnKirk on 2012-05-03
Glad it worked for you. The texlive Ubuntu packages have some sort of error in the configuration step. I wish I knew what so I could file a bug.

Anyway, happy TeXing!

---

