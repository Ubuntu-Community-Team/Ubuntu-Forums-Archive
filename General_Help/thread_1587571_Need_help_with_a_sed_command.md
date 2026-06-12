---
title: "Need help with a sed command"
date: 2010-10-03
forum: General Help
---

### Post by sr_guy on 2010-10-03
I want to change a directory name in all xxxx.sh files that launch my roms all located in the same directory.  

change:
/mnt/tera/roms/N64_vol1/roms_a-f/favs/


To:
/mnt/tera/roms/favs/N64

What would be the sed command to change to that dir name for all *.sh files in the same dir?

---

### Post by WorMzy on 2010-10-03
I'm not entirely sure what you just asked, but I can't see a need for sed. A simple mv will work fine. (with a mkdir thrown in just in case)

```
mkdir -p /mnt/tera/roms/favs/N64/ && mv /mnt/tera/roms/N64_vol1/roms_a-f/favs/* /mnt/tera/roms/favs/N64/
```

---

### Post by sr_guy on 2010-10-03
What I mean is that I want to change any instance of:

/mnt/tera/roms/N64_vol1/roms_a-f/favs/

to 

/mnt/tera/roms/favs/N64

in ever shell script in a single directory. Here is what my dir structure looks like:

```

-rwxrwxrwx 1 root root    10369 2010-10-03 19:32 aerofighters.jpg
-rwxrwxrwx 1 root root       94 2010-10-03 19:57 aerofighters.sh
-rwxrwxrwx 1 root root  4997570 2010-10-03 19:32 aerofighters.zip
-rw-r--r-- 1 root root        0 2010-10-03 20:15 ChopperAttack.sh
-rwxrwxrwx 1 root root  5791680 2010-10-03 19:32 ChopperAttack.zip
-rw-r--r-- 1 root root        0 2010-10-03 20:15 DestructionDerby64.sh
-rwxrwxrwx 1 root root 10304737 2010-10-03 19:32 DestructionDerby64.zip
-rw-r--r-- 1 root root        0 2010-10-03 20:15 DonkeyKong64.sh
-rwxrwxrwx 1 root root 27689818 2010-10-03 19:32 DonkeyKong64.zip
-rwxrwxrwx 1 root root    68825 2010-10-03 19:32 donkeykong.jpg
-rwxrwxrwx 1 root root    15601 2010-10-03 19:32 doom64.jpg
-rw-r--r-- 1 root root        0 2010-10-03 20:15 Doom64.sh
-rwxrwxrwx 1 root root  7314544 2010-10-03 19:32 Doom64.zip


```

The shell scripts are used to launch N64 roms with mupen64plus using mupen's cli

---

### Post by WorMzy on 2010-10-03
Oh, I see. You want to change the files content, not move the files. Gotcha.

```
for script in *.sh; do sed -ri 's/\/mnt\/tera\/roms\/N64_vol1\/roms_a-f\/favs\//\/mnt\/tera\/roms\/favs\/N64\//' $script; done
```

Unfortunately, since root owns those files, you'll need to be in a root shell to use the command. ```
sudo -i
``` will put you into one, then you need to browse to the folder containing the scripts.

Make a backup before you run the script. I've tested it on my PC and it seems to work, but it's always better to be safe than sorry.

---

### Post by sr_guy on 2010-10-03
That worked perfectly. You saved me a ton of time! Thanks!

---

