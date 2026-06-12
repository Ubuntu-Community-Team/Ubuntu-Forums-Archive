---
title: "wallpapers, Ubuntu 10.04"
date: 2010-06-27
forum: General Help
---

### Post by Cavsfan on 2010-06-27
I have copied several pictures into /usr/share/backgrounds/.
But, the new ones do not show up when I click on desktop and Change Desktop Background.

I put about 100 wallpapers in that folder, fixed file attributes to match the existing wallpapers and even rebooted and they still do not show up. ](*,)

Any clue as to why this is happening?
Thanks

---

### Post by RedRat on 2010-06-27
> **Cavsfan said:**
> I have copied several pictures into /usr/share/backgrounds/.
But, the new ones do not show up when I click on desktop and Change Desktop Background.

I put about 100 wallpapers in that folder, fixed file attributes to match the existing wallpapers and even rebooted and they still do not show up. ](*,)

Any clue as to why this is happening?
Thanks
This might sound strange, but when you click on the Desktop and select "Change Desktop" the program only sees an xml file. You need to manually add each of those extra pictures to get them listed. You can't just copy them into /usr/share/backgrounds and be able to use, at least not in 8.04. I had the same problem and had to get them in manually by clicking on the "ADD" button. Good Luck.

---

### Post by dcstar on 2010-06-28
> **Cavsfan said:**
> I have copied several pictures into /usr/share/backgrounds/.
But, the new ones do not show up when I click on desktop and Change Desktop Background.

I put about 100 wallpapers in that folder, fixed file attributes to match the existing wallpapers and even rebooted and they still do not show up. ](*,)

Any clue as to why this is happening?
Thanks

Right-click, select Change Desktop Background then "Add" and select all the new files you copied, then they will be available to that user.

This may also work:

[http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide](http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide)

---

### Post by Cavsfan on 2010-06-28
I should have known!  I just selected each of them with the Add button.
I didn't really want to edit XML files as I would probably just mess that up.

Thanks!

---

