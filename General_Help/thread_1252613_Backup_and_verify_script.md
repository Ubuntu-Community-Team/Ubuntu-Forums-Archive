---
title: "Backup and verify script?"
date: 2009-08-29
forum: General Help
---

### Post by DejitaruJin on 2009-08-29
I've been trying to completely redo my backup script, since tar is absolutely not what I need in this situation. The idea is, use a plain cp on an entire hard drive of files, and then use md5sum to verify that everything is identical to the way it should be - with a bonus of also pinpointing specific files that have changed (which there will be; these drives will be live and shared with samba during the backup). It *sounds *easy. In practice, bash is tripping over its own syntax the whole way.

I've got the copy part down, working with a small test folder for now. Its command:
```
datetime=`date +%F\ %T`
cp -r /mnt/40GB/Tests/ "/mnt/MegaBak/Full $datetime/40GB/"
```Note that the backup location does have spaces. That's not something I can change, for a few reasons.

I've tried literally over a dozen ways to get the files into the md5sum command. Currently, I have this:
```
find /mnt/40GB/Tests/ | tee /home/digitalman/Documents/filelist
while IFS= read line
    do
        md5sum "$line"
    done < filelist > checklist
```I got this off a site, and it is specifically to deal with the odd symbols in many of the filenames. However, md5sum halts because the first thing it gets fed is just a directory. A directory that doesn't end in a / , for some reason, so I can't just use sed to delete any lines ending with / .

And after that, a point which I haven't gotten to yet, the entire checksum list file will have to be modified to reflect that the copied files are now in a very different location.

This time, I really don't care what commands are used, as long as it doesn't involve downloading obscure packages. The method just has to be able to deal with any sort of odd characters in filenames, and work on thousands of files.

Oh, and, if anyone can tell me why: echo "\a" actually prints \a to the screen in this script, but produces a beep (the way it should) in my rc.local script, that would be nifty.

---

