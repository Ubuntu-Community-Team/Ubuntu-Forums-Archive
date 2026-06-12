---
title: "downloading with unbutu"
date: 2012-05-04
forum: General Help
---

### Post by tijak on 2012-05-04
I find it very difdficult to download using unbutu.
I tried to download adobe flashplayer and ubuntu will tell me:
 
1) to open the files with "archives manager" : didn't work
 
2) with "other applications" and after searching would say that there was no applications available to open the file (computer or internet).
 
What is the solution?

---

### Post by Revolutionary101 on 2012-05-04
All you have to do is open Ubuntu Software Center and search for "Ubuntu restricted extras" (no quotes) and install the package that appears. That package includes flash player so after the install, you should be good to go. If you have any other questions just ask!

P.S. I would suggest download Google Chrome because Adobe has dropped Flash support on Linux but Google has promised to update future Chrome version with a Flash replacement. However Firefox will be unable to play Flash whatsoever once web developers start using newer versions of Flash. Just a heads up.

---

### Post by lisati on 2012-05-04
Are you given an option to save to disk?

---

### Post by tijak on 2012-05-04
Thanks a lot Revolutionary 101. It worked :) Still the question remains : what to do when  your download is not in one of the restricted extras.

---

### Post by Revolutionary101 on 2012-05-04
Well I am glad it worked! If you are looking for a different program just search for something else in the Ubuntu Software Center. That is the primary place to download all of your programs.

The Ubuntu repositories (fancy word for central database that all programs for a Linux distribution are stored) have several thousand programs in them so I believe you should be able to find whatever you need (or something close to it) just by searching the Ubuntu Software Center.

---

### Post by grahammechanical on 2012-05-04
What format was this download of Adobe Flash? Was it .deb?

Packages come as compressed files. Ubuntu uses the format of Debian (deb).

For example, I have a compressed package for a little utility that plays internet radio. The file is radiotray_0.6.3_all.deb

When I right click on the file I get the option to Open With Ubuntu Software Centre.

If I select that option then the Software Centre will install the program for me.

It is best to get programs through the Software Centre. If you did not get the option to Open With the Ubuntu Software Centre it could be because the file was not in the deb format but in some other compressed file format that requires a different method of unpacking and installing.

Regards.

---

