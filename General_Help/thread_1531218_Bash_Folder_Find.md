---
title: "Bash Folder Find"
date: 2010-07-14
forum: General Help
---

### Post by somidscr21 on 2010-07-14
I apologize if this is not in the right place, however, I did not see a more appropriate category.

I am trying to clean up my music library, which is rather large, and one issue I keep running into artist folders being split into two. For example I see "Black Crowes" and "The Black Crowes." I feel like this is an easy command I am missing, but is there a way to search my music directory for Black Crowes and get both of them to return? With such a large library, it's a PITA to look one by one.

Also, is there some way I can automate this to look at all my artists and tell me which ones have multiple folders?

---

### Post by gzarkadas on 2010-07-16
You can use `find' and / or `locate'. Some examples follow. All assume you have first changed to the top directory of your music collection, ie did a:
```

cd <top-directory-of-your-music>

```1a. This will show you the directories (only) that match a pattern
```

find -type d -a -name '*Black Crowes*'

```1b. This will show you the files (only) that match a pattern; use the suspected directory (artist) name as pattern to get all the related files
```

find -type f -a -name '*Black Crowes*'

```1c. This is like 1b, only much faster, but may miss new additions until the locate database is updated by the (configured) cron job.
```

 locate '*Black Crowes*'
 
```

---

### Post by somidscr21 on 2010-07-16
Awesome, I figured it was a fairly easy command I was just missing. Now on to building the rest of my script! :-)

Eventually I'm hoping to find all of the folders like this, then have it display the album folders inside the artist folder, then merge the two asking me for each.

Maybe a little complex, or a little bit of an ugly way of doing it, but half the fun is in making this work.

Thanks again.

---

### Post by bodhi.zazen on 2010-07-16
> **gzarkadas said:**
> This is like 1b, only much faster, but may miss new additions until the locate database is updated by the (configured) cron job.

Or you can manually update the database

```
sudo updatedb
```

---

### Post by somidscr21 on 2010-07-16
Ya I am familiar with that command, I was thinking that might help so I don't have to wait. Now I guess my only question left is does anyone know how to automate this? By that I mean I run a command and it finds all of the duplicates for me. This way I would not have to know there is a Black Crowes and a The Black Crowes, it would just tell me that it exists.

---

### Post by yaaarrrgg on 2010-07-16
> **somidscr21 said:**
> Ya I am familiar with that command, I was thinking that might help so I don't have to wait. Now I guess my only question left is does anyone know how to automate this? By that I mean I run a command and it finds all of the duplicates for me. This way I would not have to know there is a Black Crowes and a The Black Crowes, it would just tell me that it exists.

That would require a little programming.  You might use the following:

1. list of aliases, with spelling variants, that you'd parse and check  Eg:

   The Black Crowes, Black Crowes, Black Crows, The Black Crows

2. reduce titles down to metaphone, or soundex code
3. do sha hash on files and use to compare contents of files

You probably wouldn't want to automatically delete though, but only list what could be a duplicate.

---

### Post by bodhi.zazen on 2010-07-16
> **somidscr21 said:**
> Ya I am familiar with that command, I was thinking that might help so I don't have to wait. Now I guess my only question left is does anyone know how to automate this? By that I mean I run a command and it finds all of the duplicates for me. This way I would not have to know there is a Black Crowes and a The Black Crowes, it would just tell me that it exists.

try fdupes

[http://embraceubuntu.com/2005/10/08/find-duplicate-copies-of-files/](http://embraceubuntu.com/2005/10/08/find-duplicate-copies-of-files/)
[http://www.serverschool.com/dedicated-servers/how-to-delete-duplicate-files-in-linux/](http://www.serverschool.com/dedicated-servers/how-to-delete-duplicate-files-in-linux/)

Otherwise use find || locate and pipe them through | sort | uniq -d

If you want a gui this looks interesting

[http://www.junauza.com/2010/01/how-to-find-and-clean-up-duplicate.html](http://www.junauza.com/2010/01/how-to-find-and-clean-up-duplicate.html)

---

### Post by somidscr21 on 2010-07-16
Currently learning Perl, do you think this would be a good project to work on with Perl? Originally I was envisioning a bash script, but if Perl would be better...

@bodhi: does fdupes do folders like the situation I've explained? I thought it only did files. I also wasn't a huge fan, but if it keeps me from having to manually do it, it would be fine.

---

### Post by bodhi.zazen on 2010-07-16
> **somidscr21 said:**
> @bodhi: does fdupes do folders like the situation I've explained? I thought it only did files. I also wasn't a huge fan, but if it keeps me from having to manually do it, it would be fine.

I do not know if it is what you are looking for, or if you are interested in learning to program ...

```
fdupes /dir_1 /dir_2
```

```
fdupes -r /home/music
```

---

### Post by somidscr21 on 2010-07-16
I need to learn Perl for work so I'm not opposed to using that if possible, also I am familiar with bash scripting so I could use that too.

Doesn't what you just showed me compare files in the two directories though?

---

### Post by bodhi.zazen on 2010-07-16
> **somidscr21 said:**
> Doesn't what you just showed me compare files in the two directories though?

I am not sure what you are asking or how you would identify duplicates without comparing the files. If the files are the same, the directories are the same. No ?

[http://manpages.ubuntu.com/manpages/lucid/en/man1/fdupes.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/fdupes.1.html)

> **[B]DESCRIPTION**[/B]

       Searches  the  given  path for duplicate files. Such files are found by
       comparing file sizes and MD5 signatures,  followed  by  a  byte-by-byte
       comparison.

---

### Post by somidscr21 on 2010-07-16
I'm sorry I realize I'm probably not doing a good job of explaining. I mean duplicates as in one folder called "Black Crowes" and another called "The Black Crowes." I am not concerned with duplicate ogg/mp3/wma files at this point in time.

---

### Post by bodhi.zazen on 2010-07-16
> **somidscr21 said:**
> I'm sorry I realize I'm probably not doing a good job of explaining. I mean duplicates as in one folder called "Black Crowes" and another called "The Black Crowes." I am not concerned with duplicate ogg/mp3/wma files at this point in time.

If you try fdupes and it does not do what you wish, you will likely need to then code something yourself, either in bash or perl or any tool you wish =)

---

### Post by somidscr21 on 2010-07-16
Sounds like a plan. Thanks for sticking with me through my difficulties explaining.

---

### Post by bodhi.zazen on 2010-07-16
> **somidscr21 said:**
> Sounds like a plan. Thanks for sticking with me through my difficulties explaining.

No problem. We could probably write something for you, but that kind of takes the fun out of it.

From your posts I suggest you try coding something and if you run into problems post your script ;)

---

### Post by gzarkadas on 2010-07-16
> **bodhi.zazen said:**
> ...try fdupes...

It is amazing what wealth of functionality resides in one's filesystem without him/her knowing it; just did a `man fdupes' and saw it there. Thanks :D; will start studying it!

---

### Post by yaaarrrgg on 2010-07-16
> **somidscr21 said:**
> Currently learning Perl, do you think this would be a good project to work on with Perl? Originally I was envisioning a bash script, but if Perl would be better...


Perl might be easier for this, IMO.  It's got regular expressions built in, and it sounds like you might be doing mostly pattern matching.

---

### Post by bodhi.zazen on 2010-07-16
> **gzarkadas said:**
> It is amazing what wealth of functionality resides in one's filesystem without him/her knowing it; just did a `man fdupes' and saw it there. Thanks :D; will start studying it!

You are most welcome, enjoy. The eye candy addicts do not know what they are missing :D

---

### Post by blur xc on 2010-07-16
I've run into a similar problem- and I manually fixed it in the file system (my collection isn't that big, or wasn't, back when I fixed it) but it sitll not fixed in Banshee and Rhythmbox.  Apparently, they read the song's metadata, not the directory names where the music resides, so even though all albums by The O.C. Supertones are now in one directory, in Banshee and Rhythmbox, they are still OC Supertones, O.C. Supertones, The O.C. Supertones, etc... it's really irritating.  I made a script using mp3info to edit the id3 tags to match the folder structure, and foolishly ran it globally across my whole music collection (after ripping a couple hundred more old cd's into) which messed up the artist information on all my compilation albums (of which there are many) and the only way I can think to fix it is to re-rip those cd's...which should take a few hours.

The sad, maybe even ironic thing, is that it that though it fixed the metadata on a few albums, it didn't fix all  of them.  I don't know what to do about that, besides throw a tantrum and yell obscenities at Banshee and Rhythmbox.

Good luck.
BM

---

### Post by somidscr21 on 2010-07-19
So I gave it the old college try and what I have so far is [here]("http://pastebin.com/HScgimi5"). Now it almost works, I think. The main problem I am running into right now (and only one that I'm currently aware of), is that on the rsync command, it seems to be traversing backwards up the directory tree. Basically when I'm done, it creates the new folders correctly, but it rsyncs over my entire home directory.

Btw my inputs for music folder /home/xxx/Music and the folder to house the new artist folders is /home/xxx/new.

Any ideas?

ps. I realize my code may not be the cleanest, if you have any ideas on how to clean it up, those would be great too.

---

