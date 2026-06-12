---
title: "Perl Tkx causing segmentation fault"
date: 2010-12-29
forum: General Help
---

### Post by oldtop on 2010-12-29
Running a clean install of Ubuntu 10.10 under VMWare Player on a Thinkpad with Win7. Have previously used Perl/TK for GUI apps to run under both Windows & Linux. Latest Activestate Perl (Windows) does not support Perl/Tk, recommends Tkx, so I wanted to see if Tkx would work under Ubuntu. Tried to install Tkx using cpan, got obscure failure indicating dependency problem. Found a recommendation to apt-get install tcl8.5-dev, and then cpan installed Tkx.
 
Note, perl 5.10.1 is installed in Maverick by default. apt-get upgrade says I have the latest perl, Tcl and TK. I installed Tkx version 1.09 (using cpan). Couldn't find any info on what perl / Tkx versions are compatible.
 
Now Tkx is installed, but any attempt to run a script that uses Tkx causes a segmentation fault. apt-get installed pmtools to investigate. Even examining Tkx with pmtools can cause a seg fault, for example:
 
[FONT=Courier New]$[/FONT][FONT=Courier New] pmvers Tkx[/FONT]
[FONT=Courier New]Segmentation fault[/FONT]
 
Is Tkx known to work (or not work) under Ubuntu, version 10.10 or other versions? Any suggestions about what to try next?
 
It's hard to find info about Perl Tkx because so many people put "Can u help, tkx in advance" or similar in postings about anything under the sun. I've read a lot of them.

---

### Post by briml3y on 2011-01-07
I am having trouble getting Tkx to work in Ubuntu 10.10 aswell, If anyone has any suggestions

---

