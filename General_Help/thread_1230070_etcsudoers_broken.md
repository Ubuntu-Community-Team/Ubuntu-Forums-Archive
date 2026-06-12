---
title: "/etc/sudoers broken"
date: 2009-08-03
forum: General Help
---

### Post by ecmatter on 2009-08-03
I tried to alter my sudoers file, and now I have no sudo priveledges.  What I can't figure out is why it's not working.  I boot into recovery mode and:

```

visudo

-or-

vim /etc/sudoers

```and the file displayed is an exact replica of the default sudoers file for 8.04.  I enter:

```

:q

```to exit vim and it tells me that **/etc/sudoers.tmp** is unchanged.  Only there is no such file as /etc/sudoers.tmp?

I have no idea what to do at this point.  Initially, there was an /etc/sudoers.tmp.swp file and a list of instructions to follow, but I apparently screwed that up somehow...

What can I do to fix this?

---

### Post by kerry_s on 2009-08-03
the tmp thing is normal, it's buffered while your changing it.

if it's screwed up you can boot into safe mode and remove sudo then reinstall it.
in safe mode:
[B]apt-get remove --purge sudo
apt-get install sudo
[/B]

that will remove it completely then install it again just like new.

by the way only use "sudo visudo" or "visudo" in safe mode to edit sudoers! it is the "only" safe way to do it.

---

### Post by ecmatter on 2009-08-03
Thanks for the help kerry.

Problem: When I try to remove sudo, it wants to remove a *bunch* of packages, including gparted, network-manager-gnome, ubuntu-desktop, update-manager, update-notifier and several linux-headers.

I tried several different methods, 

```

apt-get remove --purge sudo
apt-get remove sudo
aptitude remove sudo_
apt-get remove sudo; apt-get install sudo

```

and they all lead to deleting the same packages.  Any ideas?  Or am I just going to have to reinstall everything?

---

### Post by cariboo on 2009-08-03
I would suggest checking if the permissions have changed. The permissions should be set to 440 it should look similar to this:

```
-r--r----- 1 root root 557 2009-07-09 12:44 sudoers
```

---

### Post by ecmatter on 2009-08-15
Update:  I reinstalled.  Removing sudo was a bad idea (almost as bad an idea as trying to edit the sudoers file).

Everything's good now.  Thanks for the suggestions.

---

