---
title: "Problems with update manager"
date: 2011-08-28
forum: General Help
---

### Post by Jim_in_Germany on 2011-08-28
Hi,

Just installed 11.04 and tried to run the update manager.
The update manager finds a load of updates, the first one, for example, is: Advanced front-end for dpkg

However, when I click on OK, then I get the following error and update manager dies.
Failed to fetch [http://lu.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_0.4.3-0ubuntu3_amd64.deb](http://lu.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_0.4.3-0ubuntu3_amd64.deb) 403  Forbidden

I opened Firefox and tried to navigate to the folder where the update manager is looking for the deb package.

I got as far as [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/), then see the following "Archive-Update-in-Progress-syowa.canonical.com"

I'm guessing the archive is being updated (surprisingly).
Does anyone have any idea how long this normally takes?
The Archive-Update message is from 27-Aug-2011 18:03 and 24 hours seems quite a while.

Thanks in advance

---

### Post by tredegar on 2011-08-28
> However, when I click on OK, then I get the following error and update manager dies.
Failed to fetch [http://lu.archive.ubuntu.com/ubuntu/...ntu3_amd64.deb](http://lu.archive.ubuntu.com/ubuntu/...ntu3_amd64.deb) 403 Forbidden
The link hasn't been pasted properly, please try again.


But the address starts with lu - which is the country code for Luxembourg. Why are you using that if you are in Germany?

Maybe try again after you have edited **/etc/apt/sources.list** replacing **[COLOR="Red"]lu[/COLOR].archive** with **[COLOR="Red"]de[/COLOR].archive** ?

Then you'll need to so a **sudo apt-get update**

---

### Post by Jim_in_Germany on 2011-08-29
Hi,
No idea why Ubuntu is trying to use a repo in Luxembourg - it was a clean install.
Anyway, changing the "lu" to "de" and running "sudo apt-get update" completely solved the problem.
Thank you very much indeed for your help!

---

