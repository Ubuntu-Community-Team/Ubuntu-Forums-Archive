---
title: "No text in KeePass menus (could be problem with Mono and video driver?)"
date: 2011-08-14
forum: General Help
---

### Post by DarrenCarlton on 2011-08-14
I'm running Ubuntu 11.04, and I've installed KeePass 2.16 from the ppa:jtaylor/keepass repository as described here: [http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818](http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818)

When I start KeePass, all of the menu text is missing, and I see tiny squares instead. See the attached screen shot.

Other people had this problem back in Ubuntu 10.x with an intel video driver older than xserver-xorg-video-intel
2:2.9.1. (See [https://bugzilla.novell.com/show_bug.cgi?id=549882](https://bugzilla.novell.com/show_bug.cgi?id=549882)).

However, I have the 2:2.14.0 version installed.

Does anyone know what's wrong?

---

### Post by directhex on 2011-08-16
> **DarrenCarlton said:**
> I'm running Ubuntu 11.04, and I've installed KeePass 2.16 from the ppa:jtaylor/keepass repository as described here: [http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818](http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818)

When I start KeePass, all of the menu text is missing, and I see tiny squares instead. See the attached screen shot.

Other people had this problem back in Ubuntu 10.x with an intel video driver older than xserver-xorg-video-intel
2:2.9.1. (See [https://bugzilla.novell.com/show_bug.cgi?id=549882](https://bugzilla.novell.com/show_bug.cgi?id=549882)).

However, I have the 2:2.14.0 version installed.

Does anyone know what's wrong?

Can you try installing [apt:libmono-i18n2.0-cil](apt:libmono-i18n2.0-cil) if you don't have it already?

---

### Post by DarrenCarlton on 2011-09-04
I already have it installed.

---

