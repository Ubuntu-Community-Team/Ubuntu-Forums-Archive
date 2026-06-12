---
title: "Howto remove password requirement from Software Center"
date: 2011-06-13
forum: General Help
---

### Post by awdyson on 2011-06-13
Hi All,

I have an HTPC box that I'd like to make a bit more accommodating to the other folks in my apartment.
Is it possible to allow them to install and update software without entering a password?
Obviously, I wouldn't want to open access to the repo list or packages from the web.

Kind Regards
Alex

---

### Post by bahubindu on 2011-06-13
Open your system on "root". will do the work.

---

### Post by awdyson on 2011-06-13
> **bahubindu said:**
> Open your system on "root". will do the work.

Thanks for the response, but that's a little more open than I'm looking to run.
If I can't find a better route, that's probably what I'll end up doing.

Regards
Alex

---

### Post by westie457 on 2011-06-13
> **awdyson said:**
> Hi All,

I have an HTPC box that I'd like to make a bit more accommodating to the other folks in my apartment.
Is it possible to allow them to install and update software without entering a password?
Obviously, I wouldn't want to open access to the repo list or packages from the web.

Kind Regards
Alex

Hello, It is possible but not recommended as it is very easy to damage the whole system if it is being run as root. I personally do not know how to remove the password protection of the file system so the recommendation is to set up an account for each person and allow them to set their own password for installing and updating software.

This way if a user accidentally installs a virus or some other malware it will only be that user account and not the whole system that gets infected. It is much easier then to delete that users account and set up another one instead of having to do major surgery on the whole installation.

In Natty new users can be added under System Settings > System > Users and Groups

Hope this has helped you

---

### Post by fyfe54 on 2011-06-13
Why not just set up a user account for them to use with a simple password?  If it gets screwed up, just delete and start over.

---

