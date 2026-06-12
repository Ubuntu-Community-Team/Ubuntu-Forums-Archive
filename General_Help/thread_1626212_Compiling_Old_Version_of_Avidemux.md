---
title: "Compiling Old Version of Avidemux"
date: 2010-11-20
forum: General Help
---

### Post by William-Ubu on 2010-11-20
Hello All! 

I'll try to make this short, esp because I don't know if this is the right place to discuss a 3rd party program like "Avidemux"  

I'm running the latest version "2.5.4" or so. It started giving me this problem where no matter what settings I give it, the resulting files are so small it results in an error after almost a day of encoding.  ( "XYZ" was NOT saved correctly , for example.)  One day I noticed the quantisizer was at max, peaking at 48-50...which made the files tiny. So, I can avoid this sort of, by limiting the maximum and minimum quantisizer in the configurations. Problem is, I have no control over target size or bitrate this way..and sometimes the results are still unplayable. 

Naturally I've uninstalled and re-installed  several times, and recompiled the x264 codecs using this guide: [http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331)

So, I downloaded the Tar.gz of the previous version i was using (Avidemux 2.5.3), the last known thing I know that worked for me...but I have no idea how to install it. I've tried running "Make" / "Cmake" In which I was told that an "in-tree-build" was detected. And trying to run the included "bootStrap.sh" results in : "Permission denied" or file/command not found. I don't think their old releases come in the default Ubuntu/Unix package "deb" right?

All these could be small errors on my end, but It urks me. In between reading up, and everything else that needs to be done in a day, I could have been done by now... Does anyone know where i could be going wrong?

---

### Post by mc4man on 2010-11-20
It's likely your bootStrap.sh file needs to be made executable - from source dir prompt
chmod +x bootStrap.sh
Then run ./bootStrap.sh
If you want to manually compile then I'd suggest looking here - scroll down to bottom for an example ubuntu build, you'll get the idea
[http://www.avidemux.org/admWiki/doku.php?id=build:install_2.5](http://www.avidemux.org/admWiki/doku.php?id=build:install_2.5)

You may get some help with 2.5.4+ here
[http://www.avidemux.org/admForum/](http://www.avidemux.org/admForum/)

---

### Post by William-Ubu on 2010-11-20
Thanks a million, that did it! Still learning the in's and out's

The "In-tree-build" part was solved with this: [http://www.linuxquestions.org/questions/linux-software-2/out-of-tree-737875/](http://www.linuxquestions.org/questions/linux-software-2/out-of-tree-737875/)

All the failures in that directory was cached and making a new, clean build folder solved that. Now I'll have to seek help for the thousands of errors while compiling. I wish there was a way to seek old versions out of the repositories. Thanks again

---

### Post by mc4man on 2010-11-20
> seek old versions
What version of ubuntu are you using?

> thousands of errors while compiling
errors or warnings, warnings are to be expected

---

### Post by William-Ubu on 2010-11-20
I'm on Ubuntu 10.10 (Maverick Meerkat?). 

I got Avidemux 2.4.3 up, in what looks like the QT version, just couldn't test it yet because it looks like mpeg 4 AVC or x264 wasn't included.

---

### Post by mc4man on 2010-11-20
Just curious - 10.10 has 2.5.3 in it's repo's, is there something wrong or not enabled in it?

---

### Post by William-Ubu on 2010-11-21
Is it? I'm just not sure how to show old packges in the manager

Just found out how to use "Packages -> Force version"

Thanks, you've been a major help, Mc. I'll mark this one off too.

---

