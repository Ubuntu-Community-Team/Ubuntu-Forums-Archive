---
title: "Simple scripting question"
date: 2010-04-27
forum: General Help
---

### Post by oldmankit on 2010-04-27
Hello,

It's taken me all morning, but I'm very pleased to say that I can now batch edit ID3v2 tags for my mp3s very easily.  

The program is called id3v2 (available in the repositories).  My task was to change genres recursively.  The -g option sets the genre.  Here's what I've come up with:

```
~/music$ find dance\ and\ electronica/ -iname '*.mp3' -print0 |xargs -0 /usr/bin/id3v2 -g "dance & electronica"
```Now I want to run this on every sub-folder in my music folder, setting the genre according to the name of the sub-folder.  

Instead of typing 
```
find <name of sub-folder> blah blah blah -g <name of sub-folder>
```is there something that will completely automate the whole process for me?  Something that will find a subfolder and then pass the name of that subfolder to be used by id3v2 to write the genre?

Thank you!

---

### Post by Brandon Williams on 2010-04-27
Assuming that you're in the parent directory of the subfolders and that all subfolders you want to run this for have the same parent directory, this should work:
```
# find all directories at this level; uses read because of spaces in dirnames
find -mindepth 1 -maxdepth 1 -type d | while read DIRNAME
do
    # get rid of the "./" at the beginning of DIRNAME
    GENRE="${DIRNAME#./}"
    # run the original find command for the dir
    find "$DIRNAME" -iname '*.mp3' -print0 | xargs -0 /usr/bin/id3v2 -g "$GENRE"
done
```


PS: Questions like these should go in the "Programming Talk" forum under "Development & Programming".

---

### Post by oldmankit on 2010-04-28
> PS: Questions like these should go in the "Programming Talk" forum under "Development & Programming".Thanks for the pointer.

> **Brandon Williams said:**
> Assuming that you're in the parent directory of the subfolders and that all subfolders you want to run this for have the same parent directory, this should work:
```
# find all directories at this level; uses read because of spaces in dirnames
find -mindepth 1 -maxdepth 1 -type d | while read DIRNAME
do
    # get rid of the "./" at the beginning of DIRNAME
    GENRE="${DIRNAME#./}"
    # run the original find command for the dir
    find "$DIRNAME" -iname '*.mp3' -print0 | xargs -0 /usr/bin/id3v2 -g "$GENRE"
done
```
Wow, thank you.  This is one reason why I love ubuntu, linux, and open source in general.  People willing to share their time and expertise to help complete strangers. 

That code is beyond my ability to write but I can see follow you've done.  I tried running it on a small portion of my music (wma format) but found that id3v2 isn't able to edit the tags.  So I've gone and downloaded Perl Audio Converter and am converting all .wma and .m4a to .mp3 format.  When that's done, I'll run the script and say how it went.

Thank you again.

---

### Post by Brandon Williams on 2010-04-29
> **oldmankit said:**
> I've gone and downloaded Perl Audio Converter and am converting all .wma and .m4a to .mp3 format.

One thing to keep in mind about this process is that you might be compromising the audio quality by doing this conversion. Is either side of the conversion lossless? If not, then you are most likely converting from one compression format to another, losing more data along the way. If you can avoid such a conversion, you'll be happier with the result.

[This thread](http://ubuntuforums.org/showthread.php?t=181795) refers to software called picard for retagging wma. It also says that amarok supports retagging wma.

---

### Post by oldmankit on 2010-05-01
A thousand thank-yous.  All of my mp3s are now tagged neatly and I have the tools to do it automatically in the future.

> **Brandon Williams said:**
> [This thread]("http://ubuntuforums.org/showthread.php?t=181795") refers to software called picard for retagging wma. It also says that amarok supports retagging wma.

I guess eliminating m4a and wma from my system would be nice, but for the sake of quality I'll leave them as they are and try tagging them manually with amarok (unless anyone knows how to convert to mp3 without noticeable loss of quality).   I'll do that as soon as I've upgraded to 10.04.

:P

---

