---
title: "HELP! Switch Ubuntu Hoary represitories"
date: 2009-11-13
forum: General Help
---

### Post by kio_http on 2009-11-13
How can I switch Hoary repositories to that of debian or Ubuntu 8.04?

Currently Hoary repositories no longer exist and give error 404.

---

### Post by kio_http on 2009-11-13
I really need to do this and keep my hoary system running

---

### Post by mikechant on 2009-11-13
The newer repositories (e.g. 8.04) won't be suitable for hoary. You'll probably break the OS if you use them.

Hoary is a *long* time out of support, and potentially may have big security holes particularly if you are using it for web browsing.

However, if you're determined to keep using it, **the old hoary repositories do still exist** - they just have a different address.

You need to edit /etc/apt/sources.list (after backing it up)
open a terminal with ALT+F2, then type the following commands:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list

and then change "us.archive.ubuntu.com" to "old-releases.ubuntu.com" wherever you find it (may start with something other than "us.")

Then you should be able to start synaptic or whatever you use for software installation and do a 'reload' and you should be able to install stuff again.

If you're not sure post a copy of /etc/apt/sources.list for us to check before you edit it.

But I would strongly recommmend you install a supported release (one of 8.04 long term support or 9.04 or 9.10) as soon as possible.

---

### Post by kio_http on 2009-11-13
> **mikechant said:**
> The newer repositories (e.g. 8.04) won't be suitable for hoary. You'll probably break the OS if you use them.


But I would strongly recommmend you install a supported release (one of 8.04 long term support or 9.04 or 9.10) as soon as possible.

Thanks a lot, but I know its long out but I really have no choice in this case, and no web browsing would be ok since my router is a good firewall and the latest opera installs.

Any chance of debian represitories?

---

### Post by Irony on 2009-11-13
> **kio_http said:**
> Any chance of debian represitories?
No

---

### Post by sisco311 on 2009-11-13
[uhelp]community/EOLUpgrades[/uhelp]

Upgrade Hoary 5.04 to Breezy 5.10 
Breezy 5.10 to Dapper 6.06.2
and Dapper to Hardy. 

have fun! :)

---

