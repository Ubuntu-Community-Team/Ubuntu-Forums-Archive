---
title: "A good compressor"
date: 2009-07-14
forum: General Help
---

### Post by Japjeev on 2009-07-14
so is there a good compresser that can make my 6.4gb file atleast 1.5gb or less?i already tryed peazip.7zip doesnt work for me 0.o

---

### Post by NightwishFan on 2009-07-14
Compression is generally only as good as the file you are compressing. I would recommend LZMA, however you probably will not get more than 50% compression and likely will not get anywhere near that. Good luck!

---

### Post by RoestVrijStaal on 2009-07-14
Maybe WinRAR via Wine... but I think even that compress the file to 1.5 GB. 

I advice you could better compress and split up the file in 1.5 GB pieces. Do this only if your USB / External drive really have 1.5 GB. Most of the count of GB's mentioned are only a commercial trick, in real life a 1 GB USB-stick is just 944 MB. I don't know how many MB's have a 1,5 USB-Stick / External drive, but I know sure it's not 1500 MB. :)

---

### Post by lukeiamyourfather on 2009-07-14
What are you compressing? That will matter probably more than what compression utility is used. For example a ASCII text file that says "Pizza" a few hundred millions times might be a few GB text file, but only a few KB when compressed because its all the same thing. A format with native compression like PNG or MP3 will be the same size if not slightly larger when compressed in an archive.

Maybe splitting a single large file into multiple smaller compressed archives might help if it won't fit onto whatever media is being used. Cheers!

---

### Post by Japjeev on 2009-07-14
> **lukeiamyourfather said:**
> What are you compressing? That will matter probably more than what compression utility is used. For example a ASCII text file that says "Pizza" a few hundred millions times might be a few GB text file, but only a few KB when compressed because its all the same thing. A format with native compression like PNG or MP3 will be the same size if not slightly larger when compressed in an archive.

Maybe splitting a single large file into multiple smaller compressed archives might help if it won't fit onto whatever media is being used. Cheers!


so how do i put it into parts btw the file is a iso that i want to compress

---

### Post by Blacklightbulb on 2009-07-14
> **NightwishFan said:**
> Compression is generally only as good as the file you are compressing. I would recommend LZMA, however you probably will not get more than 50% compression and likely will not get anywhere near that. Good luck!

Well I my memory isn't leaking once I downloaded a 64KB game on some strange format and after 8 hours of decompressing it was 800MB O.O

How's that thing working when usually you can't get over 50%?

---

### Post by moster on 2009-07-14
> **Japjeev said:**
> so how do i put it into parts btw the file is a iso that i want to compress

First open file roller. hm, I cannot find it on menu so just click on any archive you can find. Now, make new archive and select 7zip. He  allow you to make split archives and select how big you want it to be. 7zip is one of the best compressors, if he cannot make it smaller, no other can be much better.

---

### Post by Slim Odds on 2009-07-14
> **Blacklightbulb said:**
> Well I my memory isn't leaking once I downloaded a 64KB game on some strange format and after 8 hours of decompressing it was 800MB O.O

How's that thing working when usually you can't get over 50%?

No way!

Maybe 640MB --> 800MB

Unless all of the data is zeros or all the same ASCII character.

For "real" data, there's just no way to get that much compression.

---

### Post by lukeiamyourfather on 2009-07-14
> **Blacklightbulb said:**
> Well I my memory isn't leaking once I downloaded a 64KB game on some strange format and after 8 hours of decompressing it was 800MB O.O

How's that thing working when usually you can't get over 50%?

That's pretty vague. :^o

---

### Post by Slim Odds on 2009-07-14
> **lukeiamyourfather said:**
> That's pretty vague. :^o

No... it's called fantasy.  ;)

---

### Post by lukeiamyourfather on 2009-07-14
> **Japjeev said:**
> so how do i put it into parts btw the file is a iso that i want to compress

The archive tool that shows up in GNOME context menus will make split archives if you have 7-Zip installed. If you already have 7-Zip installed then right click whatever you want to put in an archive, select "Create Archive..." and then select the format of 7z. There's options at the bottom to specify how large each chunk should be.

If you don't already have 7-Zip installed do this command to install it, which also has some other nifty formats. Try to avoid installing RAR if you can, its rubbish.

```
sudo apt-get install p7zip-full
```

Note that 7-Zip will be required to extract the archive, and all of the pieces will need to be available too. Cheers!

---

### Post by CatKiller on 2009-07-14
> **Japjeev said:**
> so how do i put it into parts btw the file is a iso that i want to compress

If you've installed the rar package, you can just right-click on the file and select Create Archive... to make a multi-part rar archive. There may be other formats that make it easy to make one archive span multiple files, but that should be sufficient.

> **Blacklightbulb said:**
> Well I my memory isn't leaking once I downloaded a 64KB game on some strange format and after 8 hours of decompressing it was 800MB O.O

How's that thing working when usually you can't get over 50%?

That isn't compression, that's self-modifying code. There are some interesting things that you can do with computers, you know :) If you like that kind of thing, you might want to check out the International Obfuscated C Contest or the 5k contest.

---

### Post by NightwishFan on 2009-07-15
I have a vague idea how compression works under the hood. From what I know, to achieve lossless compression on average data will not lead to impressive results. Frankly I am not sure how to 'split' data into multiple archive, though I believe it is possible with 7z, rar and zip.

---

### Post by Slim Odds on 2009-07-15
> **NightwishFan said:**
> Frankly I am not sure how to 'split' data into multiple archive, though I believe it is possible with 7z, rar and zip.

You can always use the split command to split any file.

```
SPLIT(1)                                            User Commands                                            SPLIT(1)

NAME
       split - split a file into pieces

SYNOPSIS
       split [OPTION] [INPUT [PREFIX]]

DESCRIPTION
       Output  fixed-size  pieces of INPUT to PREFIXaa, PREFIXab, ...; default size is 1000 lines, and default PREFIX
       is ‘x’.  With no INPUT, or when INPUT is -, read standard input.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --suffix-length=N
              use suffixes of length N (default 2)

       -b, --bytes=SIZE
              put SIZE bytes per output file

       -C, --line-bytes=SIZE
              put at most SIZE bytes of lines per output file

       -d, --numeric-suffixes
              use numeric suffixes instead of alphabetic

       -l, --lines=NUMBER
              put NUMBER lines per output file

       --verbose
              print a diagnostic to standard error just before each output file is opened

       --help display this help and exit

       --version
              output version information and exit

       SIZE may have a multiplier suffix: b 512, kB 1000, K 1024, MB 1000*1000, M  1024*1024,  GB  1000*1000*1000,  G
       1024*1024*1024, and so on for T, P, E, Z, Y.

```

---

### Post by lisati on 2009-07-15
The ability to effectively compress a file can depend on the data, and some files are already highly compressed, e.g. jpg, mpg.

I must confess that some of the algorithms go beyond my level of comprehension, particularly the more effective ones. A few years back, when I tried coming up with a "home grown" data compression program for my own use with files that were mainly text files, the best I could manage was something like 50%.

---

### Post by Slim Odds on 2009-07-15
> **lisati said:**
> I must confess that some of the algorithms go beyond my level of comprehension, particularly the more effective ones. A few years back, when I tried coming up with a "home grown" data compression program for my own use with files that were mainly text files, the best I could manage was something like 50%.

If the files are mainly text, they should compress a lot more than 50%.

Compression is all about data analysis. That's why it takes so much longer to compress than uncompress. Also, different techniques work better for different types of data.

For example, text has totally different needs than audio data to get high compression ratios.

---

### Post by lisati on 2009-07-15
> **Slim Odds said:**
> If the files are mainly text, they should compress a lot more than 50%.

Compression is all about data analysis. That's why it takes so much longer to compress than uncompress. Also, different techniques work better for different types of data.

For example, text has totally different needs than audio data to get high compression ratios.

I agree that for text files, it's possible to do better than 50%. I was just too lazy to do the research to refine what I had.

---

### Post by NightwishFan on 2009-07-16
Thank you for the split tip! Is that installed by default in Jaunty? (On windows right now pending new inet at home) :(

---

