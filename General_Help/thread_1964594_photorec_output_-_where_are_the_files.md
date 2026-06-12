---
title: "photorec output - where are the files?"
date: 2012-04-24
forum: General Help
---

### Post by engine on 2012-04-24
Successfully ran photorec, which diligently created over 130,000 items on the external hard drive I was using. A bit of fun with grep showed that among these 130,000 items were indeed some references to files in the one directory I'd accidentally deleted.

Question: have the seven deleted files themselves been restored anywhere? if so, where &#8210; and how do I get my eager hands on them again. Thanks in advance for hints and tips.

N

[ps] It would be helpful if undeleting files could be that bit easier, don't you think?

---

### Post by Rhubarb on 2012-04-24
Your previously deleted files _may_ have been restored by photorec - it all depends if it hasn't been overwritten by newer files, or if indeed photorec was able to recognise the filetype(s) you were after.

Your best bet now is to wade through all the files to try to find those 7 files.

For example, if you're looking for text files, consider deleting all the recovered jpg/png/mp3/wav/mpg files.
Then if you know the approximate size, delete all files bigger / smaller than 50kb (for example).
Then just do a grep or similar search within all those files for some key words that you happen to know would be in those files.

Unfortunately it's a bit painstaking and slow to do, but you should get there eventually.

Best of all it should make you more appreciative of making regular backups and to think twice before deleting a directory.
- I've learnt that the hard way myself.

---

### Post by engine on 2012-04-24
I agree entirely about the backups, though it's strange how "once in a blue moon" always strikes the day before "next scheduled backup" <g>

Two more questions, if I may:
[LIST]
[*]what is photorec actually telling me when it includes the names of the lost files in its copious output?
[*]to locate any *.mup files in restored_220412 and its subdirectories, is this the right [FONT="Courier New"]find[/FONT] syntax or do I need another switch for recursion?
```
[prompt]/media/LACIE/restored_220412$ find . -name '*.mup'
```
[/LIST]

---

### Post by oldfred on 2012-04-24
photorec has parameters/settings to only recover certain types of files. I think it still takes just as long to run as it still is scanning drive for anything that looks like a file, but only copies those with the extensions you choose.

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by Rhubarb on 2012-04-25
> **engine said:**
> [LIST]
[*]what is photorec actually telling me when it includes the names of the lost files in its copious output?[/LIST]

I have no idea, thankfully I haven't run photorec since a few years and hadn't noticed that.

> **engine said:**
> [LIST]
[*]to locate any *.mup files in restored_220412 and its subdirectories, is this the right [FONT="Courier New"]find[/FONT] syntax or do I need another switch for recursion?
```
[prompt]/media/LACIE/restored_220412$ find . -name '*.mup'
```
[/LIST]

Yes, that'll find mup files recursively.
But the problem is, is that photorec assumes extensions by what it's found on the surface of the Hard Disk.  So in this case it might find some text (which was a .mup file let's just say), then it dumps the recovered text in it's default text file format, which would be .txt
- So if using find to locate .mup files doesn't work, you may be better off searching for .txt files instead.

It's always a bit messy finding and cleaning up after a big photorec recovery!

---

