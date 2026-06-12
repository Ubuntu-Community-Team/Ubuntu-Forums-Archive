---
title: "Google Chrome for Gutsy"
date: 2010-01-31
forum: General Help
---

### Post by slira on 2010-01-31
Hi

I'm running an old version of ubuntu (7.10). Is there a way to install Google Chrome? I know I should have updated the distro but it is running so smoothly that I decided not to. Any ideas on how to install Chrome? Thanks!  slira

---

### Post by philinux on 2010-01-31
> **slira said:**
> Hi

I'm running an old version of ubuntu (7.10). Is there a way to install Google Chrome? I know I should have updated the distro but it is running so smoothly that I decided not to. Any ideas on how to install Chrome? Thanks!  slira

You do realise that that 7.10 is not supported anymore. No security updates etc etc.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

---

### Post by slira on 2010-01-31
Yes, I'm aware of that. However, it still works fine (no problems, in fact) and I have such a level of personalisation that I decided not to reinstall right now. Thanks anyway. slira

---

### Post by howefield on 2010-01-31
> **slira said:**
> Any ideas on how to install Chrome? Thanks!  slira

What have you tried so far, have you downloaded the .deb package from the google site for instance ?

---

### Post by slira on 2010-01-31
Hi howefield, thanks for your post.
Yes, that's the first thing I did. But, as my distro is very old, there are some dependencies I'm not able to solve (even using the repositories directly). In fact libc6 and libnss3-1d are missing in an admissible version and libc6 is now interdependent with findutils (the second will not install without the first and vice-versa - dead-end).
I'm giving up... I'll have to reinstall ubuntu using an updated distro and all will work then!
Best, slira

---

### Post by themusicalduck on 2010-01-31
Remember that you can keep all your settings and personalisation so far of your current install if you make a backup of your entire home folder then copy it over to the new install once it's done. All installed programs do need to be reinstalled though.

There are also some settings in the /etc/ folder like any software sources added, but it wouldn't be sensible to copy over the entire folder, but take note of any deb sources you've added or such.

I don't know if there would be any problem with coping a home folder from gutsy to karmic since they're probably quite different, perhaps someone else would know more about that.

---

### Post by slira on 2010-01-31
> **themusicalduck said:**
> Remember that you can keep all your settings and personalisation so far of your current install if you make a backup of your entire home (...).

Thank you; however there are some things that will have to be re-make: e.mail accounts in my pop client (a number of them...), ftp accounts (also a number of them), my virtual machines (yes, MSWindows is running in one of those, for the last few things I must do using windows), the connections to the "home net" (media server, printer, etc.).... etc. It will be some work, so I'm postponing. Probably during holidays! Thanks for your tip. Best slira

---

### Post by slira on 2010-01-31
Hi All
I'm giving up - no way Chrome will install in my system because of dependencies. I'm marking this as [solved] - thanks for your help. slira

---

### Post by howefield on 2010-01-31
> **slira said:**
> my virtual machines (yes, MSWindows is running in one of those, for the last few things I must do using windows),...

I'm sure you know, but just in case.

You needn't lose your virtual machines, copy them off some place and then copy them back. Sure you'll need to install the main program and put the settings back, but you needn't have the hassle of reinstalling the guest systems.

If it is any consolation there are some benefits to running something more current, like the opportunity to put /home on a seperate partition if not already, the fact that you are running more up to date apps is probably a good thing, security updates, so on and so on.

Of course, all that assumes it runs as well as your current setup. :)

Good Luck.

---

### Post by slira on 2010-02-05
Hi All

Since I have to reinstall de OS I'm moving to Gentoo.
Thanks for all the support and help during my Ubuntu phase ;)
Ubuntu was my introduction to linux and I learned a lot with it.

Best
slira

---

