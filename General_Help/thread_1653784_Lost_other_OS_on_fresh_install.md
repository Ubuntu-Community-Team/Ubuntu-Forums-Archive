---
title: "Lost other OS on fresh install"
date: 2010-12-27
forum: General Help
---

### Post by Robing Goodfellow on 2010-12-27
On a new HP G62-367DX with 320 GB HD and 4MB memory, Windoze 7 home premium I did a fresh install of Ubuntu 10.10 from a Live CD downloaded from the Ubuntu site.  Reduced the Windoze partition to about 80GB, 200GB of ext4 partition for Ubuntu, 20 GB for swap.

I did the install, loaded the updates, etc, did nothing else other than change the sound profile to "bark."

I now have an error message upon startup that says "cannot reserve MIMO region" which poking around in the forums seems to be either a kernel issue or something to do with the ATI 4200 my computer has.  Minor issue, will figure that out later unless someone has a quick "HEY NOOBIE!  We already figured that out!"

More importantly, the computer no longer offers me the choice of Windoze or Ubuntu on start up, it goes directly to Ubuntu,

Mind you, I've played with Ubuntu for a few days now and love it, would prefer to use it exclusively, but I have to keep Windoze so I can use my Rhapsody to go account and my Lexmark printer until Linux support for those come from either the community or the vendors.  I had issues with the previous install due to Wubi and my own ignorance/ learning process, so decided to do a fresh install and start over having read the "Official Ubuntu book" over the weekend.

The only other info I have is an odd thing during the install: I was only given two options: to use the entire drive or manual partition, the third (expected) option of installing alongside another OS was absent.  I chose manual and partitioned as explained above.

Methinks I either dumped windows unintentionally or screwed up the MBR.

I'd appreciate any ideas you might have, and thanks in advance.
Richard

---

### Post by tredegar on 2010-12-27
From ubuntu:
**sudo fdisk -l**  <-- that's a little "Ell" not "one"
will tell you if your windows partitions are still there
**sudo update-grub**
should let grub find your windows partition and add it to the menu.

But maybe the problem is that grub isn't offering you the menu to choose windows (even if it's there). I think this is the default with the newer installs (and I hate it, so disable it). Maybe the key you have to keep hitting as your PC boots up so you can the grub menu is Esc?

Worth a try.

---

### Post by Robing Goodfellow on 2010-12-27
Thanks for the help Tredegar.  It would appear that I somehow deleted the C: drive and windoze.  Not all that big a deal as I have the backup disks, I'm just trying to figure out why I should restore it.  I still have my old computer, so if I need to print or use Rhapsody I can use that or my wife's.

The more I think about it the fewer reasons I come up with to keep windoze.

curiouser and curiouser.....

---

### Post by tredegar on 2010-12-27
> Thanks for the help Tredegar. It would appear that I somehow deleted the C: drive and windoze.

Sorry (sort of) to hear that, but if you don't care, then good.

I quit win at '98 ("Faster, easier, better!", and I thought WTF? He told us that about DOS3.1 and it has ALL been c??p!). I never looked back.

It is a good idea to have 2 different PC's - one win for those "emergencies", and one (or more) for linux fun. My little place has 5 now, so I can experiment and always have a "fallback". Somewhere there's a partition with XP, but I'm not sure where.

Looks like you have "made the leap". Good luck.

If you want help printing from your linux PC to your printer, there's help here, and other places on the interweb.

---

