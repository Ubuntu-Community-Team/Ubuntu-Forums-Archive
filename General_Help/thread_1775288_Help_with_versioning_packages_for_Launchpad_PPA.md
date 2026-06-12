---
title: "Help with versioning packages for Launchpad PPA"
date: 2011-06-04
forum: General Help
---

### Post by inameiname on 2011-06-04
I finally figured out how to upload onto Launchpad into a PPA, but unfortunately, I cannot seem to get the version numbers worked out.

For instance, here is the original version of bleachbit-bonus:

bleachbit-bonus_0.8.2-1_all.deb

...and I can successfully break it down into the correct source binaries for Launchpad, but when I try a folder name such as this:

bleachbit-bonus-0.8.2-1~ppa1

...it uploads to the PPA just fine, but the versioning is bad. For some reason it breaks it down like this:

package name: bleachbit-bonus-0.8.2
version: 1~ppa1

I know its some stupid little thing I am missing, but any help would be welcomed. Also, I really don't care what the version name is, I just want it working so I can mimic for several packages.

---

### Post by inameiname on 2011-06-04
Would this be fixed by simply altering the package name in the /debian/control and /debian/changelog files? I noticed they are off as well, so I will try it again changing those first.

Such as changing:

Source: bleachbit-bonus-0.8.2 
          to            
Source: bleachbit-bonus          
in         /debian/control

...and...

bleachbit-bonus-0.8.2 (-1~ppa1) natty; urgency=low 
to          
bleachbit-bonus (0.8.2-1~ppa1) natty; urgency=low 
     in        /debian/changelog



UPDATE:

This method seemed to have solved things. I'll test it out when its finished building before marking this as solved. I still don't like how I will have to manually change these things for every single package I want to upload to my PPA.


UPDATE2:

There's still something funky and I don't know how to resolve it. It just isn't doing it correctly. Nor is the size of the finished deb inside the PPA even remotely correct. Of course, that's probably another issue altogether.

---

### Post by inameiname on 2011-06-05
Bump...

---

### Post by inameiname on 2011-06-08
Bump... I thought this would be an easy one for those who use Launchpad...

---

### Post by inameiname on 2011-06-18
I just decided to do a versioning, and so far it seems to be alright. As such, I chose this format:

For foo-0.1, my versioning is this: foo-0.1-1ppa1~inameiname1.
And for foo svn20111806, my versioning is this: foo-0.1+svn20111806~inameiname1. 

Good enough. I'll just mark this as solved.

---

