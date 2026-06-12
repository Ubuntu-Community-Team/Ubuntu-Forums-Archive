---
title: "Moving firefox and thunderbird settings to another disk"
date: 2010-02-04
forum: General Help
---

### Post by Admiral_Payne on 2010-02-04
It appears that my HDD is failing at the moment, so I'm going to replace it by two new disks (RAID1) over the weekend.
At the same moment I'll stick in another 6GB RAM. Because I'm currently running the 32-bit system, I'll be upgrading to 64-bit (doh).

Now then, is it possible to copy all Firefox and Thunderbird settings (settings, accounts, bookmarks, cookies etc) over to the other disk?
If so, which folder(s) do I have to copy?


Cheers,

---

### Post by x C0MMAND0 x on 2010-02-04
I believe all of the settings for a given application are located in /home/user/.mozilla for firefox and /home/user/.mozilla-thunderbird for thunderbird.

Can anyone else confirm this?

---

### Post by Admiral_Payne on 2010-02-04
Ahh, that appears to be what I was looking for. It looks like all the custom settings are in there, but will copying my home folder also include firefox addons? The .mozilla/extensions/ folder apperas to be empty apart from an empty folder :<

Also, will copying my home folder (or just these two folders) not give me any problems if I switch from 32-bit to 64-bit?

Thanks,

---

### Post by lovinglinux on 2010-02-05
> **Admiral_Payne said:**
> Ahh, that appears to be what I was looking for. It looks like all the custom settings are in there, but will copying my home folder also include firefox addons? The .mozilla/extensions/ folder apperas to be empty apart from an empty folder :<


Yes it will include all your settings, including extensions, which are stored under ~/.mozilla/firefox/profilename/extensions

Take a look at the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for some backup tips.

> **Admiral_Payne said:**
> Also, will copying my home folder (or just these two folders) not give me any problems if I switch from 32-bit to 64-bit?

You can switch to 64bit and keep your entire home folder. I did this a couple of weeks ago. If you have a separate home partition, then would be pretty easy. if not, then it is a good time to create one. 

Also take a look at [Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153) extension for installing all your applications after the re-installation of Ubuntu.

See [this](http://ubuntuforums.org/showthread.php?t=1358591) for instructions on how to install flash 64bit.

---

### Post by Admiral_Payne on 2010-02-05
Sweet, thanks for all the links. I think this will conclude my questions on the subject :)

---

