---
title: "Batch tagging of MP3s based on the name of directory they reside in"
date: 2009-08-26
forum: General Help
---

### Post by kwaanens on 2009-08-26
I need to tag a lot of mp3s with additional information to the comment field, in order to have good playlist filters. We're talking 1000s of files.

Basically, I need to add "Tag: LIVE" to the comment tag to all files in sub-sub-subdirectories called "live" of the directory "music".

Does anyone know first of which tool I can use for this, secondly a small bash command that will allow me to do that to all files matching my criteria.

I briefly looked at eye3d, but as far as I can tell, that will only replace the comment, not add to it. If I have to, I'll do that, but taht would be suboptimal

Thanks!

---

### Post by CatKiller on 2009-08-26
EasyTAG will do what you've asked for in the thread title. I don't know about command-line tools to add a Comment tag, though. Actually, I just did a quick search and **mp3info** is just such a thing. You could probably run that as part of a *find* command to add a comment to each file.

---

### Post by kwaanens on 2009-08-26
I have used EasyTag for years, and I have never seen a way to batch tag all files that reside in directories called "n". There isn't even a way to use ctrl and select multiple directories. EasyTag is great, but does not do much of what I need it to do for this particular case.
Any run-of-the-mill graphic tag editor can tag multiple files, but as far as I know, there is none that allows me to batch tag across directories, tagging only files that reside in dirs with specific names.
So that leaves me with a command line tool, but I haven't come across anyone that has the built-in capabilities to do this either.

I guess I'll try eyed3 and try to work out some bash magic to batch tag based on names of parent directories, then pull out the comment of each file, adding it back together with the content I wish to add.
If anyone knows how to do this easily, please don't hesitate to save me massive amount of man hours trying to figure out a simple script :)
Sigh... If there just were an easier way to do this.

---

### Post by CatKiller on 2009-08-26
> **kwaanens said:**
>  So that leaves me with a command line tool, but I haven't come across anyone that has the built-in capabilities to do this either.

All you need is a command-line tool that can add a comment to one file, like the one that I specified earlier. All the rest - which files you want tagged - will be handled by the rest of the command.

So you might use something like
(Bear in mind I've never done this)
```
find /path/to/top/directory -name "*.mp3" -exec mp3info -c CommentYouWantToAdd '{}'
``` to add a comment to every file whose name ends with ".mp3" in a subdirectory from the one you specify. You can use -mindepth or -maxdepth to tweak your query.

---

### Post by kwaanens on 2009-08-26
Thank you, but this only does part of what I need it to.
The problem is that the files that need tagging reside in directories, that reside in directories called "live". There are other directories with mp3s that I don't want the script to touch. Graphically it's like this:

Dir: Music
|----------> Artist 1
_____________|-------> album 1
_____________|-------> album 2
_____________|-------> live
________________________|------> live album 1
________________________|------> live album 2
|----------> Artist 2, etc,etc

Hopefully, this is understandable. The point is, I want to tag all mp3 from the point "live" and out, but not the files in "album 1" and "album 2".
All this results in a heavy mess that I'm having a hard time figuring out. The hierarchy is very intuitive, but my scripting skills are not up to par :(

---

### Post by CatKiller on 2009-08-26
> **kwaanens said:**
> my scripting skills are not up to par :(

Mine either :)

You can probably adjust the *find* command so that it only looks in sub-folders called "live" easily enough. Or change the * /path/to/top/directory* to /something/Music/Artist 1/live and run the command, then /something/Music/Artist 2/live and run the command, and so on.

It all depends on whether you'll find it quicker to just do it in a non-optimal way or to learn how to craft your regular expressions to do it all in one command.

---

### Post by DaithiF on 2009-08-26
Hi,
cd to the music directory, then:
```
find . -iname "*.mp3" -path "*/live/*"
```
should give you the files you want -- when you're happy thats giving you the list you need, add the -exec dosomething {} \; piece to the end.

---

### Post by kwaanens on 2009-08-27
Thank you so much! I believe that will do the trick!

---

### Post by kwaanens on 2009-08-27
I ended with:
```
find . -iname "*.mp3" -path "*/live/*" -exec eyeD3 --v2 --comment=::"Here goes comment" {} \;
```

Unfortunately, it does not keep my old comment, and just add to it.

For anyone else trying to do this, I did not succeed with mp3info or id3tool because they are id3 version 1 only. (Shouldn't that be pretty obsolete by now?) id3v2 did not fulfill my needs either, but I've been fiddling so much, I forget why.

---

