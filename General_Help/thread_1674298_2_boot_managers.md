---
title: "2 boot managers?"
date: 2011-01-23
forum: General Help
---

### Post by xrc6 on 2011-01-23
first i see Windows boot manager and must select, then if i choose Ubuntu i see yet Grub and must select again...how do i get rid of one?
i want to check out Burg so i can use a better looking boot manager. i'm hoping it will allow me to choose with my mouse, i hate using the kb.

---

### Post by oldfred on 2011-01-24
If your first choice is windows/grub you must be using wubi. I would not use burg as that takes over from grub, but you are not really using grub to boot, but are using windows. Grub in wubi is just to make it look like a standard install.

You can in both windows and grub set timeout to be less. Those that have set timeout to zero often then have issues, so short is ok, but zero can be an issue.

---

### Post by bcbc on 2011-01-24
+1 as oldred said, do not set timeout to zero with Ubuntu as the default or Windows cannot boot.
Do not install burg - this will prevent either OS from booting.

If you want to get rid of any menu, it's the grub menu - but grub makes that difficult as it refuses to be suppressed if it detects multiple OS's present. You can try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:#Step_1_Enable_the_Hidden_Menu_feature](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:#Step_1_Enable_the_Hidden_Menu_feature).
Please note that the above guide was written some time back so use with appropriate caution.

---

### Post by xrc6 on 2011-01-26
not sure i understand...can i not just use one boot screen to select the OS? Its annoying to select Linux for the Windows boot menut, then have to select it yet again in grub.
Why can't either one just take me to the OS i choose?

---

### Post by bcbc on 2011-01-26
The windows boot manager boots either Windows or Ubuntu. If you set it to boot Ubuntu by default, then set the timeout to zero, what will happen is this:

BIOS --> Windows Boot Manager (hidden) --> Ubuntu Grub
If you then select Windows it will do this:
Ubuntu Grub --> Windows Boot Manager (hidden) --> Ubuntu Grub.

In other words - you can no longer boot Windows.

If you instead hide Grub (using that guide I linked to):
BIOS --> Windows Boot Manager
If you select Windows:
Windows Boot Manager --> Windows
If you select Ubuntu:
Windows Boot Manager --> Grub (hidden) --> Ubuntu

So by hiding Grub you can still boot both OS's. Also, if you hold down SHIFT when booting Ubuntu, Grub should unhide itself so you can still select recovery mode (if required).

Personally, I'd just hit Enter twice.

When you decide to migrate to a normal Ubuntu install, then you can have BIOS --> Grub or Burg (and no Windows Boot Manager) prompt).

---

