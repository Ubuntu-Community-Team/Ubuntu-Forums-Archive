---
title: "Accessing network shares"
date: 2010-09-21
forum: General Help
---

### Post by rmcellig on 2010-09-21
I am using Xubuntu 10.04 and can't find where I can create shares as well as access network shares. In Ubuntu I just go under Places/Network and there are my shares. How do you do this in Xubuntu?

---

### Post by searchfgold6789 on 2010-09-21
You must install the gnome package "gnome-user-share"

---

### Post by rmcellig on 2010-09-21
Thanks I will do that. I can then see all of my shares after that? Can I then access the shares from under Places?

---

### Post by Morbius1 on 2010-09-21
gnome-user-share sets up a baby apache file server that announces it's one and only share at /home/user_name/Public using avahi. Nothing wrong with that but it has nothing to do with accessing remote shares.

To create shares for others to access ( and I'm assuming Windows is in your network somewhere so I'm suggesting Samba ) you need to install:
```
thunar-shares-plugin
```[COLOR=Blue]*This will allow you to create shares from Thunar*[/COLOR]
OR:
```
system-config-samba
```[COLOR=Blue]*If you want to do it the traditional way*[/COLOR]

To access shares on other machines then I'd suggest Gigolo

---

### Post by rmcellig on 2010-09-21
Thanks Morbius1!! I will try what you suggest. I have a computer running windows, one running Mac OS 10 and another one running Ubuntu. I need to connect and be able to share files with all of them.

---

### Post by Morbius1 on 2010-09-21
There is something I forgot about Gigolo. It's dependencies aren't quite right in that it needs one more package for everything to work:
```
gvfs-fuse
```I don't remember if xubuntu installs that as part of the base install or not so you should check to see if it's there.

---

### Post by rmcellig on 2010-09-21
Thanks

---

