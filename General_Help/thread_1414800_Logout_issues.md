---
title: "Logout issues"
date: 2010-02-24
forum: General Help
---

### Post by pan69 on 2010-02-24
I'm running Ubuntu 9.04 desktop with Gnome and since recently when I logout I'm presented with a sudo pop-up stating that there is still another user logged in. I normally only see this popup when there actually IS another user logged, but there is not. I'm the only one.

I have this issue since a week or so. Does anyone know what's going here?

Any help much appreciated.

---

### Post by pastalavista on 2010-02-24
Try making sure all your apps are closed out before logging out. Check in System|Administration|Users and Groups to see what other "users" have been added to your system by applications that create user accounts, sometimes with root permmissions.

---

### Post by pan69 on 2010-02-24
Thanks for your quick reply.

I have no open applications. As a matter a fact, this issue also occurs even when I shutdown directly after I've logged in. I normally only get this behavior when e.g. my girlfriend is still logged in. But in this case I'm the only one who's logged in. The issue started about a week ago.

when I open a console and use the 'users' command I see the following output:

pan69 pan69

As if I'm logged in twice. I haven't opened any TTY's other than the normal graphics one that's started after logging into Gnome. When I check the users under System|Administrator|Users and Groups I see myself, my girlfriend and root.

Still not sure what's going on here.

---

