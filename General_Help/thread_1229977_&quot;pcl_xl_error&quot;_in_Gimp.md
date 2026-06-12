---
title: "&quot;pcl xl error&quot; in Gimp"
date: 2009-08-02
forum: General Help
---

### Post by klausner on 2009-08-02
Suddenly, when I try to print a postscript file to my Brother HL-2170W in Gimp 2.6.3, instead of the image I get a message:
> pcl xl error
          Subsystem:    KERNEL
          Error:        MissingData
          Operator:     ReadImage
          Position:     15


Only postscript seems to do this. No problems with jpegs.

The only system change since the last time I successfully printed was the recent set of patches which included the change to kernel 2.6.27-14. I'm still using Intrepid, 8.10.

I tried reloading the PPD file in system-config-printer, but that didn't help.

The only bug I can find in a web search seems to generate gimp errors with anything *_but_* postscript images.

---

### Post by vkkim on 2009-11-17
I have the exact same problem as [http://ubuntuforums.org/showthread.php?t=1294854](http://ubuntuforums.org/showthread.php?t=1294854)

[QUOTE=ions]I can no longer print large PDFs on my networked Brother Laser 4040CN since I upgraded to 9.10. I installed the printer by autofinding it, by CUPS and by including the PPD file from linuxprinting.org.

```
PCL XL error

Subsystem: KERNEL
Error: MissingData
Operator: ReadImage
Position: 15

```

Before anybody blames my printer and says it doesn't have enough memory let me point out that the same document prints just fine when sent to the printer from my 9.04 machine.[/QUOTE]

Mine also does not work with 9.10 but works fine with 9.04; I am printing on a networked Brother HL-2170.

---

### Post by Ryuhayabusa on 2009-11-21
I am having the same problem with my HL-2170w and 9.10.

It seems to happen sporadically for me.

---

### Post by afrodocter on 2009-12-03
i also have the same problem, but occurs when i print a certain pdf, only on one page, which contains pictures.

i found a fix, although its not perfect. changing the driver  to 
Brother HL-2140 Foomatic/hpijs-pcl5e

solves this problem, and prints about 20x faster (the original driver 2170w, was extremely slow even on USB)
but the ink looks kind of blotty.

---

### Post by Brejcha on 2010-01-10
I too have been having this problem when trying to print certain .pdf files. It is kind of a pain in the ***, and I hope there is a fix soon. I will try the fix by changing the drivers. Hopefully that will work :-)

---

### Post by klausner on 2010-02-17
Bump. Six months later, still no answer??

---

### Post by Bertik on 2010-02-19
another bump from me...

Network printer HP LaserJet M1522n
Karmic 64 bit

---

### Post by karabas1543 on 2010-02-22
Hey that trick with changing the driver to 2140 worked! Had the same problem with my 2170w and it printed just fine with the 2140 drivers! I guess that's the solution for the time being. Not sure what it is for other printers though.

---

### Post by Bunyak on 2010-06-29
OK, how do you get the 2140 drivers?  BTW, mine prints everything very nicely from the administrator's account, but not from my wife's profile.  What's up with that?

Please consider this a "bump." :-D

---

### Post by RJARRRPCGP on 2010-06-29
Looks like a permissions problem. Sorry. :(

---

