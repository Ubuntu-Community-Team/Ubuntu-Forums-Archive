---
title: "Help with data from RS-232 device"
date: 2011-07-27
forum: General Help
---

### Post by kgriff on 2011-07-27
Hi all.  And thanks in advance for any help.
I have several devices that send data using RS-232.  In Windows i use a program called WedgeLink to capture, parse, and pass the data on to my application of choice.  (OpenOffice Spreadsheet, in one particular case)
Does anyone know of a program for Linux that will perform this function?
For example, my data string may be something like
12-Jul-2011,5.025657,Rd 1 {CR}{LF}

With WedgeLink, I can capture the entire data string, terminated by {CR}{LF}.  Using the parsing function I can extract the portion of the string that I want to use, 5.025657, and pass it to OpenOffice.  At this point in time, this is the only thing tying me to Windows and I'd dearly like to replace it.

---

### Post by HermanAB on 2011-07-27
On Linux, the popular serial port programs are minicom, cutecom and ckermit.

What you want to do, can probably be done simply by piping the device to a file:
# cat /dev/ttyS0 > filename

(after setting the port up with minicom or cutecom).

If you want to script things, then use ckermit.

---

