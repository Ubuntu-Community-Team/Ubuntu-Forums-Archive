---
title: "renaming files by Shotwell 'title'"
date: 2011-03-31
forum: General Help
---

### Post by ottadini on 2011-03-31
Hi, I've used Shotwell to give titles to a lot of photos, and now realise that I want to also rename those files using the title. I see that Shotwell saves the **title** into XMP IPTC structure, using this: dc:title[x]. Anyone have any tips on how to batch rename a bunch of files using this data?

ben.

---

### Post by lombaardcj on 2011-04-04
Hi ottadini,

Have a look at this forum [post]("http://ubuntuforums.org/showthread.php?t=95058").

If you still having issues, let me know.  If you know a little bash scripting, look at **exiv2** package.  It comes with very neat options to perform amazing things with EXIF and IPTC tags on pictures.

I also came across this [wesite]("http://freefoote.dview.net/linux_exif.html") in looking for an answer for you. This guy actually did some cool stuff with very little.

---

### Post by ottadini on 2011-04-04
Hi mate, thanks for the info. 
I had a look at exiv2, it's quite powerful, but didn't rename files in place (as far as I could figure out). 

I eventually used exiftool by Phil Harvey  ([http://www.sno.phy.queensu.ca/~phil/exiftool/]("http://www.sno.phy.queensu.ca/%7Ephil/exiftool/")), which has some  excellent features, including rename files in place. Definitely  recommended!

Here's a sample command (I think this is it, but don't quote me):
```
exiftool '-FileName<${Headline}.jpg' ./temp/*.jpg
```This renames all of the files in the temp dir using the 'Headline'  metadata. In my case, that was also set by Shotwell (version 0.9 I  think?) when it changed the title. 

Ben.

---

### Post by lombaardcj on 2011-04-05
Great!

I'm glad you solved your own problem.

I've had a look at exiftool and it looks pretty neat.

Cheers

---

