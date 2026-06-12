---
title: "Missing Applications Lens in 11.10"
date: 2011-10-13
forum: General Help
---

### Post by CrawlingKSnake on 2011-10-13
Hi there,

The problem is that when I open the dash there is no icon for the applications lens, and no results are shown when searching for applications. I.e. searching for "calc" doesn't bring up "calculator". It also seems like the "commands" lens isn't working either as I can't run any commands from "alt + F2"

This problem first occurred for me in 11.10 beta 2, so I went back to 11.04 and everything worked fine. I have my home folder on a separate partition, so today I did a clean install of 11.10 on my OS partition, keeping all my files as they were.

I've checked the /Usr/Share/Unity/Lenses/ folder and there are .lens files present for both "commands" and applications.

I've logged into the guest account on the same machine and this problem doesn't occur. So I'm thinking the problem must be an option or a conflict with something that I have in my home folder, I just don't have a clue what it could be.

Does anyone have any suggestions that I could try, or ideas what could be happening?

If all else fails, I guess I'll just copy all my data files out of home folder to my external hard drive, reinstall the OS again and copy them back across. Though I'd prefer not to, because then Ubuntu One will spend days going through everything.

Many thanks!

Mike

---

### Post by effenberg0x0 on 2011-10-13
Try this:

```

sudo apt-get install --reinstall unity-lens-applications
sudo service lightdm restart

```

Regards,
Effenberg

---

### Post by mc4man on 2011-10-13
It's possible that some conf file in your home is causing the issue

I'd probably first try creating a new  user & logging in to that user to see if things work there. If so then it is something local to your user.
(you could try 
unity --reset

---

### Post by CrawlingKSnake on 2011-10-13
@effenberg0x0

I tried that and it didn't work, I still don't have an applications lens.

@mc4man

I created a new user account and everything worked fine, so I guess the problem must be in a conf file in my user account.

I also tried resetting Unity but things stayed the same.



I've got GNOME Shell installed so I'll login into that and remove the applications I have installed. I'll see if that removes whatever is causing the problem, and then I can reinstall the applications I have one by one and see if the bug occurs again (if I manage to get rid of it).

---

### Post by CrawlingKSnake on 2011-10-13
Actually, it seems like the software center isn't working for me through Unity or through GNOME Shell in my user account. It seems to be working fine on the other user account and the guest account though.

Most strange. Well I don't know what I did to make everything like this, so it looks like it will be a "backup, copy my data to external hard drive, format everything on my laptop, reinstall and copy back, wait whilst Ubuntu One re-downloads loads of photos/videos/files even though I already copied them" jobby then.

I'll take notes if it happens again!

---

### Post by mc4man on 2011-10-13
> **CrawlingKSnake said:**
> 
Most strange. Well I don't know what I did to make everything like this, 


You likely didn't do anything - upgrades leave your home dir. alone & there's no guarantee that previous settings are still good.

If you haven't redone there are some folders/files that could be deleted though I'd go the fresh install route myself
(I just dumped a 4 day old 11.10 dev install to get a fresh start.

(there should be an SRU upgrade coming shortly  - new compiz/unity & others

---

### Post by leuty on 2011-10-14
Hi

I've encountered the same issue as CrawlingKSnake including the not working software center. I've searched the web but found nothing. 

Does anybody know a solution to this issue?

Thank you.

---

### Post by AppleWiz on 2011-11-13
Perhaps this will help the original thread poster.

Goto Ubuntu software centre, hopefully you can get that? Type in "unity-lens" in the search box at the top right. Install anything not already installed, probably 3 packages.

Close software centre, log out and back in. Try your Dash Home icon...

Regards,
Rob

---

### Post by Frogs Hair on 2011-11-13
The name of the package in 11.10 is unity-lens-application .

---

### Post by dundacil on 2011-11-15
[I]I wonder if there has been any progress in pinpointing the culprit.
As from yesterday, I am experiencing the same problem (missing apps icon in dash, and no application recognized in dash).
This is a fresh (format etc) install of oneiric, with only "data" files moved onto the machine (so, brand new configuration files and the like). The machine was formatted and installed about a week or so ago, and this came literally out of the blue.
Me too have no problem whatsoever with a guest session, and I have been through the various forced reinstall of -lens-, unity etc. :)

Thanks,

Riccardo
[/I]

---

### Post by dundacil on 2011-11-15
PS: I realize that I have some information which perhaps can help to track down the problem.

If I click on "Internet Apps" inside dash, I do get an error in .xsession-errors 

WARN  2011-11-15 15:34:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method Search proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-15 15:34:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist

Does it help?

Riccardo

Edit: Solved! In my case, the problem appears to be a corrupted .cache. I removed $HOME/.cache and after a log out/log in, dash went back to its normal behaviour

---

### Post by christovic on 2011-11-24
Thank you so much! That fixed it immediately :D Needs to be marked solved.

---

