---
title: "Automating the cleanup of a plaintext  file"
date: 2011-05-17
forum: General Help
---

### Post by Monsuco on 2011-05-17
I have this gargantuan hosts file that I use on a wide range of Windows and Linux computers to filter out banner ads, undesirable sites, etc. I realize that using the hosts file to do this is "primitive" but it is cross-platform, simple, and rather effective.

I compiled this large (1.2 MB, pretty big when you consider it's plaintext) hosts file using a large number of list I came across online. Many of these contained frequent comments and there are a lot of duplicates. Is there any way to script the removal of all of these comments, blank lines, and duplicate lines?

Some of the commented lines appear to be appended to the end of regular lines like so.
```

127.0.0.1 www.example.com #random comment attached to the line.

```

In these cases I just want to script the removal of all comments.

I realize this isn't 100% necessary but I am a little obsessive and would like to be able to keep my hosts list nice and tidy.

---

### Post by scottstensland on 2011-05-17
cat yourBigFile |cut -d'#' -f1 > NewBigFile

which will cut the file by delimitor of # and pick column 1

eliminate duplicate rows using

        cat NewBigFile | sort -u > NewBigFileUniqueRows

leverage the power of unix by doing both operations on one line :

        cat yourBigFile | cut -d'#' -f1|sort -u > NewBigFileUniqueRows


cheers - Scott Stensland

---

### Post by dragonfly41 on 2011-05-17
You'll probably get a lot of ideas here on using regexp ..

I would just like to recommend a nice tool I have used on log files etc. using text piping

[http://www.fireflysoftware.com/textools/](http://www.fireflysoftware.com/textools/)  

which runs on windows (but not free unfortunately)

---

### Post by Monsuco on 2011-05-18
Thank you very much for showing me the cat command. Hurray for delicious Unix text tools. I have my file all cleaned up with no comments but my own remaining. I was able to merge separate parts of the list using your commands and good 'ol cut and paste and cleaned out the other comments. [As you can see]("https://sites.google.com/site/monsuco/files/hosts?attredirects=0&d=1") it is nice and clean now. There used to be like 3 major list for the banner ads with a lot of overlap and there were a few list under banner ads for specific companies. You can also see why I didn't want to manually edit such a massive file. 1.2 MB of plaintext is far too beefy.

I use this thing so much at my work since we can't afford a proper web filter on the Windows boxes. I also use it at home to filter banner ads on my Linux PC's (along with Adblock Plus, but sometimes I can't use that). I've sorta  been thinking about setting up a caching proxy at my work using something like squid and using this to make it so I can apply filtering company-wide (sadly we lack Active Directory). You've been a big help.

---

