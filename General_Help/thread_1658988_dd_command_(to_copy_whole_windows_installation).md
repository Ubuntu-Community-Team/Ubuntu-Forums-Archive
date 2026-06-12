---
title: "dd command (to copy whole windows installation)"
date: 2011-01-03
forum: General Help
---

### Post by chaemil on 2011-01-03
hi. I§m wondering if is possible to copy the whole installation of windows as is to another hard drive. my father considering to buy for himself the new hdd to his laptop and he dont want to reinstall the vista installation on it so i give him this choice but i dont know if the dd command works correctly with the NTFS partition...

---

### Post by endotherm on 2011-01-03
dd operates below filesystems, so it should not matter that the drive is NTFS at all. it should work out alright for you. just make sure that your filesystem is clean at cloning time, and has no bad blocks (if it does, use ddrescue)

---

### Post by tredegar on 2011-01-03
> dd operates below filesystems, so it should not matter that the drive is NTFS at all.

Correct, but I think recent versions of windows will still notice this, and complain. Otherwise you could use this to clone a windows system to you heart's content.

I haven't used win since '98, so don't necessarily take my word on this.

You might be better off asking this Q in a windows forum, and mentioning which version of win you are referring to.

---

### Post by seawolf167 on 2011-01-03
dd will work just fine.

Another option would be to use [Clonezilla ]("http://clonezilla.org/")to image the drive then write the image to a different hard drive (there is a drive-to-drive option in the software which negates having to use an intermediary drive to store the image). Clonezilla also has an option to use dd as well as a couple other copy methods.

---

### Post by Joe of loath on 2011-01-03
DD will probably not work if the drive is a different capacity, as it writes block by block, so the partition table it copies will be wrong, and there will be an empty section between the end of the dd image and the end of the drive.

---

### Post by chaemil on 2011-01-03
so i can resize the partition after the DD command end?

---

### Post by Joe of loath on 2011-01-03
Probably not.

Clonezilla is probably what you want, it'll take the data and the bootloader(?), but fit it into the new partition.

---

### Post by seawolf167 on 2011-01-03
[Here is a dd how-to]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/")

[Here is the disk-to-disk clone how-to for clonezilla ]("http://clonezilla.org/clonezilla-live/doc/showcontent.php?topic=03_Disk_to_disk_clone")(yes it will take the bootloader, data, etc.)

---

### Post by chaemil on 2011-01-03
thanks for your help! from all of you. i'll take a look at clonezilla bcs he wants bigger hard drive.

---

