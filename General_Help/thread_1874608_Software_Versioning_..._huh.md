---
title: "Software Versioning ... huh?"
date: 2011-11-03
forum: General Help
---

### Post by tg3793 on 2011-11-03
Ok this is the second time this week that this has come up (different project this time) so I have to ask. Should I be embarrassed that I think that 2.8 is a larger integer than 2.10 ? ... The version listing below seems to suggest that v2.8 is 'older' than v2.10; huh?

[CENTER][COLOR=#000000][FONT=Bitstream Vera Sans][LEFT]GTK+ 3.0
GTK+ 2.24
GTK+ 2.20
GTK+ 2.18
GTK+ 2.16
GTK+ 2.14
GTK+ 2.12
GTK+ 2.10
GTK+ 2.8
GTK+ 2.6
GTK+ 2.4
GTK+ 1.2

[/LEFT]
[/FONT][/COLOR][/CENTER]
After fifteen years I really thought I [understood the versioning]("http://en.wikipedia.org/wiki/Software_versioning") of software :-)

---

### Post by Azdour on 2011-11-03
Hi,

You probably should not be thinking of them as just an integer :). For me 2.10 is major version = 2, minor version = 10. There may be many minor modifications to version 2 before it ticks over to version 3.

So for 2.8, major = 2, so far this is the same major version as 2.10, but the minor is 8 which is of course less than 10. That makes 2.10 the newer version.

---

### Post by WorMzy on 2011-11-03
I can see where you're coming from, but it's best to think of it like this:

2.8 is the ninth revision of 2.0
2.10 is the eleventh revision of 2.0

If 2.10 was 2.1**_._**0, then it'd be the second revision of 2.0

Major version number increases (e.g. 2.* -> 3.*) are generally reserved for complete rewrites, or the completion of a big milestone in the project.

---

### Post by decoherence on 2011-11-03
Basically, version numbers aren't decimals.

How the versioning scheme works varies from project to project but in the case of GNOME 2.10.4 (for example... i don't even know if there is a 2.10.4)

2 - major version. A new major version breaks compatibility with the previous major version. Thus GNOME 2 things can't be expected to work with GNOME 1 and GNOME 3 things can't be expected to work with GNOME 2

10 - minor version. Adding new features increments this number, but in general things aren't that much different.

4 - bugfix number. If there had been 50 bugfix releases, you'd have 2.10.50.

If you're looking at packages, you might also see 'ubuntu01' or 'ubuntu02' tacked on to the end. These indicate that the software has been repackaged for some reason. These updates don't provide any new features or bug fixes (unless the bug fix is related to the package itself, rather than the software it contains) but improve the installation process in some way.

That's how I understand it, anyway. It's been a while since I've looked at GNOME's documentation on the subject.

---

### Post by JKyleOKC on 2011-11-03
And just to make things more confusing, Ubuntu itself does not use that "standard" versioning system. Instead, it uses year.month.update so that my 10.04.3 installation is the third (not fourth) updated release of the April 2010 version.

Ubuntu releases every six months, so that the middle number will always be 04 or 10. Newcomers often drop the trailing zero and refer to the current release as 11.1, though.

And for the kernel itself, odd-numbered minor versions are always experimental, and only the even numbers are stable.

Can't tell the players without a scorecard, and sometimes, not even with one...

---

### Post by tg3793 on 2011-11-03
Ok got it.

And I'll take another look at that Wiki article because I don't think that it made that point of 2.10 being newer than 2.8. ... If that is the case then someone (perhaps me) should go back through that Wiki article and make the necessary corrections.

Thanks everyone.

---

