---
title: "problem downloading firmware for graphics card"
date: 2010-05-14
forum: General Help
---

### Post by crumpetrules on 2010-05-14
So I'm trying to download some firmware for my ATI radeon graphics card using 
> sudo wget -O /var/lib/firmware/`uname -r`/radeon/R600_rlc.bin [http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin](http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin)


but I keep getting 'such file or directory'

is there anything I'm doing wrong?

Your help would be greatly appreciated.

---

### Post by BoneKracker on 2010-05-14
Do you actually have a directory /var/lib/firmware/<kernel>/radeon/?

I'm assuming from the presence of `uname -r` in your command that this is part of a script.  (Otherwise, you'd certainly just cd to the directory and issue your wget command, right?)

Your script could first test for the presence of the appropriate directory and parent directories, and then create what doesn't exist.

Also, I don't think I'd use the -O option (which requires you to explicitly articulate the name of the file).  Instead, use the -P option, and the file will just be named whatever it is on the server (which is what you are actually doing anyway).
```
url="http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin"

dir="/var/lib/firmware/$(uname -r)/radeon"

[ -d $dir ] || mkdir -p $dir

wget -qNP $dir $url

```

You probably notice two other options there (q and P).  I just threw them in for good measure.  That way, you can run this script automatically via cron (say monthly) to keep the firmware up to date, and it will only produce output if there's an error (q -> quiet), and it will only download the file if it's newer than the one you've got (N -> timestamp).

---

