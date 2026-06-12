---
title: "Lucid problems with latest versions of GZip?"
date: 2010-05-01
forum: General Help
---

### Post by cousinit2 on 2010-05-01
OK, so after waiting eagerly for the full release of 10.04, I grabbed the 64-bit version and did my usual backup with dpkg, wiped all partitions and started over with a fresh install of Lucid on my Dell Latitude D820. While the process took a night and a day, I now have a mostly-working setup of Lucid Lynx--except for this one thing. 

I went to reinstall some icon themes from gnome-look.org, conveniently downloaded as .tar.gz files, and the installer errors out saying "There was a problem while extracting the theme."

I re-download the files, plus some other themes as a check, and none of them work. I fire up Archive Manager (file roller) and try to open the files. I get this message:

```
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

```
I've now seen this elsewhere online, and tried a few things:

1. I have downloaded other .tar.gz files and had the same result.
2. I tried to re-install, and completely re-install:
```
sudo apt-get install xz-utils
```
This had no effect.
```
 sudo apt-get --purge gzip xz-utils
sudo apt-get install gzip xz-utils
```
This had no effect either. I eventually worked my way back up the dependency tree; I purged and removed 66 other packages to no avail.

However, when I downloaded the latest version of gzip as a .tar.gz, that file opens fine! Incidentally it is found [_[COLOR="DarkGreen"]here[/COLOR]_]("http://ftp.gnu.org/gnu/gzip/gzip-1.4.tar.gz"). After building from source the latest version I still have the same problems, though.

Which leads to my ultimate question: is something going on with gzip itself that's causing trouble with older file versions (which NEVER gave errors before), is there a problem between Lucid and GZip causing the trouble, or is it a combination of both/neither/my own insanity?

I've checked every other resource online that I can using every search engine I can think of. I have seen some other recent problems with gzip mentioned in the Ubuntu forums, but nothing like what I am having here.

---

### Post by dcstar on 2010-05-01
> **cousinit2 said:**
> OK, so after waiting eagerly for the full release of 10.04, I grabbed the 64-bit version and **did my usual backup with dpkg**, wiped all partitions and started over with a fresh install of Lucid on my Dell Latitude D820. While the process took a night and a day, 
..........

Did you install old packages or only new Lucid packages?

---

### Post by cousinit2 on 2010-05-03
First of all, THANK YOU!  I am very glad to get help on my issue in the Ubuntu forums! =D>

I used the following method to carry over installed packages:

```
sudo dpkg --get-selections > installed-software
```

I then wiped and installed Lucid using frest partitions. Then I re-installed packages using these commands:

```
sudo dpkg --set-selections < installed-software
dselect
```

I chose dselect option 3: "Install and upgrade wanted packages".

When I re-installed the 66 other packages in my attempt to completely remove and re-install GZip, I simply used this: ```
sudo apt-get install <package> <package> <package>...
```

I eventually downloaded GZip 1.4 and compiled & installed that using the Linux Three-Step:```
./configure
make
make install
```
That went off without a hitch, but it still didn't fix anything.
I suppose it's possible that someone botched the theme packs on gnome-look.org, but when I used Xarchiver, I was able to open & extract them. I re-made the packages using GZip on my computer and everything worked normally. Also, the source for GZip 1.4 came in a .tar.gz file, and that opened just fine using my previous GZip version.

This is very odd. I really would like to know what is happening here.

---

