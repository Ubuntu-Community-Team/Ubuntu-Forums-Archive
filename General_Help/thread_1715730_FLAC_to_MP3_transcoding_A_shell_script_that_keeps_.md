---
title: "FLAC to MP3 transcoding: A shell script that keeps ID3 tag info?"
date: 2011-03-27
forum: General Help
---

### Post by pedrogent on 2011-03-27
My aim is to create a bash shell script that I can use in directories with many subdirectories full of .flac files for mass transcodings that recquire minimal user input.

At present I have this file at ~/bin/flac2mp3:

```
#!/bin/bash
file="$1"
flac -cd "$file" | lame --preset fast extreme - "${file%.flac}.mp3"
```

I navigate to the directory in question and run:

```
find . -name '*.flac' -exec ~/bin/flac2mp3 '{}' \;
```

This does a good job of running recursively through the subdirectories, converting every .flac to a VBR .mp3. However, the tag information from the original .flac files is not transferred in the process. This somewhat defeats the purpose of having a highly automated process such as this as I then have to use a program such as EasyTAG to check against tag databases if I want well tagged .mp3 files. (And who doesn't?)

So then, I wonder if someone can help me add to this shell script so that tag information is accounted for and properly transferred.

Thanks very much in advance.

---

### Post by tredegar on 2011-03-27
> However, the tag information from the original .flac files is not transferred in the process.
From freshmeat:> flac2mp3 is a Perl script to convert FLAC files to MP3 format. It will process an entire directory tree and put the MP3 files in a similar structure. Tags are converted where possible. 

But *your* "flac2mp3" is basically just a bash "one-liner", which uses lame (which does have options for handling ID3 tags [but which you are not using])

Try the **flac2mp3** from [freshmeat]("http://freshmeat.net/projects/flac2mp3/")
If that fails try [another tool]("https://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3")

---

### Post by pedrogent on 2011-03-27
Thanks a lot tredegar, I'll take a look at those. I'll report back tomorrow on how I went.

Cheers.

---

