---
title: "apt-get problems"
date: 2006-05-08
forum: General Help
---

### Post by theaffman on 2006-05-08
hi thank you all for your kind help.

When i try to use synaptic or apt-get i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I run that command, and it hangs on the following:

bryan@ubuntu:~$ sudo dpkg --configure -a
Password:
dpkg: dependency problems prevent configuration of python-kde3:
python-kde3 depends on python2.4-kde3; however:
Package python2.4-kde3 is not installed.
dpkg: error processing python-kde3 (--configure):
dependency problems - leaving unconfigured
Setting up debtags (1.4+svn20050912-0ubuntu1) ...
Get:1 [http://people.debian.org/~enrico/tags/tags-current.gz](http://people.debian.org/~enrico/tags/tags-current.gz) [215kB]
Get:2 [http://people.debian.org/~enrico/tags/vocabulary.gz](http://people.debian.org/~enrico/tags/vocabulary.gz) [14.5kB]
Fetched 230kB in 8s (26.3kB/s)
Reading tag data and vocabulary for [http://people.debian.org/~enrico/tags/](http://people.debian.org/~enrico/tags/)...
Writing system vocabulary...
Writing merged tag database...


after trying this a few times, i can't update or install anything.

---

### Post by Sef on 2006-05-08
Please don't double post.  We are all volunteers here, and sometimes it does take some time to get an answer.

Original post:

[http://ubuntuforums.org/showthread.php?t=172192]("http://ubuntuforums.org/showthread.php?t=172192")

---

### Post by theaffman on 2006-05-08
sorry i didn't mean to offend, i think that all the volunteers that contribute to the open source community are very kind.

 i just thought that see as it was a problem i developed while trying to install kubuntu i should post it over here as well. my fault.:confused:

---

### Post by ajgreeny on 2006-05-08
It looks as thoughh you need to install python2.4-kde3 from the main repositories.  You should be able to do this normally through synaptic but as you are having problems with that I'm a bit stuck as to how you can get the package.  Worth just trying to do it that way first, however.

---

### Post by cyracks on 2006-05-08
try to enter

sudo apt-get install python2.4-kde3

and check the error why exactly python2.4-kde3 can't be installed

---

### Post by carlos1 on 2006-05-08
My recommendation would be to try and install the missing package directly. 
Go to this page: 
[http://packages.debian.org/unstable/python/python2.4-kde3](http://packages.debian.org/unstable/python/python2.4-kde3)
and toward the bottom you will find download links for that package. 
I would try downloading the right one for your architecture (I don't know exactly what you're running, probably 1386?) and then try install that directly with:

sudo dpkg -i python2.4-kde3_3.11.3+20051013-1+b1_i386.deb

I hope that helps.

---

