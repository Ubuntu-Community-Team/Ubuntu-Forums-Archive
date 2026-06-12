---
title: "Firefox Help"
date: 2010-07-14
forum: General Help
---

### Post by Ismar on 2010-07-14
Whenever a new URL is trying to be accessed, it will search if it does not include www. or http:// it takes a bit more of time. I have a habit of just typing SiteExample.com instead of [www.SiteExample.com]("http://www.SiteExample.com") or [http://SiteExample.com](http://SiteExample.com), and sometimes when logging into sites and clicking links it will leave out the prefix when redirecting me and cause a delay. Is there a way to disable this?

Also if someone could suggest some Applications and such since I just installed this Ubuntu on my computer and so far I'm loving it!
Thanks!!
Ismar. :p

-EDIT-
Not only this but any new link I click will look up or search first, please is any one knows how to fix this tell me :D

---

### Post by lovinglinux on 2010-07-14
I don't understand the question. It makes no difference in page loading time when using [http://www](http://www) or not. Are you referring to the search suggestions that appear on a popup box when you type something in the address bar?

I would first disable ipv6 too see if there is any difference. It is recommended to do it any way, since it can slow down connections to new pages.

Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

---

### Post by Ismar on 2010-07-16
Yeah that is what I meant, Thanks for the help!!

---

### Post by techunit on 2010-07-17
Hi there are tons of great applications... Just look in the application manager for GIMP which is basically the equivalent of photoshop in ubuntu. Other than that I can recommend you check out my video tutorials (look in my signature) they cover just about everything... and if you don't find what your looking for leave a comment of the suggestions page so the next person I direct there can find it.

I hope this helps you a little...

Other great applications

Gimp

Gnome-Do

Inkscape

Supertux 2 (game)

Thunderbird (mail client from the makers of Firefox)

and more just look at the recommended section of the application manager...

Really hope this helps...

---

### Post by lovinglinux on 2010-07-17
> **Ismar said:**
> Yeah that is what I meant, Thanks for the help!!

So it was fixed by disabling ipv6?

---

