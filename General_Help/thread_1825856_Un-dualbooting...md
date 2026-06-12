---
title: "Un-dualbooting..?"
date: 2011-08-15
forum: General Help
---

### Post by Afterthought on 2011-08-15
Alright, so... how would I go about removing my Linux partition(s) and the Linux bootloader and restoring my Windows partition to my full machine without having to reinstall Windows completely or otherwise lose anything on my windows partition?

@_@;  I'm in dire need, so I hope someone can help!

---

### Post by requeth on 2011-08-15
You really should be asking this on Windows forums since this is a windows issue over a linux issue, but I found a solution for you I think. I'll admit I havn't tried it myself yet.


Make sure all your linux data is pulled out, ready to wipe it.
You probably want to back up your windows data as well...this is a dirty hack.


Login to windows as an admin.
Open a command term.
Run bootrec /RebuildBcd        This scans all partitions, finds any windows compat installs, and updates the boot loader, it should wipe grub.

Go to the control panel, and the drive management in advanced/admin tools. You can repartition your disk in here, wiping all of the linux partition and reallocating them to your windows partition. I recommend running a defrag after this (don't hear that often anymore do ya?)

Above all, remember I havn't tried the bootrec fix yet, but I found it on a forum and it helped two users, and I read on MSFT about it and it seems like will work as advised. If it doesn't you'll need a thumb drive startup disk and you'll need to run a fixmbr and bootrec rebuild again. I have used bootrec before when the windows loader corrupts, and it works fine.


If this works please update on the forum so we all know. I dub thee Danger Boy. ;)

---

### Post by Afterthought on 2011-08-15
Well, that was incredibly foolish of me.  After the bootrec /RebuildBcd thing didn't work out at all (non-existent commands, etc), I tried them via my Win7 disc, and after that didn't lead to anything, I tried a system restore (because I am king of the idiots) and managed to kill a number of things (expected, but without the benefit of it actually working).

Tomorrow, I'm just going to reinstall Windows 7 completely.  Goodie.  @_@;

Thanks for the advice, though, I thought I would ask on here because it was a Linux install I was trying to rid myself of.  I figured someone might know something, etc.  Thanks for the attempt, at the very least, because that was more than I could have gotten! :)

Anyway, it's mostly going to be about reinstalling and setting up some other stuff tomorrow...  ugh... @_@  bye, and thanks! :)

---

### Post by Megaptera on 2011-08-16
Hi Afterthought,
If it's not too late, you may want to try this guide: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

Hope it helps?

---

### Post by phosphide on 2011-08-16
I think this all could have easily been avoided. Next time just log into your windows partition and remove the linux partition via Computer Management.

[http://www.sevenforums.com/tutorials/2668-partition-volume-delete.html](http://www.sevenforums.com/tutorials/2668-partition-volume-delete.html)

(Do not take what I am about to put below as a true answer. Hopefully someone here can provide a better one. However, there are ways to change boot options in Windows. I don't know if this will technically reset the MBR or not, but I do know this applies to Vista. This will affect the Windows Boot Manager.)

1. Pull up the Run Command (Windows Logo + R)
2. Type in msconfig and hit enter
3. Go to the boot tab.
4. You should be able to set your Windows boot to be the default.

Also, look up commands like "fixmbr" that can be ran through the command prompt in windows.

Here is some more helpful information about msconfig and the boot options. This applys to Vista however. Hopefully it is not much different than Win 7 and you can find your answer.

[http://www.trainsignaltraining.com/master-the-new-and-improved-msconfig-in-vista](http://www.trainsignaltraining.com/master-the-new-and-improved-msconfig-in-vista)

---

