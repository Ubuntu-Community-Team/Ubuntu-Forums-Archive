---
title: "Getting a list of files not owned by any package?"
date: 2011-02-07
forum: General Help
---

### Post by rang501 on 2011-02-07
Hi!

I'm pretty sure that I have some unneeded files laying around on my system. Most of them are created with "make install" command.

To remove them, I need to get list of files which are not owned by any package. How can I do that?


[I]
There is a way in Arch Linux: [https://wiki.archlinux.org/index.php/Pacman_Tips#Getting_a_list_of_files_not_owned_by_any_package](https://wiki.archlinux.org/index.php/Pacman_Tips#Getting_a_list_of_files_not_owned_by_any_package)[/I]

---

### Post by geirha on 2011-02-07
I avoid that issue by always installing non-packaged software under /usr/local, /opt, or in my homedir.

But anyway, dpkg stores lists of files installed by each package as /var/lib/dpkg/info/*.list

So something like ```
comm -23 <(find / -xdev -type f|sort) <(sort /var/lib/dpkg/info/*.list)
``` might be what you want, though please note that I haven't tested that.

---

### Post by rang501 on 2011-02-07
It was almost what I wanted. I think my system is a lot cleaner now. There were some files I didn't want to delete, because they appeared to be owned by some packages.

Thank you!

---

### Post by sisco311 on 2011-02-07
In Ubuntu you can use *checkinstall* instead of *make install*.

See:
[uhelp]community/CheckInstall[/uhelp]

---

