---
title: "Shell scripts storage location(s)"
date: 2010-02-03
forum: General Help
---

### Post by jhigz on 2010-02-03
I apologize if this has been asked, I had no luck searching it out. Is there any reason I should not store shell scripts in the /usr/local/bin folder? Would an upgrade to Ubuntu at a later date overwrite this folder? If this is not considered the best location for these types of files, please advise me as to a better choice/method for there storage.



Thanks...

---

### Post by Brandon Williams on 2010-02-03
When you write programs (whether scripts or compiled binary files) that need to be available to all users on a multi-user system, then yes, /usr/local/bin is generally a good place to put them. Standard packages should not install anything to that directory that might over-write your programs. However, if you install custom software from tar-balls, you should be careful to ensure that it will not over-write your programs, since custom software will often install to /usr/local/bin by default.

If it is not a multi-user system and/or the script only needs to be accessible by you, then it's generally best to put them in your own $HOME/bin/ directory (create it if necessary). The standard system profile for bash will add this to your PATH if it exists.

Another issue to consider is how your filesystem is structured and the method you tend to use for distro upgrades. If /usr/local is part of the same filesystem as /usr, then everything in it will be lost if you tend to "upgrade" by performing a fresh install from CD. The same is true of your /home directory if it's part of the root filesystem, but many of us always put /home on a filesystem of its own so that it is not over-written by a clean install.

---

### Post by jhigz on 2010-02-03
Brandon,

Thank you for offering perspective I frankly hadn't considered. I do store /usr and /usr/local on separate partitions so that concern is addressed. Until recently, I had been running Debian for some time and any upgrade was done by way of fresh cd install.

To date, I have not installed custom software, but did not even consider the potential conflict it may create. It is not a multi-user system so I believe I'll use ~/bin as you suggest.

Thanks again.

---

### Post by Lars Noodén on 2010-02-04
If you haven't already, see also the manual page [hier(7)](http://manpages.ubuntu.com/manpages/karmic/en/man7/hier.7.html).

---

### Post by jhigz on 2010-02-04
No I hadn't, until now.

Thanks...

---

