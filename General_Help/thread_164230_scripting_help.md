---
title: "scripting help"
date: 2006-04-22
forum: General Help
---

### Post by jimisdead on 2006-04-22
hi - I have a bit of a problem with an external harddrive. Well it's almost completely dead - and I am just trying to get my data off before i send it off to be replaced.

I can mount it as read only - and most of the files seem okay and can be copied, but the hd stops working after random intervals of time so i then have to unmount it, unplug it, replug it, and remount it. When trying to copy 50,000+ files this is a bit of a problem.

I can get a file listing of all the files on the drive, but I don't know how to feed this list into the cp command. I figure then when it crashes and I remount it, I can then get a file list from the copy destination, deduct it from the original filelist, then feed the new list into the cp command and continue copying... so something like this

1) get file list from hdc1 > hdc1_filelist
2) cp < hdc1_filelist (destination being hdb1)
**crash & remount ***

3) get file list from hdb1 > hdb1_filelist
4) deduct hdb1_filelist from hdc1_filelist > temp_filelist
2) cp < temp_filelist (destination being hdb1)

then I can just punch in the commands from 3 when the crash occurs again

can anyone help me with what commands to use? Any help would be greatly appreciated. Thanks.

-Veronika

---

### Post by jazzmuzik on 2006-04-22
You may be better off using rsync instead of copy. Rsync won't get a file it's already gotten.

rsync -av /source /destination/

Also, you could be crashing because you are feeding too many files to cp. It seems people suggest using 'find' with the exec option in that case. But try rsync first, it's simpler.

---

### Post by jimisdead on 2006-04-22
[QUOTE=jazzmuzik]You may be better off using rsync instead of copy. Rsync won't get a file it's already gotten.

rsync -av /source /destination/

Also, you could be crashing because you are feeding too many files to cp. It seems people suggest using 'find' with the exec option in that case. But try rsync first, it's simpler.[/QUOTE]

That looks perfect - you're a life saver.

---

### Post by jazzmuzik on 2006-04-22
If the files you are copying are uncompressed (unlike mp3, zip, tar.gz, etc.) you can add the z option. That turns on compression and it may speed things up a bit:

rsync -avz /source /destination/

---

### Post by Face1 on 2006-04-22
[QUOTE=jazzmuzik]If the files you are copying are uncompressed (unlike mp3, zip, tar.gz, etc.) you can add the z option. That turns on compression and it may speed things up a bit:

rsync -avz /source /destination/[/QUOTE]
I'm not so sure.  I'm not positive about this, but I would think that the file would be compressed on the other drive, and then sent over, which could potentially increase the likeliness of a HD crash.

---

### Post by jazzmuzik on 2006-04-22
Yeah, I wondered about that myself. Maybe compression is done in memory, but that doesn't seem possible for large files. Compression is probably best when used over the net because it reduces the time of transfer, but it may not be a good idea for a local file transfer.

---

### Post by jazzmuzik on 2006-04-22
Got a double post.

---

