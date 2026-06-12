---
title: "WARNING: Problem when updgrading to Natty"
date: 2011-04-29
forum: General Help
---

### Post by kencamargo on 2011-04-29
A minor problem became a huge quasi-catastrophe yesterday when I was doing the upgrade from Maverick to Natty on this machine. One of the packages I head had a malformed attribute ("Priority" was stated as "Normal", when it should be "Standard"). This made the upgrade process stop, and nothing I could come up with would make it resume. The system asked to reboot, and that's where the problems began, because the computer was rendered unusable. After I found and corrected the above problem (by manualy editing the offending bit on /var/lib/dpkg/available the process went on, but by this time things were really screwed up, I had to manually install unity before I could have an usable machine again.

So, beware this error, and maybe the developers could make a more robust error detection trap for this kind of problem, allowing the upgrade to continue (it was a non-essential package).

Hope that helps someone else,
Ken

---

### Post by mörgæs on 2011-04-29
Thanks for the advice. Please mark the thread 'solved'.

---

### Post by kencamargo on 2011-04-29
I had the same problem with another machine (and another package). The first one was a 64 bit version, and the second a 32 bit. The offending packages were different. I forgot to add that I also had to manually fix the offending bit in  /var/lib/dpkg/status.

I'd strongly suggest again that the robustness of the upgrading procedure should be reviewed, I am certainly not the only user with an occasional non-standard package in the machine.

Ken

---

### Post by mörgæs on 2011-04-30
I agree on the upgrading procedure. A clean install is always preferred.

'Solved' is in 'thread tools'.

---

### Post by kencamargo on 2011-04-30
I don't think we quite agree; what I had in mind is that the upgrade procedure should be reviewed, not completely avoided. :)

Another minor issue: after upgrading a netbook, when rebooting it went into a session with no window manager; the login window kept as default the netbook session, which no longer exists. I had to change it to "ubuntu", and everything worked fine.

---

