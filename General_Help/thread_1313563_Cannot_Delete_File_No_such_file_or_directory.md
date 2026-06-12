---
title: "Cannot Delete File: No such file or directory"
date: 2009-11-03
forum: General Help
---

### Post by Doctor Corndog on 2009-11-03
This is just confusing me.

I have an old External USB drive which I have daisy chained to my NAS. First order of business, cleaning that sucker up.

So, not a problem. I was able to delete about 22GB of data, only to be left with a few .mp3s in three directories. For the life of me, I cannot get these guys to go away. I have tried deleting them, moving them, chmoding them and even copying them, but anything I aim at them comes back with this:

```
No such file or directory
```So, here what I'm looking at:

```
bryan@opteron:/USB1$ ls
iTunes Music  My Music
bryan@opteron:/USB1$ rm -rf ./*
rm: cannot remove directory `./My Music/Jazz': Directory not empty
rm: cannot remove directory `./My Music/new opera': Directory not empty
rm: cannot remove directory `./My Music/Opera': Directory not empty
bryan@opteron:/USB1$ cd ./My\ Music/Jazz/
bryan@opteron:/USB1/My Music/Jazz$ ls
ls: cannot access Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3: No such file or directory
Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3
bryan@opteron:/USB1/My Music/Jazz$ rm -rf ./*
bryan@opteron:/USB1/My Music/Jazz$ ls
ls: cannot access Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3: No such file or directory
Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3
bryan@opteron:/USB1/My Music/Jazz$ rm -rf ./Kenny\ G\ -\ Paradise\ -\ 04\ -\ One\ More\ Time\ \(Featuring\ Chant_\ Moore\).mp3 
bryan@opteron:/USB1/My Music/Jazz$ ls
ls: cannot access Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3: No such file or directory
Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3
bryan@opteron:/USB1/My Music/Jazz$ cp ./Kenny\ G\ -\ Paradise\ -\ 04\ -\ One\ More\ Time\ \(Featuring\ Chant_\ Moore\).mp3  ..
cp: cannot stat `./Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3': No such file or directory
bryan@opteron:/USB1/My Music/Jazz$ mv ./Kenny\ G\ -\ Paradise\ -\ 04\ -\ One\ More\ Time\ \(Featuring\ Chant_\ Moore\).mp3  ..
mv: cannot stat `./Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3': No such file or directory
bryan@opteron:/USB1/My Music/Jazz$ ls -la
ls: cannot access Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3: No such file or directory
total 0
drwxrwxrwx 1 root root 0 2009-11-03 14:07 .
drwxrwxrwx 4 root root 0 2009-11-03 14:08 ..
-????????? ? ?    ?    ?                ? Kenny G - Paradise - 04 - One More Time (Featuring Chant_ Moore).mp3
bryan@opteron:/USB1/My Music/Jazz$
```Yeah, it's a Kenny G song too, as if this were not frustrating enough. This really isn't anything critical, but I thought it might be nice to know how to actually remove a file in this state. Anyone have any ideas?

PS. I have also tried everything with sudo...

---

### Post by Praxicoide on 2009-11-03
Have you tried to format with Gparted? It could be damage to the drive, if that were so, Gparted would tell you about any errors.

---

### Post by stevepburke on 2012-08-30
Touch the file first, then you should be able to remove it:

touch <file>
rm <file>

---

### Post by oldos2er on 2012-08-31
Please don't bump old threads.

---

