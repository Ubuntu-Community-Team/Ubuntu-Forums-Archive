---
title: "menu in wrong place"
date: 2010-10-23
forum: General Help
---

### Post by bawkqsz on 2010-10-23
So I'm new, not to Ubuntu, but to the whole posting a new thread thing, but I'm pretty sure no one else was stupid enough to encounter this problem before so I think I'm the first. But I'm not so good with the forum-searching tool so I may be wrong, and I'm sorry if this is a duplicate thread.

Anyway, the problem I have is the fact that I was pruning my menus by turning on and off some things in the Applications and System menus, and I accidentally moved one menu inside another by accidentally clicking and drag-dropping it inside another. I was wondering how I managed to do this (wasn't really paying attention when it actually happened) and tested it with another menu or two, and now my Sound & Video, Internet, and System Tools menus are nested inside of the Science, Programming, and Office menus, respectively (first, second and third screenshots). And I rather like them being their own separate menus, ya know? (as in, directly under the Applications, as opposed to a subset of another set) I tried drag-dropping them back in the Edit Menus app (last screenshot) but that doesn't work for some reason; I can only drag-drop each menu as another sub-menu (so I could have all three problems inside, say, the Accessories menu, but that's still not what I want).

Is there a way to make each one its own full menu again, as opposed to a sub-menu?

---

### Post by D4rkEclipse on 2010-10-23
Any luck choosing the "revert" option in menu editor?

---

### Post by Verbeck on 2010-10-23
clicking "revert" should fix the problem

---

### Post by bawkqsz on 2010-10-23
Nope. I must've hit that about ten or twelve times now, at various points in time over the last few days, and the first few times it did absolutely nothing, and the last time all it did was revert the Preferences and Administration menus to their original forms, but not the others (which was a pain to "fix" the pruning of, but would've been worth it if it had reverted correctly).

---

### Post by D4rkEclipse on 2010-10-23
I was just now able to recreate your problem on my computer, and it seems to work just dragging them into the "Applications" menu from the menu editor. However, revert also worked for me. So maybe the problem is with something else. Have you made any changes to any kind of menu configuration file?

---

### Post by Verbeck on 2010-10-23
Try this:
run **gedit .config/menus/applications.menu** and replace the contents with the following:
```

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
<Name>Applications</Name>
    <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

```

---

### Post by bawkqsz on 2010-10-23
Ah! Thanks, to both of you. Drag-dropping it like that fixed the problem, but when I looked at the file in question that Verbeck pointed out, I realized it is an endless morass of total crap, so resetting that then re-pruning it also fixed the problem like a charm, and got rid of a bunch of useless stuff.

Although, Revert still doesn't do anything. . . . Didn't even fix the Preferences and Administration menus this time.

As far as I know, I haven't changed any menu config files directly through gedit or other applications. But I have customized this desktop beyond belief throughout the years, over several versions of Ubuntu, so I'm sure something could've easily gotten messed up somewhere. . . .

---

