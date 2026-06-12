---
title: "Open terminal in specific desktio"
date: 2011-12-05
forum: General Help
---

### Post by Cool Javelin on 2011-12-05
Hello all:

Can someone please tell me how to open a terminal in a specific desktop when booting?

I used "System" "Preferences" "Startup Applications" and added a 'gnome-terminal..." and it seems to work, but it comes up in the first desktop, and I would like to come up in another.

Later, I would like a few different ones to come up in other desktops too.

I am sure this has been dealt with before, but searching didn't yeald any results.

Ubuntu 10.10 Desktop using Gnome.

Thanks, Mark.

---

### Post by collisionystm on 2011-12-05
> **Cool Javelin said:**
> Hello all:

Can someone please tell me how to open a terminal in a specific desktop when booting?

I used "System" "Preferences" "Startup Applications" and added a 'gnome-terminal..." and it seems to work, but it comes up in the first desktop, and I would like to come up in another.

Later, I would like a few different ones to come up in other desktops too.

I am sure this has been dealt with before, but searching didn't yeald any results.

Ubuntu 10.10 Desktop using Gnome.

Thanks, Mark.


if you were using 11.10 with gnome-shell you would have figured this out already ;)

extensions.gnome.org has exactly what you want lol.

---

### Post by Toz on 2011-12-05
> **Cool Javelin said:**
> Hello all:

Can someone please tell me how to open a terminal in a specific desktop when booting?

I used "System" "Preferences" "Startup Applications" and added a 'gnome-terminal..." and it seems to work, but it comes up in the first desktop, and I would like to come up in another.

Later, I would like a few different ones to come up in other desktops too.

I am sure this has been dealt with before, but searching didn't yeald any results.

Ubuntu 10.10 Desktop using Gnome.

Thanks, Mark.

You could use **devilspie**. See: [http://burtonini.com/blog/computers/devilspie/]("http://burtonini.com/blog/computers/devilspie/") and [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie").
You could use a config file like:
```
(if (is (application_name) "gcolor2")
	(begin
		(set_workspace 2)
	)
)

```
...this will start the application gcolor2 on the second workspace.

---

