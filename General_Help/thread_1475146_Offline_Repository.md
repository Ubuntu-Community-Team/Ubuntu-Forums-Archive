---
title: "Offline Repository"
date: 2010-05-06
forum: General Help
---

### Post by forensicneophyte on 2010-05-06
I am trying to make my own offline repository for my offline test lab. In the documentation, on the following webpage:

[https://help.ubuntu.com/community/AptGet/Offline/Repository?action=show&redirect=SuiteCodename](https://help.ubuntu.com/community/AptGet/Offline/Repository?action=show&redirect=SuiteCodename)

it states: 

Go to this web address [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) and then to the [SuiteCodename]("https://help.ubuntu.com/community/SuiteCodename") of the Ubuntu installed in your hard disk (intrepid, jaunty, karmic, ...) and download the files : 

[LIST]
[*]Release
[*]Release.gpg
[*]And the  Contents files for your architecture (i.e Contents-i386.gz ,if you architecture is i386).
[/LIST]

When I click on the Release and the Release.gpg links, they give me a webpage with text. The text is basically a categorization of md5sums with bz2 files, and a GPG signature.

My question is as follows: Am I just supposed to copy and paste the text into a text file and save them as Release and Release.gpg respectively? And then save them in the files that described by that webpage as denoted in the following path?

/home/repository/dists/Lucid


If so, then please let me know. I also would like to know if this would be a good thing to add to the documentation. I am relatively new to ubuntu, although I have used it for about 2 years, but I find it hard to understand the documentation sometimes. Since I have the perspective of a new user, I hope I can help other new users by contributing to the documentation as I learn. I can help put in some of the missing link that lie between the beginner and the super geek.

Thanks
FN

---

### Post by forensicneophyte on 2010-05-06
I am saving Release in notepad on a windows xp computer. It will only save it as Release.txt  . Do I simply need to save that onto my ubuntu computer, and change the name from Release.txt to Release? Also, I want to know if the repository is the same for the server, and the desktop, because I am implementing an ubuntu server, and I will be accessing it from my ubuntu desktop through my home network, and I want to do updates and package installation from my home offline repository.


Thanks
FN

---

### Post by forensicneophyte on 2010-05-06
Apparently I am missunderstanding something. I downloaded all the files, and made the file tree as described on the foresaid webpage in my first post.

Go to this web address [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) and then to the [SuiteCodename]("https://help.ubuntu.com/community/SuiteCodename") of the Ubuntu installed in your hard disk (intrepid, jaunty, karmic, ...) and download the files : 

[LIST]
[*]Release 
[*]Release.gpg     
[*]And the  Contents files for your architecture (i.e Contents-i386.gz ,if you architecture is i386). 
[/LIST]
Later, go to the component (main, multiverse, restricted, universe) and architecture (i.e. binary-i386/ in /dists/karmic/main/) that you want in your local repository, and download the files: 

[LIST]
[*]Packages.bz2              
[*]Packages.gz               
[*]Release    
[/LIST]
Optionally, you can download the same files for the source directory (its packages are architecture independent). 
Now, you have to store the files in your local Ubuntu repository in the same order. For example:  

[LIST]
[*]In /home/repository/dists/karmic you would have the files: Contents-i386.gz , Release and Release.gpg     
[*]And in /home/repository/dists/karmic/main/binary-i386 the files: Packages.bz2  ,  Packages.gz  and Release
[/LIST]

I want to install apache mysql and php on my ubuntu server. The problem is that the total of all the files that I downloaded is 32.8 Megabites. I had the impression that I am downloading a "so to speak" mirror of the ubuntu repositories. The ubntu repositoriies cannot possibly be contained in 32.8 Megabites. What am I missunderstanding, and how can I get the files that I need to install packages and dependencies to put in my offline repository?

---

### Post by forensicneophyte on 2010-05-24
No need to reply to this thread. I found the answer on the following thread. It didn't come up in my original search, but later I found it.


[http://ubuntuforums.org/showthread.php?t=1487802](http://ubuntuforums.org/showthread.php?t=1487802)

---

