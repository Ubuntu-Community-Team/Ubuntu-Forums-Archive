---
title: "Why do I receive updates for removed software?"
date: 2009-07-07
forum: General Help
---

### Post by MockY on 2009-07-07
I don't use Pidgin since I find Emesene vastly much better, and I therefore uninstall it as soon as I install Pidgin. So why is it that I receive updates for Pidgin even though it's removed from the system?

These are the packages belonging to Pidgin:

pidgin-data
libpurple0
libpurple-bin

---

### Post by Agent ME on 2009-07-07
If you have a package installed, you will receive updates for it. Remove those packages if you don't want to receive updates for them.

---

### Post by philinux on 2009-07-07
> **MockY said:**
> I don't use Pidgin since I find Emesene vastly much better, and I therefore uninstall it as soon as I install Pidgin. So why is it that I receive updates for Pidgin even though it's removed from the system?

These are the packages belonging to Pidgin:

pidgin-data
libpurple0
libpurple-bin

Post 2 is wrong.

Packages that are available in the ubuntu repos get updated to the latest version even if they are installed or not installed. Thats just the way it is.

---

### Post by c0mput3r_n3rD on 2009-07-07
In other words, you can't really get rid of the stuff Ubuntu comes with. I mean you can if you really try.... but for the most part it's there for ever :D

---

### Post by Agent ME on 2009-07-07
> **philinux said:**
> Post 2 is wrong.

Packages that are available in the ubuntu repos get updated to the latest version even if they are installed or not installed. Thats just the way it is.
Er, what? If you remove a package, it will not get updated and reinstalled *(unless another package you have was updated to include the removed package as a dependency)*.

There is a lot of software in the Ubuntu repos, and I'm pretty sure I haven't been receiving updates for stuff like Apache that I don't even have installed.

I've been able to remove software Ubuntu has by default. I normally kill Evolution as the first thing I do as I use Thunderbird instead.

---

### Post by ibutho on 2009-07-07
> **MockY said:**
> I don't use Pidgin since I find Emesene vastly much better, and I therefore uninstall it as soon as I install Pidgin. So why is it that I receive updates for Pidgin even though it's removed from the system?

These are the packages belonging to Pidgin:

pidgin-data
libpurple0
libpurple-bin

Seems to me that when you uninstalled Pidgin, you did not remove the packages listed above, and thats why you are still receiving updates for them.

---

### Post by MockY on 2009-07-07
I thought doing
```
sudo apt-get autoremove pidgin
```
would remove everything belonging to pidgin. As in, that action is the same as removing it via Synaptic. If that is not the case, how do you keep your system from being littered with packages you don't need or use that you specifically removed?

Like Agent ME said, I don't receive Apache updates on my systems with Apache not installed. And since Pidgin is not installed anymore, it's odd that I still receive updates for it.

---

