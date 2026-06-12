---
title: "mint menu in ubuntu?"
date: 2009-08-27
forum: General Help
---

### Post by themusicalduck on 2009-08-27
I've been playing with Mint a little and I seriously like the look of it, so much that I'm tempted to give it a go as a permanent switch. However, I want to give Karmic a go first before switching over.

Anyway, one thing I really loved was the mint menu, is it possible to get this working well in Ubuntu?

I downloaded mintmenu and mintsystem from this website: [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

And I can now add mint menu to a panel, and everything generally works, except that the applications do not show. I have all the categories listed, but when I mouseover, nothing shows. Also the filter doesn't work either, but I guess that's not surprising.

I've heard of successes doing this, but many of the threads are dated, so I'm wondering if it's still possible or not to do?

---

### Post by themusicalduck on 2009-08-27
Nevermind, I fixed it.. realised that link was for an old repository.

If anyone else wants to know, I added this to my software sources:

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) gloria main upstream import

Then downloaded mint menu from the repos and removed it again.

Or just downloading from here would probably work:

[http://packages.linuxmint.com/](http://packages.linuxmint.com/)

---

### Post by Villiam on 2009-08-27
Thank you for your question and the subsequent solution. It will help me setting my friend mint menu.  Actually one just have to  follow the links. Thanks anyways

---

### Post by themusicalduck on 2009-08-27
I have found another problem now. I'd like if possible for the ubuntu add/remove to run when I click on Software manager.

I changed the key in gconf-editor under /apps/mintMenu/plugins/system-management/install_software_cmd to /usr/bin/gnome-app-install, but it just won't run.

---

