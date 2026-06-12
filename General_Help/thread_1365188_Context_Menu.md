---
title: "Context Menu"
date: 2009-12-26
forum: General Help
---

### Post by elkade on 2009-12-26
I am using Karmic Koala.  When I right click on a folder, the sharing option is missing.  I am trying to share some folders for visibility in my network.

If more info is needed please inform me.

Thanks,

Larry

---

### Post by jonest1 on 2009-12-26
I took a quick look at this and you may want to check if the nautilus-share package is installed.

Run 'aptitude search nautilus-share' and if there is an i in front of the returned line item, it is installed and there must be some other issue.

If not, install with 'apt-get install nautilus-share'.  I'm not sure if you will need to log out of gnome or not for the change to take affect.

---

### Post by elkade on 2009-12-27
jonest1, thank you for the quick reply to my post.  pi was in front of the line item, so I followed the install instructions and now have the ability to share.  I did have to reboot.

Larry

---

