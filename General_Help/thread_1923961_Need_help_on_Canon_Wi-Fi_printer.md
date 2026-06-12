---
title: "Need help on Canon Wi-Fi printer"
date: 2012-02-11
forum: General Help
---

### Post by susja on 2012-02-11
Hello,
Maybe someone has experience with wireless Cannon printer and could help me?
I'm running Ubuntu 11.10.
Yesterday I've bought PIXMA MX410. I was able to  install drivers and it works for print, copy and fax. I use it over  Wi-Fi. I have 2 questions.
Question #1.
I connected regular phone to the machine and I'm using one line for fax  and phone calls.My phone does not have answering machine.  I use one line for phone and fax. My question:  is it possible to receive fax unattended? Currently I have to pick up  receiver when fax is coming  and then place it back and then fax got  received ... Could I disconnect phone from the machine or it's  mandatory? Will this feature work only in case connected phone has  answering machine?
Question #2.
As I mentioned I use the machine wirelessly but I failed to scan. I  successfully installed both printer and scanner drivers but it looks  that machine does not recognize my computer when in Scan mode. Is it  possible to setup machine to scan in Wi-Fi mode? If it's 'not' and only  in USB mode how could I switch from Wi-Fi to USB only for scanning?
Thanks in advance.
susja

---

### Post by susja on 2012-02-12
well ... Canon already answered my Question #1 but they don't support Linux and can't help me with Question #2 i.e. failure to scan.
Just FYI: I connected my printer to another laptop which run Rhat 6.2 and it got the same issue with scanning.
Does anyone has experience with this stuff?
Thanks.

---

### Post by grahammechanical on 2012-02-12
Have you seen this comment?

>  Please note that there is only support for scanning on Linux in version 2.80 or higher of the Linux drivers - there is a seperate Scangear download for this purpose. While Canon Inc has tested the drivers successfully on the listed Linux distributions, this is meant only for guidance;

On this web site:

[http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp]("http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp")

Have you tried using the Sane scanning utility to see if that will pick up this printer as a scanner?

I have also found this site, but it is old information.

[http://mp610.blogspot.com/]("http://mp610.blogspot.com/")

I do not have a working printer. so, I do not speak from experience but I may buy one of these all-in-one printers so I am interested in this subject.

And another link that might help:

[http://linuxtidbits.wordpress.com/2011/07/14/canon-pixma-mg5220-ubuntu-setup/]("http://linuxtidbits.wordpress.com/2011/07/14/canon-pixma-mg5220-ubuntu-setup/")

Regards.

---

### Post by susja on 2012-02-12
hello [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323"),
appreciate your speedy reply.
I believed that I used drivers from the site you pointed [http://software.canon-europe.com/products/0011010.asp](http://software.canon-europe.com/products/0011010.asp)
This site has 2 files: driver and source file. Both are 1.70. I used driver and successfully installed it ( as I mentioned before). Are you talking that only starting from 2.80 it'll do scanning? But I don't see sources for it .. or I"m missing something .... I'll continue to investigate.
Thanks again.

---

### Post by susja on 2012-02-12
well I stuck again.
1. I failed to find either scan driver or source code file for my MX410 hence I can't run ScanGear
2. I installed Sane and added repository but Sane failed to find drivers.

Very frustrated ...
susja

---

### Post by susja on 2012-02-13
Thanks to everyone who tried to help.
Eventually I was able to resolve the issue and now I could print and scan wirelessly.
Regards,
susja

---

