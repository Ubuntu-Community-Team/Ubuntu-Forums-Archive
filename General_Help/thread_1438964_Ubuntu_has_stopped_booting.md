---
title: "Ubuntu has stopped booting?"
date: 2010-03-25
forum: General Help
---

### Post by Jordan Moore on 2010-03-25
[B]PROBLEM IS NOW SOLVED, HERE IS HOW.

[/B]I was seeing this screen:
> 
GNU GRUB version 1.97~beta4

[ Minimal BASH-like editing is supported. For the first word, TAB lists possible completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub> 

But I followed the steps in this link:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

And it all works perfectly.


_**Original Post:**_


Hi,

I am sorry to bother you but I am stuck with my ubuntu, it has stopped booting after performing an update.
Unfortunately I am extremely new to the Linux scene and can think of no way to fix it without having to re-install it.

So here is what happened:
I was using ubuntu perfectly (as usual) when it asked for an update, I chose to update everything on the list.
When it went to restart it failed to boot into ubuntu, instead I get this Grub loader, shell, something of that sort (sorry I do not know the name).

I would greatly appreciate any help on fixing it, and of course - just ask if you need more details (though you may have to explain how to get those details).

Extra Info:
Ubuntu 9.10 Dual booted with windows 7.
I installed ubuntu to its own partition using the installer for windows.

Thank you.

---

### Post by oldfred on 2010-03-25
Please run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Jordan Moore on 2010-03-25
How can I run this script on my machine without installing another Linux aswell?
I cannot get to the terminal on my Ubuntu.

---

### Post by John Wolf416 on 2010-03-25
Grub2beta4 is uneditable to new user, as well as the updater who did that to you.
All those query utilities will tell you exactly what is wrong but not how to fix.
I had to delete Grub2 using W7 emergency recovery disk (or installdisk) and use command line bootrec.exe (use /switches to delete & rebuild bootrecord). This will delete grub return you to Win 7 without destruction to Win . You did not mention whether you had any AHCI-eSATA or not it's very important these devices be off during update process.
I then deleted partition Ubuntu was on. Re installed Ubuntu. The next time I updated I watched splash screens and understood what to do when you see (do you want to install the new managed Grub) HELL NO! is not listed but no is.

---

### Post by oldfred on 2010-03-25
As the instructions say use a liveCD. You can download to the desktop of the liveCD and run it there.

---

### Post by Jordan Moore on 2010-03-25
I do not believe that I have any AHCI-eSATA connections, my system is a laptop if that helps.

I am still able to boot windows 7 as the boot loader works fine, it is just that when I select ubuntu, ubuntu does not actually load.
I will try and boot into it now, and write down what the screen is called.

EDIT:
This is exactly what the screen says:
> 
GNU GRUB version 1.97~beta4

[ Minimal BASH-like editing is supported. For the first word, TAB lists possible completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>

It never used to do this, it always used to boot straight onto the login screen.

---

### Post by oldfred on 2010-03-25
You said dual boot which to me is an install in another partition. You must have wubi which is installed in the windows partition and uses the windows boot loader.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Jordan Moore on 2010-03-26
Thank you, I was just about to try the Live CD with that script for debugging - but updating the file has worked perfectly, I am writing this message from within Ubuntu.

Thank you once again.

---

