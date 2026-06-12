---
title: "Newsreader w/ NZB support for Ubuntu?"
date: 2005-01-21
forum: General Help
---

### Post by ubuntu-nerd on 2005-01-21
I am sorry if this is the wrong place to put this post.  Do any of you guys know of a newsreader with NZB support that I can use wtih Ubuntu?

Thanks in advance.

---

### Post by J. S. Jackson on 2005-01-21
Looking for the same thing.  Also looking for an equivalent of these:

**QuickPar** - For handling .par and .par2
**Mastersplitter/JAS/HJSplit** - joining .000 .001 .002 etc.
**WinRar** - rar archives

I'd like to get my USENET downloading frenzy set up on Linux.  Really it's the only thing I still lack on linux.

---

### Post by hardcandy on 2005-01-21
Binary News Reader- no debian package but does have an installler for linux. . 
[http://www.bnr2.org/](http://www.bnr2.org/)
parchive- handles par2 files. [http://unix.freshmeat.net/projects/parchive/?branch_id=45316](http://unix.freshmeat.net/projects/parchive/?branch_id=45316) not sure if it is in the repository, I just installed the debian package. 
rar and unrar are packages avaialble from universal (I believe)

---

### Post by Rule on 2005-01-21
oh no all this time i've been uing BNR and I never knew about bn2 thanks HC :D

---

### Post by ubuntu-nerd on 2005-01-22
[QUOTE=J. S. Jackson]Looking for the same thing.  Also looking for an equivalent of these:

**QuickPar** - For handling .par and .par2
**Mastersplitter/JAS/HJSplit** - joining .000 .001 .002 etc.
**WinRar** - rar archives

I'd like to get my USENET downloading frenzy set up on Linux.  Really it's the only thing I still lack on linux.[/QUOTE]
 I am not sure if this is an option for you, but I use Winrar and Quickpar through Crossover Office.  Both work very well.

I'd usually use NZBget since that was my favorite newsreader (command line only, flawless) but when I install it tells me I need some other dependencies that are already install.  I will copy and paste the message here to see if I can get some help.

---

### Post by ubuntu-nerd on 2005-01-22
Here is the code:


```
checking for strerror... yes
checking for strsignal... yes
checking for getopt_long... yes
checking /usr/include/g++/vector usability... no
checking /usr/include/g++/vector presence... no
checking for /usr/include/g++/vector... no
configure: WARNING: "STL header file was not found in /usr/include/g++."
checking /usr/include/libxml2/libxml/tree.h usability... no
checking /usr/include/libxml2/libxml/tree.h presence... no
checking for /usr/include/libxml2/libxml/tree.h... no
configure: error: "libxml2 header files were not found in /usr/include/libxml2."root@ubuntu:/home/mike/nzbget-0.1.2 #
```

I forgot to mention that HJsplit works under Crossover Office too.  They also have a linux build for HJsplit as well.

Hope this helps, and hope I can get an answer.

---

### Post by eNiNjA on 2005-01-22
> 
  **WinRar** - rar archives
  
 
 Why not d/l the linux command line version from their site, make a couple symbolic links to /usr/bin , for both rar and unrar.
 
 Kinda like this:
 [http://eclecticmonkey.com/index.php?p=15](http://eclecticmonkey.com/index.php?p=15)
 
 Doesnt Ubuntu have it via apt?

---

### Post by J. S. Jackson on 2005-01-22
I had heard of BNR2, but didn't look into it yet.  I wanted to get a feel for what everyone else is using.

Thanks for the tips from everyone.  I'm gonna play around a bit with some of these and see what happens.

Nerd - sorry I cannot help with your problem, I'm still pretty n00b to Linux.  I hadn't heard of Crossover Office.  I'll have to look into that.

---

### Post by martijntje on 2005-01-24
Here's what i use:
 
 - nzbget, for download files from usenet through the use of nzb files
 - par2, command line utility for checking, repairing files (available in
 - unrar, command line utility to unrar files.
 
 100% winbloze free!

---

### Post by ellingtn on 2005-01-25
For me, 

File Roller unrars with no problem. I also have the command line utility installed. 
For PAR2 files, I'm using the command line utility 'par2cmdline' version 0.4. Haven't had a need for PAR file utility yet.
For a news robot, I'm using NewsbinPro via wine. I had it registered some time ago, a few years and it works rather well. Plus, I didn't like the user interface of BNR2.
For 001, 002, files I'm using the java version of HJ Split.

---

### Post by Snarfy on 2005-02-01
[QUOTE=ubuntu-nerd]Here is the code:


```
checking for strerror... yes
checking for strsignal... yes
checking for getopt_long... yes
checking /usr/include/g++/vector usability... no
checking /usr/include/g++/vector presence... no
checking for /usr/include/g++/vector... no
configure: WARNING: "STL header file was not found in /usr/include/g++."
checking /usr/include/libxml2/libxml/tree.h usability... no
checking /usr/include/libxml2/libxml/tree.h presence... no
checking for /usr/include/libxml2/libxml/tree.h... no
configure: error: "libxml2 header files were not found in /usr/include/libxml2."root@ubuntu:/home/mike/nzbget-0.1.2 #
```

[/QUOTE]
 You need to install the development package of libxml2

-- Hope this helps --

---

### Post by vassie on 2005-06-14
[nzbperl](http://noisybox.net/computers/nzbperl/) is great, and very easy to use

Ben

---

### Post by sizzam on 2005-10-22
I like klibido for downloading NZB's.  It is a KDE app, but installing it via apt on Breezy will automatically get all the KDE libraries it needs

```
sudo apt-get install klibido
```

---

### Post by poptones on 2005-10-22
I have been a regular usenetter since about '94 and I have no idea what nzb is...

Par and rar are easily handled on the command line, and installing hjsplit is kinda like putting a volkswagen hood ornament on your Benz:

cat somefile.avi.??? >> somefile.avi

Split and cat are built in, man... those windowsplitter tools were invented to make up for Microsoft's weak command line.

---

### Post by eldergod on 2008-05-04
> **ellingtn said:**
> For me, 

File Roller unrars with no problem. I also have the command line utility installed. 
For PAR2 files, I'm using the command line utility 'par2cmdline' version 0.4. Haven't had a need for PAR file utility yet.
For a news robot, I'm using NewsbinPro via wine. I had it registered some time ago, a few years and it works rather well. Plus, I didn't like the user interface of BNR2.
For 001, 002, files I'm using the java version of HJ Split.

You can use cat to join files:
replace the .001, .002 with *

cat filename.avi.* > filename.avi

---

