---
title: "Getting &quot;don't have permissions&quot; error in Win 7 trying to access a shared Ubuntu file"
date: 2012-04-15
forum: General Help
---

### Post by johnsmoke on 2012-04-15
I have a share folder on my Ubuntu machine and have accessed all the files in it with no problem. Recently I imported a large folder containing many video files into my shared folder from my external hard drive. I figured that they would inherit the "share" settings so that I could access it on my Windows 7 laptop.... When I try to access this folder I get into the share folder from my Win 7 laptop, I can get into the first folder of this new chunk of vid files I put in, but when I try to access any of the sub-folders containing the video files, I get an error on the Win 7 machine saying that I don't have permissions. 

Why can't I access this? I even went into Samba and manually added the main "share" folder to the list of shares... made sure visible was selected as well as "access to everyone." Any help would be appreciated.

---

### Post by CharlesA on 2012-04-15
Did you just mount the external drive, or copy the files to the existing share?

---

### Post by johnsmoke on 2012-04-15
> **CharlesA said:**
> Did you just mount the external drive, or copy the files to the existing share?

I just copied/dragged the folder (from my external HD) into the existing share.

---

### Post by CharlesA on 2012-04-15
Check the permissions then.

```
ls -l
```

Will show what permissions the files have and you can compare them to the ones that work.

---

### Post by johnsmoke on 2012-04-15
> **CharlesA said:**
> Check the permissions then.

```
ls -l
```Will show what permissions the files have and you can compare them to the ones that work.

Just did that, but I don't know how to read the info that came up. "Seinfeld" is the folder that I have trouble accessing (can get into the actual folder, but none of the sub-folders within). Here's what comes up when I use that code for the Seinfeld folder:

johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ ls -l
total 40
drwx------ 11 johnsmoke johnsmoke 4096 2012-04-12 19:52 Extras
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 1
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:47 Season 2
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 3
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 4
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 5
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 6
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 7
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 8
drwx------  2 johnsmoke johnsmoke 4096 2012-04-13 18:49 Season 9
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$

---

### Post by CharlesA on 2012-04-15
Are you trying to access them with the johnsmoke user?

Can you post what the permissions look like for a file that you can access?

---

### Post by johnsmoke on 2012-04-15
> **CharlesA said:**
> Are you trying to access them with the johnsmoke user?

Can you post what the permissions look like for a file that you can access?

Yes, I just go into the johnsmoke network from my Win 7 machine and access my Shared folder from there. Here's permissions for a folder I have full access to with no problem:

johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/Comedy/Bill Hicks$ ls -l
total 2536432
-rw-r--r-- 1 johnsmoke johnsmoke 814527140 2009-02-06 04:50 Bill Hicks - Outlaw Comic.mpeg
-rw-r--r-- 1 johnsmoke johnsmoke 721818618 2009-02-15 20:22 Chicago 1992 (rare).avi
-rw-r--r-- 1 johnsmoke johnsmoke 733317120 2009-02-05 22:07 HBO Special.avi
-rw-r--r-- 1 johnsmoke johnsmoke 327611956 2010-03-22 00:39 On The Seventh Day - Bill Hicks At The Cult Compound.mpg
drwxr-xr-x 2 johnsmoke johnsmoke      4096 2012-03-11 21:51 Rare TV Appearances
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/Comedy/Bill Hicks$

---

### Post by CharlesA on 2012-04-15
Ah gotcha. The permissions are different here, you can change them to match with:

```
chmod -R go+rX /path/to/folder/
```

---

### Post by johnsmoke on 2012-04-15
> **CharlesA said:**
> Ah gotcha. The permissions are different here, you can change them to match with:

```
chmod -R go+rX /path/to/folder/
```

I'm sorry, I'm a bit of a beginner, I'm not sure how to enter the code properly and write the correct path to the folder... here's some of what I've tried just now:

johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV$ cd Seinfeld
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX /Desktop/Shared/Movies\ \&\ TV/TV/Seinfeld
chmod: cannot access `/Desktop/Shared/Movies & TV/TV/Seinfeld': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX johnsmoke-desktop:~/Desktop/Shared/Movies\ \&\ TV/TV/Seinfeld
chmod: cannot access `johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX /Desktop/Shared/Movies\ \&\ TV/TV/Seinfeld
chmod: cannot access `/Desktop/Shared/Movies & TV/TV/Seinfeld': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld
[1] 3031
bash: TV/TV/Seinfeld: No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod: cannot access `johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies': No such file or directory

[1]+  Exit 1                  chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$
[1] 3038
bash: TV/TV/Seinfeld$: No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod: cannot access `johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies': No such file or directory

[1]+  Exit 1                  chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$
[1] 3044
bash: TV/TV/Seinfeld$: No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod: cannot access `johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies': No such file or directory

[1]+  Exit 1                  chmod -R go+rX johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX chmod -R go+rX /path/to/folder/chmod: cannot access `chmod': No such file or directory
chmod: cannot access `go+rX': No such file or directory
chmod: cannot access `/path/to/folder/': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX /path/to/Seinfeld/
chmod: cannot access `/path/to/Seinfeld/': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$ chmod -R go+rX /Desktop/Shared/Movies\ \&\ TV/TV/Seinfeld
chmod: cannot access `/Desktop/Shared/Movies & TV/TV/Seinfeld': No such file or directory
johnsmoke@johnsmoke-desktop:~/Desktop/Shared/Movies & TV/TV/Seinfeld$

---

### Post by CharlesA on 2012-04-15
Easier to just run this:

```
chmod -R go+rX ~/Desktop/Shared/Movies
```

---

### Post by johnsmoke on 2012-04-15
> **CharlesA said:**
> Easier to just run this:

```
chmod -R go+rX ~/Desktop/Shared/Movies
```

Got it! It's working now. Thanks SO much for the helpful info. Really appreciate the help!

---

