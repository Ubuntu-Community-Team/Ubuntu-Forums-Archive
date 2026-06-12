---
title: "processing and bash files"
date: 2010-11-11
forum: General Help
---

### Post by bitttttor on 2010-11-11
Hi,

I'm working in a processing script that needs to interact with other application that can be controlled with the shell. 
So I have my processing script and a bash script that I need to somehow joint. The conversation is only one way round, I mean, I need processing to make the .sh file run so I can read the output.

Is there any simple way to run a bash file from processing, or I'm looking it the wrong way and should I automate from above using a bash file for the whole thing?

Thanks !!

---

### Post by papibe on 2010-11-11
> **bitttttor said:**
> ... I'm looking it the wrong way and should I automate from above using a bash file for the whole thing?


Probably, What is the other script written on?  Give us more details so we can come up with better ideas.

Regards.

---

### Post by bitttttor on 2010-11-17
Thanks for answering,

I've just started currently working on the script, but in general terms I'm trying to connect [Processing ]("http://processing.org/")and [ESP-r.]("http://www.esru.strath.ac.uk/Programs/ESP-r.htm") Nothing too complex, after some operations in processing, I use it to print an HTML or a XML 2d matrix with geometric coordinates, then I need to read this info from a bash file to inform the geometry and run some simulations. Then rewrite the matrix and read it back in processing. 

The first thing is easy, I can get the html file. Also now I can start the bash from processing, and can run an ESPr simulation from a bash file using a 2d matrix. What I haven't done yet is connect them. The main problem is I'm quite new in Ubuntu so I don't know if a bash can parse and write html (maybe I should change to Perl?). 

Thanks,

---

### Post by papibe on 2010-11-17
If you just want to "catch" a few tags of html, you'll be fine using a combination of sed, awk, or grep inside a bash script.

However if you are going to do more serious parsing, it could get be very frustrating. In that case, you need a more powerful language.

My recommendation: python. Specially since there's a lot of libraries to parse html. I have used both python and a library called [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/") very successfully to parse html.

Good Luck!

---

### Post by bitttttor on 2010-11-18
Thanks a lot papibe !!!!!!

I'll check your recommendations to see what suits me,

---

### Post by bitttttor on 2010-11-18
> **papibe said:**
> My recommendation: python

Regarding python in ubuntu, do anyone know a good tutorial for absolute beginners?

I have done some simple stuff in python but don't know how to use it in the terminal, so started with Ruby but as there was also few info (and my skills are limited), after a quick research I've ended learning bash script.

---

### Post by asmoore82 on 2010-11-18
To quickly get going with python, try "quickly"

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

[http://www.youtube.com/watch?v=9EctXzH2dss](http://www.youtube.com/watch?v=9EctXzH2dss)

---

### Post by bitttttor on 2010-11-18
Thanks !!!!!!

---

