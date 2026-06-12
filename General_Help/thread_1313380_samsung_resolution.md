---
title: "samsung resolution"
date: 2009-11-03
forum: General Help
---

### Post by s.dalas on 2009-11-03
Hi people,
i bought a samsung lcd TV lw26a33w.
My problem is this. In my manual it says:
> VESA 640 x 480  37.861 72.809 31.500 -/-
     640 x 480  37.500 75.000 31.500 -/-
     800 x 600  37.879 60.317 40.000 + /+
     800 x 600  48.077 72.188 50.000 + /+
     800 x 600  46.875 75.000 49.500 + /+
     1024 x 768 48.364 60.000 65.000 -/-
     1024 x 768 56.476 70.069 75.000 -/-
     1024 x 768 60.023 75.029 78.750 + /+
 GTF 1280 x 768 47.700 60.000 80.136 -/+

What i want to know is this. with vesa i get 1024*768 something that i can see without doing anything in xorg. ubuntu found it self.

Is there a way to get the 1280*768 resolution which is GTF??

Thanks in advance, 
Stelios

---

### Post by s.dalas on 2009-11-04
i spend some hours to find out the solution. I was experiment with the Xorg with a modeline i generate from here [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl"), but this was for vesa and not for GTF. 
The solution came when i found that the modeline generator for GTF driver was already install in ubuntu! Just type gtf in terminal and the generator is there.;)

---

