---
title: "dell inspiron 2650 no keyboard commands"
date: 2011-08-26
forum: General Help
---

### Post by evilscrappy on 2011-08-26
ok I am kinda new to ubuntu and not,have played a bit with before.
the problem I am having and have googled and found numerous threads on the forum about this,but nobody seems to have found a good workaround.
when I install ubuntu 10.10 on a dell inspiron 2650 with most updated bios version a13.windows xp pro as other operating system with 512 megs of ram.
Everything works fine till I run update manager it updates fine then upon reboot it will not accept keyboard commands,will accept usb keyboard and mouse
again only happens after update.
I tried editing the grub menu with acpi-off,but not sure if I did it right,as when it rebooted again thats with fresh install with no updates it wouldnt accept keyboard again.
right now I am running ubuntu with no updates,afraid to keep trying as I dont want to keep reinstalling  


any ideas?



mods I didnt see the dell support section please move thread to there.

---

### Post by searchfgold6789 on 2011-08-26
If the grub option worked, then never fear because it did do what it was supposed to do, which was that when you rebooted it removed the option from the line. This means that every time you reboot you will have to add the boot option again, unless you find a way to add it permanently. I know there is a way to do this, but I don't know what. It is highly likely that it is in the [Grub 2 guide]("http://http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by evilscrappy on 2011-08-27
no,I meant that the grub option didn't work,as when it rebooted it would not accept the keyboard again,(unless I did the acpi=off line wrong) which is possible as I was not exactly sure how to do it.


quoting---I tried editing the grub menu with acpi=off,but not sure if I did it  right,as when it rebooted again thats with fresh install with no updates  it wouldn't accept keyboard again.


grub2 link didn't work couldn't find server

---

### Post by evilscrappy on 2011-08-28
ok I think I solved this.
here is a link to what I did.
[http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/](http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/)
actually I think other person solved it I just repeated!
Mods I haven't marked as solved yet ,as I am not sure, will do when I am.

I am gonna post it as there was some extra stuff there and could become confusing to someone.

1. In the grub menu, press &#8216;e&#8217;.  add after quiet splash "acpi=off&#8217; (without quotes) 
then keyboard should work --
in terminal type[COLOR=#c20cb9]** sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR]grub. Find the line which says GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; and change it to the following:
 GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi=off&#8221;
 5. Exit gedit.
 6. Execute:
[COLOR=#c20cb9]**sudo**[/COLOR] update-grub

7. Restart. This time you don&#8217;t have to edit anything. Ubuntu should boot without any issues.

---

### Post by reyemtm on 2011-11-09
This is not solved. ACPI=OFF disables battery status among other things, this should get moved to bugs. What is a laptop without battery status? Is there any fix for this for these older laptops?

---

### Post by reyemtm on 2012-01-25
Inspiron 2650 works fine with Lucid Puppy with battery management, no acpi=off needed. This is the only distro so far that I've found works out of the box with this laptop.

---

