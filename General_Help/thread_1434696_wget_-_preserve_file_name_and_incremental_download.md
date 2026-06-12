---
title: "wget - preserve file name and incremental downloading"
date: 2010-03-20
forum: General Help
---

### Post by marXman on 2010-03-20
Dear Ubuntu users,

I'm having a little problem with figuring out how to make wget behave the way I want it to. My *nix experience is somewhat limited, but I have a fair assumption that wget can perform the following tasks, I just don't know *how*.

**1) Preserving file names**
When downloading a dynamic URL with wget (ex. [http://www.example.com/download.php?did=232](http://www.example.com/download.php?did=232)), the file gets the name "download.php?did=232" instead of File001.doc which Firefox's download manager saves it as. How can I make wget keep the original file name?

**2) Incremental/decremental downloading**
First of all, I would like to point out an existing program I use for Firefox. It's called URL Flipper, and it's just the thing I need.

[IMG]http://code.kliu.org/urlflipper/screenshots/pattern_setup-3.0-aero.png[/IMG]

As you can see from the picture, it's pretty self-explanatory. I'm looking for something similar, but it doesn't need to be as complex as URL Flipper. It only needs to handle decimals, and I plan to use it together with question **1)** as mentioned above.


Why not just keep using URL Flipper and Firefox, you may ask, as it could solve both my problems. Well, it's an awful lot of manual labour, and I was hoping to set up a script which could turn it all into an automated process. Therefore, I turn to you, almighty cloud of savvy Linux users. Can you help me out on this one?

---

### Post by asmoore82 on 2010-03-20
I've used this shell script stub a lot:

```
#!/bin/bash

stem="http://some.url/download.php?id="
type=".mp3"

for num in {301..4000}
do
   wget -O "File_${num}${type}" "${stem}${num}"
done

#End of File
```

---

### Post by marXman on 2010-03-20
> **asmoore82 said:**
> I've used this shell script stub a lot:

```
#!/bin/bash

stem="http://some.url/download.php?id="
type=".mp3"

for num in {301..4000}
do
   wget -O "File_${num}${type}" "${stem}${num}"
done

#End of File
```

Thanks for the feedback, **asmoore82!**

I guessing "wget -O" specifies output file name, in this case File_[digit_from_url]? And 301-4000 is the specified number range?

This is a really good start - now, if I could only figure out how to fetch the original file name and output it correspondingly...

---

### Post by marXman on 2010-03-22
Bumping, since I'm still looking for a solution for question 1)

> 1) Preserving file names
When downloading a dynamic URL with wget (ex. [http://www.example.com/download.php?did=232](http://www.example.com/download.php?did=232)), the file gets the name "download.php?did=232" instead of File001.doc which Firefox's download manager saves it as. How can I make wget keep the original file name?

---

### Post by faopvnc on 2010-04-01
> **marXman said:**
> 
When downloading a dynamic URL with wget (ex. [http://www.example.com/download.php?did=232](http://www.example.com/download.php?did=232)), the file gets the name "download.php?did=232" instead of File001.doc which Firefox's download manager saves it as. How can I make wget keep the original file name?

Posting here since it was the first google result I looked at when trying to figure this out myself. Google actually tried to help me by suggesting I search for "wget content disposition" but I ignored it and instead launched a new search for what the name of that header was that let you set a file to be an attachment and force a browser to download it, since surely there'd be threads talking about wget and that header... which of course turned out to be Content-Disposition.

```
wget --content-disposition <URL>
``` will cause wget to save to the filename specified in the Content-Disposition header. It should work if you have a wget that's version 1.11 or newer. **BUT** [the wget manual]("http://www.gnu.org/software/wget/manual/html_node/HTTP-Options.html#index-Content_002dDisposition-100") warns about its newness, its buginess, and says it will result in an extra trip to the server per-file (to perform a HEAD request, learning the filename, before GETing the file), so you probably don't want to use it if doing a mass download.

But that's ok for me, and it's exactly what I need to speed up redownloading all my favourite scripts from vim.org.

---

