---
title: "No icons on my desktop."
date: 2004-10-19
forum: General Help
---

### Post by Neo40 on 2004-10-19
Hello,

This is my first installation of Ubuntu. So far, it's pretty nice! :)
When Gnome starts, everything is working but I don't have icons on my desktop.Is it the normal configuration  or I'm missing something?

Thanks in advance.

---

### Post by JProgrammer on 2004-10-19
Yep this is normal Ubuntu doesn't have icons on the desktop by default

---

### Post by pocket on 2004-10-19
I like a clean desktop, but I deleted the little trash utility from the taskbar and I'd love to get a trash can on the desk.  How do I do it, links and whatnot don't seem to make it functional like the old gnome trash can.

---

### Post by LongTooth on 2004-10-20
I too am a 'clean' desktop advocate. Very little is on any distro I've installed. I like the clean uncluttered way Ubuntu has their desktop. But!...and there is always a but...I also would like the trash can on the desktop. I can do without everything else. It's a minor nitpick. But I'd like to know how to put a trash can on the desktop. Thanks.

---

### Post by Jspired on 2004-10-20
Love the clean desktop and really like the trash icon on the toolbar and not the desktop.  To each his own, I suppose..

---

### Post by cybrjackle on 2004-10-20
[ Ubuntu FAQ](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-16.1393795212)

> Applications &gt; System Tools &gt; Configuration Editor, navigate to /apps/nautilus/general, and choose the icons you want to appear.

---

### Post by nOmArch on 2007-11-27
doesn't work.  have messed about with gconf-editor and whatever options i choose my trash can refuses to appear on either my desktop on panel :(

---

### Post by geirha on 2007-11-27
Trashcan in the notification area:
Rightclick an "empty" spot on the toolbar (where there's no icons), choose Add to panel, and choose the trashcan in the window that pops up.

Trashcan on the desktop:
run gconf-editor
Browse to apps -> nautilus -> desktop and enable trash_icon_visible

---

