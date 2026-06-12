---
title: "Boinc, minimise/close to system tray"
date: 2009-11-06
forum: General Help
---

### Post by elfuegodiego on 2009-11-06
Hi all,

Running 9.10 and installed Boinc v6.4.5 from the software centre and attached myself to a project no problems.

I was looking through the preferences and can't seem to find an option to minimise the Boinc manager application to the tray.  So my question is, is it possible to minimise the app to tray in ubuntu?  If so how?

I think Boinc is still running after I close the window, did ps -A | grep boinc and it shows up, so not a massive problem.  Just wanted an easy way to check my stats now and again.

Thanks!

---

### Post by Niniel on 2009-11-06
I am using KboincSpy for that. It also lets you start BOINC in the tray.

---

### Post by elfuegodiego on 2009-11-06
Thanks for the reply, will give it a go.

*edit*
Doesn't seem to be in the repos, do you know any gnome equivalents?

---

### Post by Niniel on 2009-11-06
No, this was the only software that I was able to find that worked for me. 
You may have to enable some other repositories... not sure anymore how I did it, so look at this:
[http://kboincspy.sourceforge.net/downloads.php?distro=Ubuntu](http://kboincspy.sourceforge.net/downloads.php?distro=Ubuntu)

I'm not sure the project is still being maintained since the last news date back to 2008, but it works fine for me in 9.04 (haven't upgraded that box to 9.10 yet).

---

### Post by elfuegodiego on 2009-11-06
Downloaded the source from their sourceforge page, when I ran ./configure it complained of me not having kde-configure installed.  I assumed this is because I don't have KDE installed on my system and I don't really want to install it just to run one little prog so I'm just gonna let this go. :D

Boinc seems to run nicely in the background anyway and if I want to check my stats I can just run the manager from the menu.

Thanks again for the info. :)

---

### Post by Niniel on 2009-11-07
You just need the KDE runtimes, not the whole package. All that stuff gets installed anyway when you grab something like Amarok, or, what I found particularly useful, KGrubEditor (I so wish that gets updated for Grub 2).

---

