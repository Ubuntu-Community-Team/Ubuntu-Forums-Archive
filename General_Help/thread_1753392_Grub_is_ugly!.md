---
title: "Grub is ugly!"
date: 2011-05-08
forum: General Help
---

### Post by ZRTMWA on 2011-05-08
Am I the only one that finds the GRUB (and GRUB 2) screen unappealing aesthetically? BIOS-ish screens are so 1990's. I was wondering, Ubuntu (and Linux in general) being open source and all:

Has anyone put up their own version of a bootloader screen maybe an updated version of GRUB?

I've seen some examples of people who have GRUB screens that are just normal black and white [ugliness]("http://www.itecsoftware.com/wp-content/uploads/2010/08/ubuntu-grub2-boot-menu.jpg"),  one that had an [image]("http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04") behind it. And a couple that had Ubuntuish looking [backgrounds]("http://ubuntuguide.net/wp-content/uploads/2010/06/grub2_brown1-478x360.png"). Is there any bootloader that doesn't use the BIOS-like format?

I am getting a new laptop soon (3 days yeeeeah) and honestly, the ugly GRUB screen is the only reason I'm thinking about just installing Windows 7 and not a dual boot of Win7 and Ubuntu (although the GRUB with the background image is appealing). As always, thanks guys.

Chris

---

### Post by drs305 on 2011-05-08
If you install Natty and want a background image, all you have to do is drop an image into /boot/grub and run "sudo udpate-grub". It's just a bit more difficult if you are using Maverick.

But it's just a background image, not a theme with buttons, icons, etc.

Here is a guide I put together on 'drop-in' backgrounds and how to play with font colors:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

Theming is more advanced with an offshoot of GRUB called BURG. You can do a search to find out more about it.

---

### Post by ZRTMWA on 2011-05-08
sweet thanks drs305, I'll check out you guide and look up BURG.

EDIT: DANG THERE ARE SOME SEXY VERSIONS. This is exactly what I was looking for. I would +1 rep you if ubuntuforums had reputation

---

### Post by towheedm on 2011-05-08
You can now theme GRUB2 using the gfxmenu theming engine.  Check out the link to my tutorial in tyhis thread:
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)
I'm presently writing a 2nd edition which should be available soon.

---

### Post by madjr on 2011-05-08
> **ZRTMWA said:**
> Am I the only one that finds the GRUB (and GRUB 2) screen unappealing aesthetically? BIOS-ish screens are so 1990's. I was wondering, Ubuntu (and Linux in general) being open source and all:

Has anyone put up their own version of a bootloader screen maybe an updated version of GRUB?

I've seen some examples of people who have GRUB screens that are just normal black and white [ugliness]("http://www.itecsoftware.com/wp-content/uploads/2010/08/ubuntu-grub2-boot-menu.jpg"),  one that had an [image]("http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04") behind it. And a couple that had Ubuntuish looking [backgrounds]("http://ubuntuguide.net/wp-content/uploads/2010/06/grub2_brown1-478x360.png"). Is there any bootloader that doesn't use the BIOS-like format?

I am getting a new laptop soon (3 days yeeeeah) and honestly, the ugly GRUB screen is the only reason I'm thinking about just installing Windows 7 and not a dual boot of Win7 and Ubuntu (although the GRUB with the background image is appealing). As always, thanks guys.

Chris

if you use startup manager, you can set grub to 1 or 2 second, so is almost impossible to notice.

also you may try burg (but be cautious, not to break something)
[http://www.omgubuntu.co.uk/tag/burg/](http://www.omgubuntu.co.uk/tag/burg/)
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

when i installed natty, my grub is purple so is kinda cute

---

### Post by yetiman64 on 2011-05-09
> **ZRTMWA said:**
> ...I've seen some examples of people who have GRUB screens that are just normal black and white [ugliness]("http://www.itecsoftware.com/wp-content/uploads/2010/08/ubuntu-grub2-boot-menu.jpg"),  one that had an [image]("http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04") behind it. And a couple that had Ubuntuish looking [backgrounds]("http://ubuntuguide.net/wp-content/uploads/2010/06/grub2_brown1-478x360.png"). Is there any bootloader that doesn't use the BIOS-like format?....

Check the backgrounds in use in [[COLOR=Blue]--this attachment--[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=172859&d=1287509232") from a thread I posted in a while ago. You can put any image in a grub background if you "format" (not the right word really) it correctly first, be aware of the aspect ratios with regard to images and how grub will stretch them out of shape, allow for that first when setting up (the gimp was used on all my images - including to push them out of shape originally to allow for grub's corrections). **Edit**: this is probably only necessary on widescreen monitors like I use here.

[noparse]Use drs305's links and info for setting up backgrounds, grub is quite customizable, you may also note from the text in the pic of the grub menu is quite a bit smaller than usual (I like my grub screen at a resolution of 1024x768).[/noparse]

Have fun tweaking but always do a backup of any file you intend to alter, *_before_* touching it.
I haven't dropped a link to the thread itself I posted that pic in just in case you are not using Lucid as I do. The method varies slightly between Lucid and later releases.

---

### Post by drs305 on 2011-05-09
> **towheedm said:**
> You can now theme GRUB2 using the gfxmenu theming engine.  Check out the link to my tutorial in tyhis thread:
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)
I'm presently writing a 2nd edition which should be available soon.

Thanks. I'll give it a look and will include it in the links section of the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread.

---

### Post by towheedm on 2011-05-09
> **drs305 said:**
> Thanks. I'll give it a look and will include it in the links section of the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread.

Thanks for that.  Look out for 2nd edition which also covers Fedora 14, openSUSE 11.3, Sabayon 5.5, LinuxMint 10, Ubuntu and it's variants and of course Debian.  Note that the 1st edition has some errors during conversion to pdf.  For some reason -- was translated to - in some of the code examples.

---

### Post by morefeo on 2011-05-09
What about **BURG** and some themes?

---

### Post by MG&amp;TL on 2011-08-08
I am also attempting to make GRUB less BIOS-ish. Although I'm trying not to use burg, I have a tarball and an install script here:

[http://ubuntuforums.org/showthread.php?t=1810063&page=11]("http://ubuntuforums.org/showthread.php?t=1810063&page=11")

About halfway down. (I realised UF accepted tarballs) Detar it to you desktop, and run the .sh script inside. (exercise caution, only tested on one machine.) PM me with feedback/errors or post in the thread. I hope we can collaborate :)

It still looks hideous, but with enough time...thanks to drs for the help and support. +1 from here too. :)

---

