---
title: "Problem installing matlab 2008b from dvd"
date: 2011-06-24
forum: General Help
---

### Post by ikirby77 on 2011-06-24
Hi Guys,
 
I been having a bit of a problem installing matlabR2008b on ubuntu. I have followed step by step what little installation information is provided with the dvd, however for some reason when i type the command:
 
sudo sh /media/MATHSWORKS_R2008B/unix/install 
 
I am presented with:
 
sh: can't open /media/MATHSWORKS_R2008B/unix/install 
 
:( :(
 
Any help or advice regarding this problem would be very much appreciated.
 
Thanks
 
Ian

---

### Post by Topsiho on 2011-06-24
First: what is in /media/MATHSWORKS_R2008B/unix/ ?
If it is empty or doesn't exist, or if it doesn't contain an executable file with the name "install" then nothing happens.

Second: in the repositories you'll find a perfect clone of Matlab, it is called Octave, is open source, and you may use it without any license problems which are connected to closed source software, AND it's somewhat cheaper. Octave comes with a comprehensive documentation too.


Topsiho

---

