---
title: "Computer crashes after running TAR command."
date: 2009-09-28
forum: General Help
---

### Post by Max Bain on 2009-09-28
My computer crashes after running the command:

```
tar -c --new-volume-script=/home/aj/Desktop/tarscript.sh --tape-length 1502333 -M -f Desktop/backup/picturebackup20090927.tar Pictures/
```

It freezes up at a different point each time. The REISUB trick does not work. Running a fairly fresh install of 9.04.

Any ideas as to what could cause this? Or how I could trouble shoot?


for the curious the tar script is:
```
#! /bin/bash
echo Preparing volume $TAR_VOLUME of $TAR_ARCHIVE.

function pause(){
   read -p “$*”
}

pause "press_enter_to_continue"

name=`expr $TAR_ARCHIVE : '\(.*\)-.*'`
case $TAR_SUBCOMMAND in
-c)       ;;
-d|-x|-t) test -r ${name:-$TAR_ARCHIVE}-$TAR_VOLUME || exit 1
          ;;
*)        exit 1
esac

echo ${name:-$TAR_ARCHIVE}-$TAR_VOLUME >&$TAR_FD
```


[COLOR="Red"]Update Tuesday, September 29 2009 10:34 AM[/COLOR]
I just ran this from the live cd (9.04) and it still crashed. Unless this is a problem with LVM or tar itself, I'll go with there is something wrong with my hardware.

---

