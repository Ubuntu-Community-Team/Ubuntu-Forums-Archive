---
title: "how to use a CD as respository?"
date: 2006-05-07
forum: General Help
---

### Post by medya on 2006-05-07
hey guys  I am reinstalling my ubuntu, I have installed many packages,
I want to back up all I have downloaded by S. Package Manager .

I have copied all of the Deb files that were in /var/apt/ ...

now I want to copy it to a CD , I want to know, when I install my new ubuntu, how should I "force" S.Package mangare to install the packages from my CD, and "not" download them from internet ? 
(my internet speed is very slow )

should I just simply copy the Deb files into the root of a CD and thats all ?



[COLOR="Gray"]+ I am reinstalling ubuntu because I am replacing ubuntu with Windows .
my ubuntu is on an old small hard disk , and windows is on the big hard disk.
I am killing windows and giving the good hard disk to ubuntu.:p 
[/COLOR]

---

### Post by pyromidget on 2006-05-07
This should be what you're looking for...

[http://ccrma.stanford.edu/planetccrma/man/man8/apt-cdrom.8.html](http://ccrma.stanford.edu/planetccrma/man/man8/apt-cdrom.8.html)

Hope it helps! :)

---

### Post by medya on 2006-05-07
would that show programs in my CD in S. Package manager?

---

### Post by medya on 2006-05-07
when in S.pakage manager menu I click on **add a cd-rom** (in edit menu)
it gives me this error 
E: Unable to locate any package files, perhaps this is not a Debian Disc



while my CD is full Deb files... should they be in a certain way?

---

### Post by pyromidget on 2006-05-07
Sorry man - this bit's outta my league - i just did a quick google for the earlier post!

Hope someone can help you!

---

### Post by StefanoCole on 2006-05-08
Hello medya, try the following link: [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")

and read the chapter: 2.4 Adding a CD-ROM to the sources.list file

Stefano

---

### Post by az on 2006-05-08
[QUOTE=medya]when in S.pakage manager menu I click on **add a cd-rom** (in edit menu)
it gives me this error 
E: Unable to locate any package files, perhaps this is not a Debian Disc



while my CD is full Deb files... should they be in a certain way?[/QUOTE]


You need a pacages index file.  See wiki.ubuntu.com/AptMoveHowto/simple

or just go to the directory on the cd and run

sudo dpkg -i *.deb

That will jst install all the deb in the directory, without using apt.  You mayt have to run

sudo apt-get -f install

a few times, since the packages have not installation order and dpkg may complain about dependancies that are there, but not done yet.

---

