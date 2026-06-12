---
title: "Why doesn't alacarte clean up?"
date: 2010-04-12
forum: General Help
---

### Post by x-shaney-x on 2010-04-12
Ever since I first discovered alacarte (gnome menu editor) I have been creating lots of menus and submenus for gnome menu so I can always find what I want.

To avoid having to redo them, whenever I try another gnome based distro or do a fresh install I always copy ~/.local/share/desktop-directories and applications (and a couple of other files, I forget right now) so I can use the same menus in those.

Well, I don't use these custom menus so much lately so have gone for a much simpler solution of creating a "Favourites" submenu and just adding apps I use a lot.

It was while rummaging around .local today I noticed there are hundreds of left over files from long since deleted custom menus (like 18 months+) that I have been copying from one distro to another all this time.

Why on earth doesn't alacarte delete all these deleted menus and applications files? 

I just did a little experiment:
I deleted everything out of these folders so I was basically left with the stock gnome menu with no customizations.
I then added a new submenu and then added 3 random apps to to it.
I then went and deleted two of those apps and when I went to check, sure enough ~/.local/share/applications contained the 3 files instead of one.

---

### Post by dcstar on 2010-04-13
> **x-shaney-x said:**
> Ever since I first discovered alacarte (gnome menu editor) I have been creating lots of menus and submenus for gnome menu so I can always find what I want.
........
Why on earth doesn't alacarte delete all these deleted menus and applications files? 
........

Probably because no one - including you - has reported this as a bug?

---

### Post by cong06 on 2010-04-13
It's also possible that it's allowing more control over customization.

Consider this.
If you add a menu, thereby changing the default, it makes an icon.

Now, this is exactly how you want it.

If for some reason the default changes (ie, you reinstall a newer version of firefox and the ubuntu devs decide that firefox shouldn't be showing on the menu at all) then your changes would still override the default.

So I don't consider it a bug so much as a feature that causes alot of mess.
That's why I usually don't venture into the ".*" folders unless I need to retrieve something.

Not to mention that actually cleaning up the mess would be pretty messy code (I imagine).

---

