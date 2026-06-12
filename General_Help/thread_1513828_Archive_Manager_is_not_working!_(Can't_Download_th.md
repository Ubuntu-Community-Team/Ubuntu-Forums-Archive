---
title: "Archive Manager is not working! (Can't Download things)"
date: 2010-06-20
forum: General Help
---

### Post by geeee on 2010-06-20
Hello. I am quite new to Ubuntu. Just today, I have upgraded my Ubuntu to 10.04, in hopes that my problem would dissapear. Sadly, it hasn't. You see, my archive manager isn't cooperating with me and it's not letting me download anything. For example, I tried to download Sony Vegas and it gave me the following error. (Among other things, but this data seems more important.)[INDENT]
" End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive. "

[/INDENT]This occured when I tried to open the "SonyVegas 8.0 exe" . I have unzipped this file. I think "exe" has something to do with Windows, if so, is there a way I can convert this file so it can be adapted to my archive manager? Or is my archive manager not working, correctly? Does anyone else have these problems, also? Please, I want to be able to download things and my archive manager is the reason I can't. Leave me wisdom. Thank you &reply please. 

[Also, is this the right forum? I tried the Absolute beginners forum but it seemed no one was able to help me. :( ]

---

### Post by Pollox on 2010-06-20
Archive manager is just for unzipped compressed files (like .zip), and it doesn't have anything to do with downloading stuff.  You can not "open" exe files with it.  Files ending in .exe are executable Windows files (aka Windows programs).  Ubuntu seems to default to trying to open them with archive manager, but that's not helpful for you.  You may be able to run this particular program using Wine (I like PlayOnLinux as a nice frontend to this).  Read about Wine and try to get it working.  If you can't, come back and start a new topic about it.  I suggest a descriptive title like "help installing Sony Vegas using Wine".

Either this or Absolute Beginners seems to be fine for questions like this.  I think Absolute Beginners is fairly active response-wise, and good for any question by people new to Ubuntu.

---

### Post by cuberts on 2010-06-20
> **Pollox said:**
> Archive manager is just for unzipped compressed files (like .zip), and it doesn't have anything to do with downloading stuff.  You can not "open" exe files with it.  Files ending in .exe are executable Windows files (aka Windows programs).  Ubuntu seems to default to trying to open them with archive manager, but that's not helpful for you.  You may be able to run this particular program using Wine (I like PlayOnLinux as a nice frontend to this).  Read about Wine and try to get it working.  If you can't, come back and start a new topic about it.  I suggest a descriptive title like "help installing Sony Vegas using Wine".

Either this or Absolute Beginners seems to be fine for questions like this.  I think Absolute Beginners is fairly active response-wise, and good for any question by people new to Ubuntu.I have learned this in my own excperience that .exe files are not able to be "opened" in Linux because it is a Windows based file extension. as the person above said, the Archive Manager is only a useful program which will automatically extract the files for you. If you are having problems downloading stuff then it does not have anything to do with the Archive manager. 

This following command here will download the file from any URL you enter after "wget" This is the  quickest way that I found to download a file, especially when you are  already in the terminal.  
Type the following code into the terminal (applications>accesories>terminal)
```
wget http://linkofthefileyouwanttodownload.com/
```
This is directly downloading files from the CLI which is much powerful than the Graphical user interface. If this method does not work, then I will not know how to help you. I hope that this will help your problem.

---

### Post by geeee on 2010-06-20
Thank you very much.

---

### Post by sonkamble satish shripati on 2011-08-26
Hi friends, I am also getting similar problem while installing [B]archival manager.
[/B]I am getting following error Please, help me to solve this problem

sonkamble@sss:~$ sudo apt-get install tar
[sudo] password for sonkamble: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev libdata-page-perl graphicsmagick libclass-accessor-perl
  g++-4.3 swish++ libclass-accessor-chained-perl pstotext libsub-name-perl
  lesstif2 libimage-size-ruby1.8 liboil0.3 xpdf-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 340 not upgraded.
Need to get 0B/403kB of archives.
After this operation, 721kB of additional disk space will be used.
dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: 1 expected program(s) not found in PATH or not executable.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

