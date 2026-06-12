---
title: "bash script failure using sed"
date: 2009-08-17
forum: General Help
---

### Post by Subban on 2009-08-17
My head hurts, could someone please tell me where I have gone wrong with a bash script using sed (doesn't have to be sed, anything that works).

```
file1=/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png
```

I need to remove the escape characters and keep the result in a variable, doesn't strictly have to be $file1.

I was trying using a sed like:

```
printf "$file1\n"|sed 's/\\\//g/'
```
In a terminal just to test as I utterly failed to get it working in the script, anyway, its leaving the escape character \ in.

Help :[

---

### Post by kaibob on 2009-08-17
Not an expert at sed, but I tried this and it seemed to work:

```
file1="/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png"
printf "$file1\n" | sed 's/\\//g'
```

As one long command line to test in a terminal window:

```
file1="/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png" ; printf "$file1\n" | sed 's/\\//g'
```

---

### Post by Subban on 2009-08-17
> **kaibob said:**
> Not an expert at sed, but I tried this and it seemed to work:

```
file1="/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png"
printf "$file1\n" | sed 's/\\//g'
```

Thanks a bunch, I had been reading my pocket guide to Sed and Awk and completely failed to get the right combination of chars, the closest I came looking at my bash history was:

```
printf "$file1\n" | sed 's/\\//g/'
```

The last pesky / at the end must have been messing it..

Once again, thanks for the help, now I finish the script, its the only part I was stuck on ;)

---

### Post by Johnny B on 2009-08-17
the escape characters will be interpreted by the shell if you dont use quotes:

file1=/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png
echo $file1
/media/FREECOMHDD/Music/best_mp3/Norah Jones/Come_Away_With_Me/.folder.png

---

### Post by kaibob on 2009-08-17
> **Johnny B said:**
> the escape characters will be interpreted by the shell if you dont use quotes:

file1=/media/FREECOMHDD/Music/best_mp3/Norah\ Jones/Come_Away_With_Me/.folder.png
echo $file1
/media/FREECOMHDD/Music/best_mp3/Norah Jones/Come_Away_With_Me/.folder.png
I hadn't noticed that the backslashes were simply escaping spaces. So, there's no reason for the OP to use sed.

---

### Post by Subban on 2009-08-17
> **kaibob said:**
> I hadn't noticed that the backslashes were simply escaping spaces. So, there's no reason for the OP to use sed?

I won't swear to it, but I think I had to start messing with sed because the script wouldn't work, but then I perhaps had it quoted like a good boy ;)

On the brightside, my script now works a treat. What I was doing was farming out the job of copying the album art from conky to an external script, I noticed conky copies the art every single update otherwise (every 1 second)

Going to post the script up in the conky thread, thanks to all.

---

