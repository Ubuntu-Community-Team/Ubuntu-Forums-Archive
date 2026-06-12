---
title: "How do you change a certian window setting???"
date: 2006-05-11
forum: General Help
---

### Post by morbid_bean on 2006-05-11
There has to be some possible way to make it where you can disable the animation when you minimize a window.?

---

### Post by ElijahLofgren on 2006-05-11
From: [http://lists.debian.org/debian-user/2005/01/msg01088.html](http://lists.debian.org/debian-user/2005/01/msg01088.html)
> 
On Fri, 2005-01-07 at 21:35 +0700, David Garamond wrote:
> I'm using Sarge with GNOME 2.6 (haven't updated to 2.8). There's a
> 'shrinking box' animation when you minimize a window. How do I disable
> it? It gets pretty annoying after a while.

You'll want to set /apps/metacity/general/reduced_resources to True
using either Applications->System Tools->Configuration Editor or running
"gconftool-2 -t bool -s /apps/metacity/general/reduced_resources true"

-Mark


Hope this helps ;)

---

