---
title: "Problem with overwritten PPA repository"
date: 2012-09-29
forum: General Help
---

### Post by AudioFlux on 2012-09-29
I had an existing ppa repo source of wine in my software sources, but I realized that wine never existed on my drive in the first place. So, I went to add the repository again, thinking that even if the previous one existed, it would be overwritten. Unfortunately, I was wrong. Now the whole updating process is messed up. On the taskbar, I see a red circle with a minus sign on it. It says, "A problem occurred when checking for the updates", and when I click on show updates, I get this:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list'

This error prevents me from opening Ubuntu Software Centre as well.

Any help is much appreciated :)

---

### Post by oldos2er on 2012-09-29
Open the file in a text editor: ```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
``` and change the **b-src** to **deb-src**
Lines in any sources list must begin with either deb or deb-src.

But if you already had this repo enabled (if I'm understanding you correctly), why would you want to add it again? I don't think it would be overwritten; and you may see a "duplicate sources" warning.

---

### Post by AudioFlux on 2012-09-29
Thanks, that did the trick :)
I had installed wine before adding the repository the first time, but for some reason wine got removed once I updated. So I thought that it was something to do with the repository, and I added it again. It didn't get overwritten, but I did not get a "duplicate sources" warning either. I tried to fix it by removing both the repos, but that did not do anything.

Again, thanks for your help.

---

### Post by oldos2er on 2012-09-29
You're welcome. Would you please mark the thread as 'Solved' under Thread Tools?

---

