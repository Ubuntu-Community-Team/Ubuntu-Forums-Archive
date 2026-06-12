---
title: "Help WindowList - can't find running apps"
date: 2010-03-14
forum: General Help
---

### Post by Dusenberg on 2010-03-14
Help please!

I have 4 workspaces set up and they appear on the bottom menu bar. Usually I can switch to each and see what's running in each, even if the apps are minimised. Now I can only see what hasn't been minimised, and I can't see or return to the ones that are minimised...  System Monitor shows the minimised apps are running...  I was poking around gconf editor late the other night and I must have altered a setting but I have no idea which. I've looked through docs etc but can't find a solution.  

Anyone any ideas????

---

### Post by Dusenberg on 2010-03-14
Bump...

Can anyone help????

This is Gnome desktop on 8.10 Intrepid, and its stopped me working :mad:

Is it possible to desktop restore default settings?

---

### Post by howefield on 2010-03-14
Try opening a terminal and typing/executing these three commands.

```
gconftool –-recursive-unset /apps/panel
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

---

### Post by Dusenberg on 2010-03-14
> **howefield said:**
> Try opening a terminal and typing/executing these three commands.

```
gconftool –-recursive-unset /apps/panel
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

Thanks Howefield, mush appreciated. Tried that but still can't see the minimised windows. I can't see anything in gconfeditor that should cause this..... at least I've found I can ctrl-alt-tab to the minimisied windows which is something.... but it's still not good

---

### Post by howefield on 2010-03-14
I'd have thought the above would have taken care of it, but I suppose you could check that you have "Window List" on your panel.

Right click panel > Add to Panel > Window List

---

### Post by Dusenberg on 2010-03-14
> **howefield said:**
> I'd have thought the above would have taken care of it, but I suppose you could check that you have "Window List" on your panel.

Right click panel > Add to Panel > Window List

You cracked it Howefield):P

How I missed the fact that it wasn't running...!!!!  I thought the miniature screens on the bottom panel *were* Window List- doh!

THANKS A MILLION!!!!

---

### Post by howefield on 2010-03-14
> **Dusenberg said:**
> You cracked it Howefield):P

That's good to know, not sure why the first suggestion didn't work, it should put your panels back to default, which includes "Window List"

No matter, thanks for letting us know you are sorted.

PS. The  "miniature screens" are called the Workspace Shifter.

---

