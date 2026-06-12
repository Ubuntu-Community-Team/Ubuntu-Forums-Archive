---
title: "PRN to PDF -- a2ping?"
date: 2011-05-07
forum: General Help
---

### Post by wmeler on 2011-05-07
I have an old PRN file (created in Win98) by doing "Print to file."  I want to turn this into a PDF file.  According to "man a2ping" [direct quote]:

· If  you  have  a PS coming from Win32 (often with extension ".prn"), run it through a2ping. It will remove the resolution changes and the progress text printed to the terminal (which confuses gv(1) and makes some filters in the print queue emit incorrect output).

And yet, when I try to run a2ping myinput.prn myoutput.pdf, I get the following:
/usr/bin/a2ping: unknown input image format: myinput.prn


Thoughts?  I am not set on a2ping...just want to convert the file somehow.

---

### Post by wmeler on 2011-05-08
Not worrying about this.
I used PDF995 at [http://www.pdf995.com/download.html](http://www.pdf995.com/download.html)

More info here:
[http://www.linuxquestions.org/questions/linux-software-2/prn-to-pdf-a2ping-879409/](http://www.linuxquestions.org/questions/linux-software-2/prn-to-pdf-a2ping-879409/)

---

