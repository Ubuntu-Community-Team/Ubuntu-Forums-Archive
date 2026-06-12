---
title: "Tripple A bord game clone"
date: 2011-12-19
forum: General Help
---

### Post by sinbowden on 2011-12-19
I am having trouble installing Triple A on Kubuntu. I found a thread but the link was disabled. any help would appreciated.

---

### Post by jake.anq on 2011-12-19
Hi

What do you mean by 'trouble'?  Some error messages/problem details would be helpful if available.

---

### Post by sinbowden on 2011-12-19
I am trying to use wine but get this: The file  '/tmp/kde-mark/arkqzsns8//Setup_e.exe' is not marked as executable.  If  this was downloaded or copied from an untrusted source, it may be  dangerous to run.  For more details, read about the executable bit. I  marked the file as exe but still no luck? any idieas? 
I have no clue where to begin with Triple A. I found this thread: [http://ubuntuforums.org/showthread.php?t=734081](http://ubuntuforums.org/showthread.php?t=734081) which gave me this link: [http://gwos.org/doku.php/guides:64bit:triplea](http://gwos.org/doku.php/guides:64bit:triplea), and that link is disabled. A walk through woul be cool. it doesnt have to be supper detailed. I read where I don't understand. I might asked if I'm just totally lost.

---

### Post by sinbowden on 2011-12-19
made new, proper post.

---

### Post by jake.anq on 2011-12-19
Hi

It seems to me that you do not need to use wine to install TripleA.
This is the instructions from here: [http://triplea.sourceforge.net/mywiki/Installing](http://triplea.sourceforge.net/mywiki/Installing).

To install the program, first check your version of java:
```
$java -version
```  It should be 1.6 or higher.  If it is not, try running the upgrade tool or install from java's website.

Then download the file from [http://sourceforge.net/projects/triplea/files/TripleA/1_3_2_2/ ]("http://sourceforge.net/projects/triplea/files/TripleA/1_3_2_2/")called triplea_1_3_2_2_all_platforms.zip.
Lastly, unzip the file to a directory of your choosing and run triplea_unix.sh by double clicking on it (you may need to set this as an executable first).

---

