---
title: "Installing wyd0.2"
date: 2009-09-08
forum: General Help
---

### Post by bonicideur on 2009-09-08
Hello,
 
 I would like to install wyd0.2 on my ubuntu 9.04 jaunty. I've downloaded a tar file (wyd-0.2.tar.gz).
 Inside the tar file there is a folder called wyd-0.2 with inside three folder "docs", "testfiles", "wlgmod" and 5 files called "BUGS", "CHANGES", "README", "TODO", "wyd.pl".
 
 Of course there is any word about installation in the readme file...I seek the web and found nothing about installation of this software.
 
 I am not a complete noob, and I think that's a non-compiled program...but I have no idea on how to install it.
 

 Thank you for your help and your time.

PS: a link with explanation is more than enough.

---

### Post by kurtdriver on 2010-03-07
You don't really install perl programs, you run them:
[you@yourbox dict]$ chmod a+x wyd0.2
and then:
[you@yourbox dict]$./a+x wyd0.2
This assumes that perl is installed.
Perl is an interpreted language and the interpreter is called perl.
[you@yourbox dict]$man perl
for more details.

---

### Post by bonicideur on 2010-03-07
Thank you very much....haven'y found the solution for long time....It's working now :D...Have a nice week.

---

