---
title: "Deleting Bulk Duplicate Files"
date: 2010-07-07
forum: General Help
---

### Post by fydo44 on 2010-07-07
I am using my Ubuntu machine to serve as a media server and network storage. The problem I have is iTunes on my desktop managed to make 2 copies of every song on the machine so instead of the 30GB I have its up to almost 100gb. I was wondering if there was a way to write a script to go through and delete the duplicates. The duplicates are the same filename as the original except a 1 or 2 following. Wasn't looking forward to deleting  12,000 files by hand. Any suggestions!!

---

### Post by gzarkadas on 2010-07-07
Open a terminal window (from menu `Applications|Accessories|Terminal'). Then:

Type ```
cd <path-to-music-directory>
``` (change the <...> part to your actual path).

Type this command to find and print all duplicates. The somewhat complex conditional is for ignoring directories ending in 1 or 2. ```
find -type f -a '(' -name '*1' -o -name '*2' ')' | less
```You can scroll up and down the screen with the PgUp PgDn and arror keys. [B]

>>>Confirm that the files showing up are indeed your duplicates. The next command will delete those same files. <<<[/B]

After you have ensured that the correct files are shown, type this command to find and **delete** all duplicates: ```
find -type f -a '(' -name '*1' -o -name '*2' ')' -exec rm '{}' ';'
```If you want to be on the safe side, make a directory `~/trash' and instead of issuing `rm' above, use a `mv' to move the duplicates in the temporary trash folder. That way you can review the selected files and restore possible errors. In that case the commands to type are:
```

mkdir ~/trash
find -type f -a '(' -name '*1' -o -name '*2' ')' -exec mv '{}' ~/trash/ ';'

```

---

