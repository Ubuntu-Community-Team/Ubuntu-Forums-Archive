---
title: "Upgrading from 8.10"
date: 2011-02-06
forum: General Help
---

### Post by topher-t-mill on 2011-02-06
I have several hard drives which get swapped around and run various linux distros, at present I would like to rationalise a 160gb hard drive which has several partitions, but Ubunbtu 8.10 is stretched out over about100gb  with 10gb as /, 30gb as /usr and 60gb as /home. I guess /usr has the programs and /home I want to leave untouched. Can I reinstall 10.10 on the first partition and leave the other 2 with their respective mount points but leave them unformated? or should I just install in sda1 and reinstall any prorams I need and keep the home folder where it is and possibly re format sda2 into Fat or something? I am not a fluent terminal user.

---

### Post by tredegar on 2011-02-06
**/** and **/usr** do not matter if you are doing a fresh install (recommended).

Just _do not re-use_ your **/home** partition. You can always mount it later and copy over the (non-configuration, ie data) files to your new home.

Make sure where **/home** currently is with the **mount** command, and make a note of which partition  **/home** is currently on.

If in doubt, backup (as root) all of **/home** to a linux-formatted external HDD. 

Check that you can read your backup (including the "hidden" dot-files eg **~/.gnome2** [sometimes there is stuff in there that you only realise you _need_ later]) before you go any further.

You should let 10.10 refer to disk partitions by their UUIDs and not /dev/sdXY (it sort-of defaults to this).

This makes **fstab** much more robust, but just be careful.

Once in 10.10 **sudo blkid** will help you work out the UUID mapping of your partitions, so you'll be able to remount your old **/home** with an entry in **/etc/fstab** (or you can just search for it with nautilus eg Places ... 60GB filesystem )

Good luck.

Please let us know how you get on.

---

### Post by topher-t-mill on 2011-02-07
Thank you, I thought a fresh install was probably the thing to do but there are quite a lot of programs in /usr/bin, can these be included or is that too complicated?

---

