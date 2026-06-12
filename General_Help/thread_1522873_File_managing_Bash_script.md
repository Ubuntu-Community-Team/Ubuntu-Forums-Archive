---
title: "File managing Bash script"
date: 2010-07-02
forum: General Help
---

### Post by tazthecat on 2010-07-02
Hi,

I want to manage my torrent downloads by using a bash script.

My goal is to unpack a rar file, rename, and move to my directory.

example:

/home/tazthecat/Torrent/Possession.2009.DVDRip.XviD-VoMiT has multiple rar files. but when unpacked it's name is vmt-possess-xvid.avi

I want to right click the possesion folder in nautilus and have the file extracted and renamed, then moved to /home/tazthecat/Films_engels

This is what I use but it is not able to right click on the folder.

> find . -type d | while read dir
do
  cd "$dir"
  find . -name \*.rar -exec unrar x '{}' \;
  find . -name \*.avi -exec mv '{}' "${PWD##*\/}.avi" \;
  mv *.avi /home/tazthecat/Films_engels

done

When i right click on a folder it starts to unpack everything in the folders dir.

How can I fix this?
I tried editing this script, but it just stops working.

Please give me advice, i can't write scripts I just try to edit them to my preffereces

---

### Post by tazthecat on 2010-07-19
bump?

---

