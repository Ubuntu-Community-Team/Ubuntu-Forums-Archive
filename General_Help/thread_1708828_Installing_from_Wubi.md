---
title: "Installing from Wubi"
date: 2011-03-17
forum: General Help
---

### Post by Azaz on 2011-03-17
I originally installed linux with Wubi and I am very satisfied with it.  I was mainly wondering if I could do a proper duel boot without having to uninstall Wubi and lose all the stuff I did on ubuntu. Also how would I go about doing this?

(thanks ubuntu forums you rock:guitar:)

---

### Post by mastablasta on 2011-03-17
no you can't because you installed it within windows. unless you install it on spearate parittion but it will still be different.
 
My suggesiton is to use some backup tool (for example a simple one to use is LinuxMint backup tool) to backup your home folder and programme settings. then uninstall wubi, create partition and do a side by side install or whatever you want. then when  it's done you just move the files back (again with linux mint backup tool). and you're done.
 
.

---

### Post by seawolf167 on 2011-03-17
When you save your home folder, unless you are only saving things like documents, music, videos, etc., ensure that you save it to an extX formatted disk drive otherwise you program settings (Firefox, etc.) that reside in your home folder may not transfer over correctly.

As usual, before making any changes to your computer and starting the dual boot installation, I suggest imaging you hard drive with [Clonezilla ]("http://www.clonezilla.org")so you can restore and try again if something goes wrong.

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is a how-to guide for installing alongside Windows.

---

### Post by ChipOManiac on 2011-03-17
> **Azaz said:**
> ...without having to uninstall Wubi and lose all the stuff I did on ubuntu

By all the stuff do you mean the applications? If so I think it will be rather a rather heavy task. I think WUBI depends heavily on Microsoft WIndows ©®(TM) since it runs from WITHIN it... 

Simplest you can do is just backup your /home/ data and reinstall using the CD with a dual boot... Trying to do a dual boot from the WUBI Would mean playing around with the Microsoft Windows ©®(TM) Boot Selector (Not a Good Idea)...

---

### Post by Rubi1200 on 2011-03-18
> **Azaz said:**
> I originally installed linux with Wubi and I am very satisfied with it.  I was mainly wondering if I could do a proper duel boot without having to uninstall Wubi and lose all the stuff I did on ubuntu. Also how would I go about doing this?

(thanks ubuntu forums you rock:guitar:)
I am going to have to respectfully disagree with most of the comments made in response to your post.

If you want to migrate your Wubi install to a dedicated partition on the hard-drive, see this excellent guide by forum member bcbc:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

This will allow you to keep all your current settings, files, installed programs etc. but in a proper dual-boot configuration.

If you need specific help, ask bcbc in that thread. I am sure he will be happy to help.

---

### Post by ChipOManiac on 2011-03-19
> **Rubi1200 said:**
> I am going to have to respectfully disagree with most of the comments made in response to your post.

If you want to migrate your Wubi install to a dedicated partition on the hard-drive, see this excellent guide by forum member bcbc:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

This will allow you to keep all your current settings, files, installed programs etc. but in a proper dual-boot configuration.

If you need specific help, ask bcbc in that thread. I am sure he will be happy to help.

WOW!!! Thumbs Up Rubi1200!!! =D>

---

