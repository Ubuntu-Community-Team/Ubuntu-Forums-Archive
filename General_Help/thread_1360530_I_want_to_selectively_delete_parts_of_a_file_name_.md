---
title: "I want to selectively delete parts of a file name from some files"
date: 2009-12-21
forum: General Help
---

### Post by skooma314 on 2009-12-21
I have some music that was named really badly and confuses Winamp and Mediamonkey resulting in it being poorly tagged, which means Last.fm get those bad tags later.

I want to use this as an opportunity to use my Ubuntu partition and engage in some script-fu. Any pointers on how I should go about this? I can do basic functions in Bash and I'm about 9 pages into the Camel Book (O'Reilly Perl book).

The files are all named like "01-the_radio_dept-**too_soon-**twee.mp3" with the part in bold being what I want to keep. They will require their own scripts to remove underscores and put the artist title in front.

---

### Post by prshah on 2009-12-21
> **skooma314 said:**
> 
The files are all named like "01-the_radio_dept-**too_soon-**twee.mp3" with the part in bold being what I want to keep. They will require their own scripts to remove underscores and put the artist title in front.

Sorry, I cannot advise you on a suitable script; however, you can consider using ExFalso (from the repositories); it will allow you to (interactively) rename a bunch of files by creating the filename from the embedded MP3 tags.

Eg, you can multi-select the files you want to rename, then specify the new name format as (Eg) <Album>-<Track#>-<Title> etc. Of course this presumes that the embedded tags are correct and to your liking.

Just a suggestion...

---

### Post by skooma314 on 2009-12-21
> **prshah said:**
> Sorry, I cannot advise you on a suitable script; however, you can consider using ExFalso (from the repositories); it will allow you to (interactively) rename a bunch of files by creating the filename from the embedded MP3 tags.

Eg, you can multi-select the files you want to rename, then specify the new name format as (Eg) <Album>-<Track#>-<Title> etc. Of course this presumes that the embedded tags are correct and to your liking.

Just a suggestion...

The tags are messed up from my screwing with them in Winamp and Mediamonkey. I could just redownload them but I'd rather do it this way. :)

---

### Post by pbrane on 2009-12-21
one thing to look at is the **rename** command. you can do someting like
```

rename 's/01-the_radio_dept-/best_artist_ever/' *.mp3

```

assuming that all the same artists songs are in one directory. This would replace **01-the_radio_dept-** with **best_artist_ever** on all mp3 files in that directory. If the prefix is different for each file then you may have to write a script to sort that out.

you can look at the man page for rename or search the web for examples.

---

### Post by kaibob on 2009-12-21
> **skooma314 said:**
> The files are all named like "01-the_radio_dept-**too_soon-**twee.mp3" with the part in bold being what I want to keep.

You have to post more examples of file names before anyone can really answer your question. With the example given, you could use one of many methods to extract the string identified in your post. For example, it could be done with awk as follows:

> $ echo "01-the_radio_dept-too_soon-twee.mp3" | awk -F "-" '{ print $3 }'
too_soon

---

