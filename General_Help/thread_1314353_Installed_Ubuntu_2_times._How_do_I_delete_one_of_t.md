---
title: "Installed Ubuntu 2 times. How do I delete one of them?"
date: 2009-11-04
forum: General Help
---

### Post by Feareilo on 2009-11-04
I had Windows XP and Ubuntu 9.04. Then I upgraded Ubuntu 9.04 to 9.10. Then I thought that Ubuntu 9.10 had problems so I downloaded a "fresh install" and tried reinstalling it. But instead of reinstalling it, I installed *another* Ubuntu 9.10. So now I've got Windows XP, Ubuntu 9.10 (fresh install) and Ubuntu 9.10 (upgraded from Ubuntu 9.04).

How can I delete the Ubuntu 9.10 fresh install and assign that empty space to the upgraded Ubuntu 9.10?

By the way, I think there's gonna be an issue with Grub because I think Grub's in the Ubuntu 9.10 fresh install.

---

### Post by phillw on 2009-11-04
> **Feareilo said:**
> I had Windows XP and Ubuntu 9.04. Then I upgraded Ubuntu 9.04 to 9.10. Then I thought that Ubuntu 9.10 had problems so I downloaded a "fresh install" and tried reinstalling it. But instead of reinstalling it, I installed *another* Ubuntu 9.10. So now I've got Windows XP, Ubuntu 9.10 (fresh install) and Ubuntu 9.10 (upgraded from Ubuntu 9.04).

How can I delete the Ubuntu 9.10 fresh install and assign that empty space to the upgraded Ubuntu 9.10?

By the way, I think there's gonna be an issue with Grub because I think Grub's in the Ubuntu 9.10 fresh install.

Grub2 lives here   [http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)    and here  [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

GParted can 'kill' the partition and then move that area to whatever partition you want.

I'd suggest 'teaching' Grub2 that the area is no longer there, before u 'nuke' it ... Oh, and don't forget ... BACKUP YOUR DATA !!!!

Phill.

---

### Post by Feareilo on 2009-11-04
> **phillw said:**
> Grub2 lives here   [http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)    and here  [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

GParted can 'kill' the partition and then move that area to whatever partition you want.

I'd suggest 'teaching' Grub2 that the area is no longer there, before u 'nuke' it ... Oh, and don't forget ... BACKUP YOUR DATA !!!!

Phill.

Could you be more specific please? I'm a complete newbie. How do I 'teach' Grub2 that the area is no longer there? And how do I 'nuke' the area?

Thanks a lot man!

---

### Post by phillw on 2009-11-04
> **Feareilo said:**
> Could you be more specific please? I'm a complete newbie. How do I 'teach' Grub2 that the area is no longer there? And how do I 'nuke' the area?

Thanks a lot man!


My apologies, It's a delicate step between counting beans on someones account & not patronising them.

If you go through the stuff on Grub2, what you need to do, is to get Grub not to look for the area you have your old install on. I'm sorry, I'm still running the 'old' grub. 

But, what you are aiming for is to remove the old installs' partiton that Grub sees at boot (start-up) time.
Once you have got it to that, then you can safely delete and merge that area of your hard-disk to give that area to your other systems.

The reason I say to teach Grub2 not to look for it is that, should anything go wrong - you haven't actually deleted any data.

As my system is a live system, I cannot do the upgrade to Grub2 just yet. You may to have to roll up your sleves and get 'dirty' at the command line. 

There will be folks on here with experience of Grub2, certainly the guy who wrote the thread I pointed you to earlier, would be a good place to pop your question on.

If you phrase it like you did here - asking to remove the partition that had your old install from the boot menu before you remove the partition, it'll help them to understand what you're wanting to do.

Just, please, please, do a backup of data that is important - delving into the innards of your hard disk could result in a horrible data loss. It is rare, but, just be aware that it can happen.


> For anyone passing by, that knows Grub2, could you please help the OP 

Phill.

---

### Post by Feareilo on 2009-11-04
Thanks a lot man. I really appreciate it. And most of the posts I've got are from being a crying bitch. I really regret some posts.

All I've got to say is that Linux, Ubuntu and this forum are awesome. Long live free software!

---

### Post by phillw on 2009-11-05
> **Feareilo said:**
> Thanks a lot man. I really appreciate it. And most of the posts I've got are from being a crying bitch. I really regret some posts.

All I've got to say is that Linux, Ubuntu and this forum are awesome. Long live free software!


Hi,  the grub2 link I gave you was for when Koala (9.10) was in development. The live Grub2 area is over here ---->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You'll be after section 7  ;)

> **[COLOR=Navy][SIZE=3]Removing Entries from Grub 2[/SIZE][/COLOR] **
Entries should be removed by editing or removing files in the /etc/grub.d folder. The [COLOR=DarkRed]*/boot/grub/grub.cfg*[/COLOR] file is read-only and should not normally require editing.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]**Too Many Kernels?** Kernels removed via Synaptic or with "apt-get remove" will automatically update [COLOR=DarkRed]*grub.cfg*[/COLOR] and no user action is required.
[LIST]
[*]In Synaptic, type the kernel number in the search window at the upper right (for example - 2.6.28-11).
[*]Find the "linux-image" and "linux-headers" files for the applicable kernel (example - linux-image-2.6.26-11 or "linux-image-2.6.26-11-generic).
[*]Right click and select "Mark for Complete Removal" and then press the Apply main menu button.
[*]The kernels will be removed from your system and from the Grub menu.
[*] If you are not sure of the kernel you are currently using, in a terminal type "uname -r".
[*]Many users keep one previous kernel on the machine which previously ran without problems.
[/LIST]
[*]Other Operating Systems which have been removed from the computer will also be removed from the menu once "[COLOR=Navy]*update-grub2*[/COLOR]" is run as root.
[*] To prevent one of the */etc/init.d* files from running, remove the "executable" bit.
[LIST]
[*] Example: If you don't want to see the "Memtest86+" entries, run this command:
 	Code:
 	sudo chmod -x /etc/grub.d/20_memtest86+ 
[*]Run the *update-grub* command to allow the changes to be incorporated in grub.cfg
[/LIST]
 
[/LIST]


[SIZE=3]**[COLOR=DarkRed]User-Created Entries.[/COLOR]**[/SIZE]
[LIST]
[*]To remove a user-created menu entry, remove the applicable file from the /etc/grub.d folder.
[*]If a custom file contains multiple entries, individual items may be removed and others retained.
[*]Once the file has been removed or edited, run "[COLOR=Navy]*update-grub2*[/COLOR]" to update [COLOR=DarkRed]*grub.cfg*[/COLOR].
[/LIST]
[/LIST]


As i earlier said, it is very worth taking the time to understand WHY you are doing things to the configuration.

Phill.

---

### Post by bharaths_jois on 2009-11-19
Helped me!!

Thank you!

Warm regards,
Bharath

---

