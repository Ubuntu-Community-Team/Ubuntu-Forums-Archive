---
title: "Update Manager hangs"
date: 2010-07-02
forum: General Help
---

### Post by bkline on 2010-07-02
Anyone else have this problem with Ubuntu's Update Manager?  You sit down at your computer and Update Manager is open telling you that there are packages that need to be updated.  You click on "Install Updates" and nothing happens.  You expect to be prompted for your password but the dialog box never shows up.  Doesn't happen every time, but often enough that it's annoying.

---

### Post by bkline on 2010-07-08
Bump.  Surely I'm not the only person who's run into this problem.

---

### Post by PEM59 on 2010-08-15
Bump,

I just started having the same problem.

Up to now Update manager has been working fine.

This morning (15 Aug 2010 - about 8:00 USA EST)  it show up.  I click on "Install updates" and it does nothing.

I have tried several times, even rebooting.

On one try, it asked for my password as usual, then did nothing.

.

---

### Post by sikander3786 on 2010-08-15
> **PEM59 said:**
> Bump,

I just started having the same problem.

Up to now Update manager has been working fine.

This morning (15 Aug 2010 - about 8:00 USA EST)  it show up.  I click on "Install updates" and it does nothing.

I have tried several times, even rebooting.

On one try, it asked for my password as usual, then did nothing.

.

Did you try updating from the terminal?

```
sudo apt-get update

sudo apt-get upgrade
```

The issue might resolve itself after a successful update.

---

### Post by PEM59 on 2010-08-15
I figured out my problem - it was a dumb mistake - wrong password.  :redface:

---

### Post by bkline on 2010-08-15
As you figured out for yourself, your problem wasn't really the same one I'm experiencing (neither the cause nor the symptoms).  I'm able to get Update Manager to do the right thing if I close it down and launch it again by hand, or even just force it to check for new updates again, and **then** click on Install Updates.  Probably not a hard problem for the maintainers to fix, but they probably don't read these forums. :(

---

### Post by ceoxtc on 2010-10-23
<Bump>  I too have experienced this problem since upgrading to 10.4.  Usually the problem is that I'm surfing via FF and the update manager opens in the background.  When I bring it to the foreground and click "Install Updates", nothing happens.  Like you, I can only install if I either a) shutdown update manager and let it launch again; or b) click the "Check" button, which then prompts me for the password.

I came here looking for a solution.  Guess I'll go search on launchpad...

---

