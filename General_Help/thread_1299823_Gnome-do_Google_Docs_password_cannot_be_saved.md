---
title: "Gnome-do Google Docs password cannot be saved"
date: 2009-10-24
forum: General Help
---

### Post by sgleo87 on 2009-10-24
After upgrading to Ubuntu Karmic RC and installing Gnome-do 0.8.2, the Google Docs Plugin no longer works. When I configure the plugin by entering my email and password and then hit apply and close, the password is not saved (when opening the config menu afterwards, the password field is blank again). Also, the password validation is successful for any password I enter (which obviously shouldn't be the case). Without a stored password, I cannot access any of my google documents through gnome-do...anybody else having this problem or know a solution???

---

### Post by sgleo87 on 2009-10-25
Nobody in the same boat with me?

---

### Post by commonplace on 2009-11-04
I'm having a similar problem, but not with Google Docs (I haven't tried it) -- mine is with the Microblogging plugin. I put in my Twitter name and password and it works... until the next time, when it "forgets" my information.

So it sounds like the same problem, just with a different plugin. I haven't found a fix yet, but came across this thread while researching the issue.

Hopefully someone will figure it out!

/Kevin

---

### Post by commonplace on 2009-11-04
[Here]("https://bugs.launchpad.net/do-plugins/+bug/475002")'s the bug report I filed. I still assume (perhaps incorrectly) that my bug is the same as yours, so if they fix it for me, it will hopefully resolve your issue.

UNfortunately, it worked fine under 9.04 and all previous releases, so it may be something specific to 9.10/Karmic. But I'd still imagine the issue is GNOME Do's to fix, not Ubuntu's.

/Kevin

---

### Post by sgleo87 on 2009-11-05
> **commonplace said:**
> UNfortunately, it worked fine under 9.04 and all previous releases, so it may be something specific to 9.10/Karmic. But I'd still imagine the issue is GNOME Do's to fix, not Ubuntu's.


Yeah you're probably right about that...hopefully it gets fixed soon.

---

### Post by commonplace on 2009-11-05
> **sgleo87 said:**
> Yeah you're probably right about that...hopefully it gets fixed soon.

Question for you: are you running Ubuntu (GNOME) or Kubuntu (KDE)?

I'm starting to wonder if my issues might not be related to KDE... when I run gnome-do from the terminal, I see errors about it not finding gnome-keyring (something like that -- I'm not at that computer), which is probably what stores/secures the passwords..?

So my issue might be a KDE issue, not a Ubuntu or GNOME-Do issue. But I don't know. GNOME-Do is supposed to work in KDE, too. I'll have to do some more research.

Just curious if you're also using KDE, or if you're using GNOME.

/Kevin

---

### Post by sgleo87 on 2009-11-09
I am using Ubuntu and I do not get any error messages when running gnome-do from a terminal. I also left a comment in your bug report stating that I have the same problem...I hope it helps to find a solution.

---

### Post by commonplace on 2009-11-09
> **sgleo87 said:**
> I am using Ubuntu and I do not get any error messages when running gnome-do from a terminal. I also left a comment in your bug report stating that I have the same problem...I hope it helps to find a solution.

Interesting. Okay. That rules out the Ubuntu/Kubuntu explanation.

I really miss GNOME-Do! Hope someone fixes it soon. :)

*Edit: Yep, just saw your bug response post. Maybe that'll catch their attention again. When I initially turned it in, I got a response within minutes it seems, which got my hopes up. Nothing since then, though.*

/Kevin

---

### Post by sgleo87 on 2009-11-10
I just realized the Google Docs plugin actually works without entering my password. If I just enter my email address, gnome-do can access my documents online if I am signed into my account. So I guess that solves the problem for me!

---

### Post by sgleo87 on 2009-11-11
Well, I guess I was a little too optimistic...I have the exact same problem: if I enter the username and password it works until I reboot and then I have to enter the password again....very annoying.

---

