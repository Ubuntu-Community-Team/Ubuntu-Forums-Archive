---
title: "Accessing multiple accounts via console causes LibreOffice to lag"
date: 2012-06-09
forum: General Help
---

### Post by ladasky on 2012-06-09
Hello again,

This is a follow-up from _[the thread I started about a week ago]("http://ubuntuforums.org/showthread.php?t=1988085")_.  I have defined my problem more precisely, and thought that a new thread with a better title should be created.

My system configuration:
AMD 6-core CPU, 8 GB RAM, NVidia GTX 460 GPU, Ubuntu 11.10 x64. All fairly recent hardware and software, as you can see.  LibreOffice version is 3.4.4, the one bundled with Ubuntu 11.10.

I am gradually moving towards separating my personal and work computing environments.  I now have two logins on my home desktop machine.  Both logins have administrator privileges (in case that matters).  In the course of a computer session, I typically start a long-running process on my work account, then switch to my personal account, and switch back later.  I keep a log of my work in LibreOffice Writer, and I leave Writer open when I log out of my work account.

When I log back in to my work account, I have a noticeable lag in response to typing in Writer, and pop-up menus take up to a full second to appear.  Scrolling also gets very slow.  If I open LibreOffice Calc, it too performs fine UNTIL I log out of my work account and log back in again.

If I look at the System Monitor, CPU loading and memory use do not appear to be a problem. None of the CPU cores are registering much more than 10% use at any given moment. RAM is lightly used, and swap space is not used at all.

Every other application that I have open continues to operate normally.  Quitting LibreOffice and starting it again restores normal operation.

OK, so I have a work-around solution to the problem.  But I don't understand why the problem exists in the first place.  If anyone has any insights on this matter, I would appreciate hearing what you know.  Thanks!

---

### Post by ladasky on 2012-09-26
> **ladasky said:**
> Both logins have administrator privileges (in case that matters).

More recent changes to my computer have confirmed that it DOES NOT matter whether the accounts in question have administrator privileges.  Just the act of switching back and forth between two accounts while LibreOffice is open can trigger the extreme slowdown.

---

