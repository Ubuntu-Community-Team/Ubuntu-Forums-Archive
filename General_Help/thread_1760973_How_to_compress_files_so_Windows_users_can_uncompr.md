---
title: "How to compress files so Windows users can uncompress them?"
date: 2011-05-17
forum: General Help
---

### Post by 1script on 2011-05-17
Hi everyone, another one of those Windows related inquiries :rolleyes:

I'm on an AMD64 Ubuntu 10.10 PC.

I'm distributing some of my [free vector and CNC designs here]("http://elabz.com/cnc-files/") and I've been naively ZIPing the files thinking it will make them more compatible for Windows users. However, after a second person reported that they cannot unzip my files, I decided to look into it on my wife's barebones (meaning no WinZIP or 7Zip or any other third-party file compression tools) Win XP Home and lo and behold - I cannot unzip my files there. It says "The Compressed (Zipped) folder is invalid or corrupted".

I've tried *zip*'s -*l* option (-l   convert LF to CR LF (-ll CR LF to LF)) but that didn't change much.

Does anyone have any advice to offer about the best way to compress files (text and Jpeg) on a Ubuntu computer so that they are guaranteed to uncompress on a Windows machine, preferably one without third party tools ('cause I can never be sure they are installed)?

Thanks a bunch!

---

### Post by doas777 on 2011-05-17
the Archive Manager (Apps -> Accessories) shoudl be able to create zips that any client can decompress. have you tried it?

---

### Post by dino99 on 2011-05-17
search for "zip" or "tar" or "7zip" into synaptic

---

### Post by doas777 on 2011-05-17
7zip is prolly a good bet.

---

### Post by noah++ on 2011-05-17
Huh. I have been *zip*ping my programming projects from the command line in Ubuntu 11.04. My instructor grades them in Windows 7, and he hasn't had a problem opening my files. Perhaps the problem is specific to 10.10 or XP or both together.

Archive Manager sounds like it's worth a try.

---

### Post by 1script on 2011-05-17
> **doas777 said:**
> the Archive Manager (Apps -> Accessories) shoudl be able to create zips that any client can decompress. have you tried it?

Honestly, I've just been using Nautilus's right-click menu (select your files, right-click, selct "Zip", Done!) at first. Then I've tried the same zip utility but from command line (to be able to add the "-l" option) - still no luck. 

Archive Manager (*File Roller 2.32.0*), although does not have a menu item under Apps-> Accessories on my machine, is installed and is **UN**-compressing those files just fine. I never tried to use it for compressing though. I'll go try to see if it makes difference.

Thanks!

---

### Post by -=hazard=- on 2011-05-17
> **1script said:**
> Honestly, I've just been using Nautilus's right-click menu (select your files, right-click, selct "Zip", Done!) at first. Then I've tried the same zip utility but from command line (to be able to add the "-l" option) - still no luck. 

Archive Manager (*File Roller 2.32.0*), although does not have a menu item under Apps-> Accessories on my machine, is installed and is **UN**-compressing those files just fine. I never tried to use it for compressing though. I'll go try to see if it makes difference.

Thanks!

In your case whats important is the file format, so others can use it in winzoz.

The simpliest way from terminal is zip, example:

You want to compress the folder named music, then do:
```
$ zip -r music.zip music
```
where music.zip is the output compressed file that you can name like you want, and music is the folder that you want to compress.

See $ zip -h for other options.

---

### Post by 1script on 2011-05-17
> **doas777 said:**
> 7zip is prolly a good bet.

Well, here the problem is: if you force ***7z*** to create a zip archive, it pretty much creates the exact same file as ***zip*** does (which also does not work in Win): 
```
7z a file.zip ./*
``` creates file.zip

If you let 7z create its own 7z format files, a barebones Windows with no 7Zip installed does not know what to do with a .7z file:
```
7z a file ./*
``` creates file.7z which Win does not recognize


Still soliciting suggestions.

Surely, I'm not the only one posting ZIP files on the Web and hoping everyone would be able to read them. How do they do it?!

---

### Post by 1script on 2011-05-17
> **-=hazard=- said:**
> In your case whats important is the file format, so others can use it in winzoz.
Thanks for your suggestion, -=hazard=- , but I've already tried all that. Using terminal to launch ***zip*** makes no difference from launching it via Nautilus menu as far as Windows compatibility is concerned. it still created the same .zip file.

---

### Post by -=hazard=- on 2011-05-17
> **1script said:**
> Thanks for your suggestion, -=hazard=- , but I've already tried all that. Using terminal to launch ***zip*** makes no difference from launching it via Nautilus menu as far as Windows compatibility is concerned. it still created the same .zip file.

Doesnt winrar open zip files?
I'm positive that it can extract .7z files too.

---

### Post by 1script on 2011-05-17
> **-=hazard=- said:**
> Doesnt winrar open zip files?
I'm positive that it can extract .7z files too.

I understand as much.

However, I cannot rely on whether or not WinRAR is installed on the the user's PC. Chances are it is (or WinZIP or 7Zip) but I would rather create a zip file that's un-zippable using Windows' own compression utility so no extra software is required.

---

### Post by 1script on 2011-05-17
In an interesting turn of events I'm finding out now that if I use Firefox on the same Windows PC to download the files created on my Ubuntu box, I can unzip them! If I download them with Internet Explorer, the error persists.

Wow, I guess it pretty much invalidates my question: it appears that there is no issue with compressing it, the issue is with IE downloading it from this particular site.

Still, I have no solution at this point: unfortunately, most of Windows users use IE and so won't be able to unzip the file that appears to become corrupted when IE downloads it. Has anyone ever seen something like that? Any ideas/tips/comments? Thanks!

---

### Post by AlphaLexman on 2011-05-17
```
apropos zip
```
```
which zip
```
```
man zip
```

---

