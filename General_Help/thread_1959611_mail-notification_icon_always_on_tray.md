---
title: "mail-notification icon always on tray"
date: 2012-04-16
forum: General Help
---

### Post by tanoloco on 2012-04-16
Hello,

I'm running mail-notification (Mail Notification version 5.4) on lubuntu oneiric.
I would like to have its icon always on my tray, and not only when a mail arrives.
I found this post [http://ubuntuforums.org/showpost.php?p=10474777&postcount=7]("http://ubuntuforums.org/showpost.php?p=10474777&postcount=7") explaining how to do it with gnome,
but how to do it on lxde?

Thank you

---

### Post by croque on 2012-05-01
Here's what I did to solve this:

```
leafpad ~/.gconf/apps/mail-notification/%gconf.xml
```and add the following line after the <gconf> tag:

```
<entry name="always-display-icon" mtime="1320676101" type="bool" value="true"/>
```You might have to restart for it to take effect.

---

### Post by tanoloco on 2012-05-02
It works great! Many thanks :D
BTW: ending session and logging in again was enough.

---

