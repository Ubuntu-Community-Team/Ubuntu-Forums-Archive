---
title: "Sendmail constantly accessing hard drive"
date: 2011-12-27
forum: General Help
---

### Post by duncan12 on 2011-12-27
This is my first post!

I have a problem with my hard drive running constantly. The blue hard drive light is nearly fully on whenever I boot up. I run > sudo iotop each time I turn on my computer, and what is constantly using the hard drive is > sendmail. To run > sudo service sendmail stop temporarily fixes the problem, however I have to switch to terminal (eg. Ctrl+Alt+F1) each time I turn my computer on and run that, which gets annoying.

I really don't want or need sendmail so I have tried running > sudo apt-get remove sendmail many times, only to be told that sendmail is not installed so not removed. I have tried installing then apt-get purge-ing it, however the problem continues.

I am worried about my hard drive and would like a way to stop sendmail from trying to run all the time.

I am using an Acer Aspire 5534, running Ubuntu 11.10, and the exact entry in iotop for sendmail looks like this (but with those random characters changing every few seconds):

> sendmail: MTA ./pBI67itY001689 from queue

Thanks in advance for any help.

---

### Post by Zill on 2011-12-28
duncan12:  A very peculiar problem as my understanding is that sendmail is not installed by default as part of a default Ubuntu desktop system.  You do not appear to want sendmail and so I must question *how* it got installed in the first place?

However, as you seem to have installed it and then removed it to try to resolve the original problem I am concerned that other dependencies will have been installed at the same time and may not now have been removed.

I suggest you open the Synaptic package manager and check to see if *any* sendmail packages are installed.  You can also review the installation history (in the Synaptic File menu) to see exactly when sendmail was installed and which other packages were installed at the same time.  All sendmail packages can then be **completely** removed via Synaptic.

It may well be that this does not actually resolve the problem as it still seems strange that sendmail was installed initially and could have been caused by a corrupted installation.  You might find that the best solution is a fresh download of Ubuntu desktop, checking the md5sum to ensure a good download.  Then burn to a new CD and try running it "live" and ensuring sendmail does not start.  If all is well you could then re-install a clean system.

It could also be useful if you would advise exactly which release of Ubuntu you initially installed and indicate if it *ever* worked correctly (i.e. without the sendmail problem).

---

### Post by duncan12 on 2011-12-30
Hi, thanks for your reply.

> I suggest you open the Synaptic package manager and check to see if any sendmail packages are installed. All sendmail packages can then be completely removed via Synaptic.
In Synaptic Package Manager, a search for "sendmail" brings up "sendmail" and "sendmail-doc" as uninstalled, however some other packages (sendmail-mda, sendmail-mda, sendmail-bin, sendmail-base, and libmail-sendmail-perl). I have now uninstalled them, and the problem seems fixed. Thanks!

With the packages I just mentioned, it also uninstalled "bsd-mailx", for the record.

> However, as you seem to have installed it and then removed it to try to resolve the original problem I am concerned that other dependencies will have been installed at the same time and may not now have been removed.
When running apt-get I check what packages are getting installed/removed, so if that's what you mean by broken dependencies, I don't think that has happened - with apt-get remove sendmail anyway, because it was just sendmail, procmail, and sensible-mda that goes with it.

> You can also review the installation history (in the Synaptic File menu) to see exactly when sendmail was installed 
Looking at the history in Synaptic, a search for "sendmail" brings up nothing. I'm not sure if this is because I never use Synaptic normally and just use apt-get, however I would have thought it keeps a universal record.

> It could also be useful if you would advise exactly which release of Ubuntu you initially installed and indicate if it ever worked correctly (i.e. without the sendmail problem).
I started using Ubuntu in 10.04, and I actually don't know how recent this problem is.

While this is a weird problem, it has been solved as the packages have been removed and the hard drive's no longer going crazy :). I still don't get what sendmail was running with those random "MTA ./pBI67itY001689 from queue" things... what was in them and why were there so many?

Anyway marked as solved because the problem is solved. I'm new to the forum so tell me if that was wrong. Thanks for your help.

---

### Post by Zill on 2011-12-30
> **duncan12 said:**
> ...In Synaptic Package Manager, a search for "sendmail" brings up "sendmail" and "sendmail-doc" as uninstalled, however some other packages (sendmail-mda, sendmail-mda, sendmail-bin, sendmail-base, and libmail-sendmail-perl). I have now uninstalled them, and the problem seems fixed. Thanks!
Good. :-)
> **duncan12 said:**
> ...With the packages I just mentioned, it also uninstalled "bsd-mailx", for the record.
This may have been installed as a dependency to some other application.  Unless you find you need this I suggest it can remain uninstalled - it isn't currently installed on my 10.04 system!
> **duncan12 said:**
> ...When running apt-get I check what packages are getting installed/removed, so if that's what you mean by broken dependencies, I don't think that has happened - with apt-get remove sendmail anyway, because it was just sendmail, procmail, and sensible-mda that goes with it.
My suggestion was to look at Synaptic's history log as this will list *exactly* which packages were installed along with sendmail.  You can then consider removing them if you think they were erroneously installed and are not actually required.  However, this is actually quite difficult to determine due to the way dependencies work - you don't want to remove anything required by a wanted application.  It is usually best to leave dependencies in place unless you *really* know you can remove them.
> **duncan12 said:**
> ...Looking at the history in Synaptic, a search for "sendmail" brings up nothing. I'm not sure if this is because I never use Synaptic normally and just use apt-get, however I would have thought it keeps a universal record.
This implies that sendmail (and dependencies) has been installed for some time.  Synaptic is a useful GUI for viewing dependencies when installing and removing applications, hence my suggestion.  However, it is simply a graphical front-end for apt and so just reflects the apt data.  For example, the synaptic history log shows the same data as the following terminal command:
```
cat /var/log/apt/history.log
```
> **duncan12 said:**
> ...I started using Ubuntu in 10.04, and I actually don't know how recent this problem is.
If you did an upgrade from 10.04 to 11.10, rather than a clean install, then this *could* be the cause of the problem.  Upgrades sometimes work OK but are notoriously flaky and a clean install usually gives better results as it clears out all the "sticky toffees" from old packages that hang around to cause problems.
> **duncan12 said:**
> ...Anyway marked as solved because the problem is solved. I'm new to the forum so tell me if that was wrong. Thanks for your help.
As the problem has now gone you are quite right so thank you for marking the thread as "solved".

ps.  Welcome to Ubuntu forums and feel free to post any further problems - we are (or try to be!) helpful folk here. ;-)

---

